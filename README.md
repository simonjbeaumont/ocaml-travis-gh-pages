# Push your OCamldoc to Github pages from Travis-ci

## Usage

Append the following `install` stanza of your `.travis.yml`:

```yml
install:
  ...
  - wget https://raw.githubusercontent.com/simonjbeaumont/ocaml-travis-ghpages/master/travis-gh-pages.sh
```

and add the following to your the `script` stanza:

```yml
script: ... && bash -ex travis-gh-pages.sh
```

## Prerequisites

This relies on the existence of a `configure` script and `Makefile` such that
the docs are built as follows:

```shell
./configure --enable-docs
make doc
```

It also relies on you uploading an OAuth token to your Travis job. To do this,
create a token on your Github account settings page and upload it as follows:

```shell
gem install travis
travis encrypt GH_TOKEN=<token> --add
```

It will then push the contents of the resulting `<lib>.docdir` to the Github
pages branch of your repo.
