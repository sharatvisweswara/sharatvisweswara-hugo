---
title: "Blog Setup"
date: 2017-07-09T17:56:43-07:00
draft: false
---

This blog is generated by [Hugo](https://gohugo.io),
hosted on [Github Pages](https://pages.github.com)
and uses [Travis CI](https://travis-ci.org) to glue them together.

I use two separate repositories: one for my [sources][1],
and a separate one for [output][2]. Some examples
combine both in a single repository, using separate branches for
sources and output; but I prefer separate repositories.

[1]: https://github.com/sharatvisweswara/sharatvisweswara-hugo
[2]: https://github.com/sharatvisweswara/sharatvisweswara.github.io

The glue is in [`.travis.yml`][4] and it performs the following in order:

1. Install Hugo using `go get`.
2. Clone the output repo into the `public` subdirectory.
3. Generate output using `hugo`; this overwrites existing content in `public`.
4. Commit and push changes in `public` to the output repository.

To enable step 4 I clone the output repo using the `https` protocol instead
of the `git` protocol, and use a [Github Access Token][3] so that Travis can
push to the repo as well. The access token is configured in Travis
as an environment variable; this avoids exposing it in `.travis.yml`.

[3]: https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/
[4]: https://github.com/sharatvisweswara/sharatvisweswara-hugo/blob/master/.travis.yml

I can now create my posts using Markdown, push my changes
to Github, and minute or two later, they're live!

Let me know if this method works for you, or if you have any other feedback on it.
