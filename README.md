# Heroku Buildpack: gostatic

This is a Heroku [buildpack](http://devcenter.heroku.com/articles/buildpacks) for
[gostatic](https://github.com/piranha/gostatic), a static site
builder written by [piranha](https://github.com/piranha).

## Using the buildpack

This assumes you have set-up a site locally with gostatic. Your
directory should look a little like this:

    $ ls
    config
    site/
    template.tmpl

    $ heroku create --buildpack https://github.com/pearkes/heroku-buildpack-gostatic.git
    ...

    $ git push heroku master
    ...
    -----> Fetching custom git buildpack... done
    -----> gostatic app detected
    -----> Installing Go 1.0.3... done
           Installing Apache v2.2.19... done
           Installing Virtualenv... done
           Installing Mercurial... done
           Installing Bazaar... done
    -----> go get github.com/pearkes/gostatic ... done
           go install github.com/pearkes/gostatic ... done
    -----> Compiling static site...
           Total pages to render: 6
    -----> Discovering process types
           Procfile declares types    -> (none)
           Default types for gostatic -> web
    -----> Compiled slug size: 13.5MB
    -----> Launching... done, v6
    ...

Your first deploy will be slow, but following deploys should speed
up dramatically as you use the dependency cache.

Note: Your deploy will fail if you do not have a gostatic `config` file
in the root of your project.

## Contributing

Current TODO's include:

- Caching the gostatic binaries, for faster deploys

To change this buildpack, fork it on GitHub. Push
changes to your fork, then create a test app with
`--buildpack YOUR_GITHUB_GIT_URL` and push to it. If you
already have an existing app you may use `heroku config:add
BUILDPACK_URL=YOUR_GITHUB_GIT_URL` instead of `--buildpack`.

More on [buildpacks](http://devcenter.heroku.com/articles/buildpacks).

## Thanks

Much borrowed from the [Go buildpack](https://github.com/kr/heroku-buildpack-go)
and [PHP buildpack](https://github.com/heroku/heroku-buildpack-php).

## License

Copyright (c) 2012 Jack Pearkes

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
