# Uuups Blocked &ndash; experimental block based WordPress Theme

Uuups Blocked is an experiment how to use only blocks in your WordPress theme.

- It's a block version of [Uuups theme](https://github.com/samikeijonen/uuups/).
- Check [theme experiments](https://github.com/WordPress/theme-experiments) for more information.

## Overview

Block based theme itself was pretty straightforward to put together. But there are so many details that needs polishing or custom blocks which makes block based themes hard to use in production.

## Semantics

In [theme experiments](https://github.com/WordPress/theme-experiments) repo I didn't see usage of basic HTML elemets like `<header>`, `<main>`, and `<footer>`.

I decided to hardcode them inside the templates. I have a feeling this is not desired solution and markup should live inside the blocks.

Maybe [content-block areas](https://make.wordpress.org/core/2019/09/05/defining-content-block-areas/) will resolve this issue?

## Skip to content block?

I didn't see "Skip to content" block and I decided to hard code it in `block-template-parts/header.html`. Doesn't feel ideal since it's not translatable string.

Maybe it's better to add using `wp_body_open` hook. Done.

## Site title block

[Site title block](https://github.com/WordPress/gutenberg/tree/master/packages/block-library/src/site-title) can have any heading level and even paragraph. That's nice but missing some usecases for projects.

- It's common UX to link site title to home page.
- Sometimes it makes sense that site title is `h1` in home page, and `<p>` in other pages.
- No way of adding custom class names.

Feels like a custom block if needed as a block.

## Navigation block

I'm not sure where to start:)

- I'm not sure where I add `aria-label` for the `nav`?
- I'm not sure how I add class name in to the nav anchor? Let's say I want to have "CTA" link in the navigation.
- No way of adding own markup like toggle button for mobile navigation. On the other hand these are OK if added using JS.
- Didn't tested sub-menus yet.

## Post title and content

There is no way of changing class name in

- post title &ndash; `<h1>`.
- post content &ndash; wrapped inside `<div class="entry-content"></div>`.

Not a huge issue but in custom project these will potentially be custom blocks.

## Archive

- How can I display posts from spesific category automatically?
- How can I display category title and description automatically?
- How can I display pagination?
