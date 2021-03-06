---
title: Project Structure
order: 0
---

Make sure you saw this section's [introduction](/guide/meta) first!

### File Casing

Capitalized file names (aka first letter upper-cased).

**Justification**: Module names can only be capitalized. Newcomers often ask how a file maps to a module, and why `draw.re` maps to the module `Draw`, and sometimes try to refer to a module through uncapitalized identifiers. Using `Draw.re` makes this mapping more straightforward. It also helps certain file names that'd be awkward in uncapitalized form: `uRI.re`.

### Folders

Try not to have too many nested hierarchies. Keep things flat, and have fewer files (reminder: you can use nested modules).

**Justification**: Directory organization is a big source of decision paralysis for some. We've been asked more than a few times on how to "semantically convey info through the hierarchy". The bikeshedding/benefit ratio is quite high for these currently.

### Third-party Dependencies

Keep them to a minimum.

**Justification**: A compiled, statically typed language cannot model its dependencies easily by muddling along like in a dynamic language, especially when we're still piggy-backing on NPM/Yarn (to reduce learning overhead in the medium-term), both not made with Reason/BuckleScript in mind. Keeping dependencies simple & lean helps reduce possibility of conflicts (e.g. two diamond dependencies, or clashing interfaces).

### Documentation

Have them. Spend more effort making them great (examples, pitfalls) and professional rather than _just_ fancy-looking.

**Justification**: It's hard for newcomers to distinguish between a simple/decent library and one that's fancy-looking. For the sake of the community, don't try too hard to one-up each other's libraries. Do spread the words, but use your judgement too.

### PPX & Other Meta-tools

Keep them to a minimum. PPX, unless used in renown cases (printer, accessors and serializer/deserializer generation), can cause big learning churn for newcomers; on top of the syntax, semantics, types, build tool & FFI that they already have to learn, learning per-library custom transformations of the code is an extra step. More invasive macros makes the code itself less semantically meaningful too, since the essence would be hiding somewhere else.

### Paradigm

Don't abuse overly fancy features. Do leave some breathing room for future APIs but don't over-architect things.

**Justification**: Simple code helps newcomers understand and potentially contribute to your code. Contributing is the best way for them to learn. The extra help you receive might also surpass the gain of using a slightly more clever language trick. But do try new language tricks in some of more casual projects! You might discover new ways of architecting code.

### Publishing

If it's a binding to a JS library, don't publish the JS artifacts. If it's a legit library, publish the artifacts in lib/js if you think JS consumers might use it. This is especially the case when you gradually convert a JS lib to Reason + BuckleScript while not breaking existing JS consumers.

**Justification**: Be nice to JS consumers of your library. They're your future Reasoners.
