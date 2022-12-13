Testing

<a href="https://pypi.org/project/cookiecutter-pypackage-test"><img src="https://img.shields.io/pypi/v/cookiecutter-pypackage-test"></a>
<a><img src="https://img.shields.io/badge/python-3.10 | 3.9 | 3.8 | 3.7-success"></a>
<a href="https://github.com/hypothesis/cookiecutter-pypackage-test/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-BSD--2--Clause-success"></a>
<a href="https://github.com/hypothesis/cookiecutters/tree/main/pypackage"><img src="https://img.shields.io/badge/cookiecutter-pypackage-success"></a>
<a href="https://black.readthedocs.io/en/stable/"><img src="https://img.shields.io/badge/code%20style-black-000000"></a>

# cookiecutter-pypackage-test

A test package for our pypackage cookiecutter.

## Installing

We recommend using [pipx](https://pypa.github.io/pipx/) to install
cookiecutter-pypackage-test.
First [install pipx](https://pypa.github.io/pipx/#install-pipx) then run:

```terminal
pipx install cookiecutter-pypackage-test
```

You now have cookiecutter-pypackage-test installed! For some help run:

```
cookiecutter-pypackage-test --help
```

## Upgrading

To upgrade to the latest version run:

```terminal
pipx upgrade cookiecutter-pypackage-test
```

To see what version you have run:

```terminal
cookiecutter-pypackage-test --version
```

## Uninstalling

To uninstall run:

```
pipx uninstall cookiecutter-pypackage-test
```

## Setting up Your cookiecutter-pypackage-test Development Environment

First you'll need to install:

* [Git](https://git-scm.com/).
  On Ubuntu: `sudo apt install git`, on macOS: `brew install git`.
* [GNU Make](https://www.gnu.org/software/make/).
  This is probably already installed, run `make --version` to check.
* [pyenv](https://github.com/pyenv/pyenv).
  Follow the instructions in pyenv's README to install it.
  The **Homebrew** method works best on macOS.
  The **Basic GitHub Checkout** method works best on Ubuntu.
  You _don't_ need to set up pyenv's shell integration ("shims"), you can
  [use pyenv without shims](https://github.com/pyenv/pyenv#using-pyenv-without-shims).

Then to set up your development environment:

```terminal
git clone https://github.com/hypothesis/cookiecutter-pypackage-test.git
cd cookiecutter-pypackage-test
make help
```

## Releasing a New Version of the Project

1. First, to get PyPI publishing working you need to go to:
   <https://github.com/organizations/hypothesis/settings/secrets/actions/PYPI_TOKEN>
   and add cookiecutter-pypackage-test to the `PYPI_TOKEN` secret's selected
   repositories.

2. Now that the cookiecutter-pypackage-test project has access to the `PYPI_TOKEN` secret
   you can release a new version by just [creating a new GitHub release](https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository).
   Publishing a new GitHub release will automatically trigger
   [a GitHub Actions workflow](.github/workflows/pypi.yml)
   that will build the new version of your Python package and upload it to
   <https://pypi.org/project/cookiecutter-pypackage-test>.

## Changing the Project's Python Versions

To change what versions of Python the project uses:

1. Change the Python versions in the
   [cookiecutter.json](.cookiecutter/cookiecutter.json) file. For example:

   ```json
   "python_versions": "3.10.4, 3.9.12",
   ```

2. Re-run the cookiecutter template:

   ```terminal
   make template
   ```

3. Commit everything to git and send a pull request

## Changing the Project's Python Dependencies

To change the production dependencies in the `setup.cfg` file:

1. Change the dependencies in the [`.cookiecutter/includes/setuptools/install_requires`](.cookiecutter/includes/setuptools/install_requires) file.
   If this file doesn't exist yet create it and add some dependencies to it.
   For example:

   ```
   pyramid
   sqlalchemy
   celery
   ```

2. Re-run the cookiecutter template:

   ```terminal
   make template
   ```

3. Commit everything to git and send a pull request

To change the project's formatting, linting and test dependencies:

1. Change the dependencies in the [`.cookiecutter/includes/tox/deps`](.cookiecutter/includes/tox/deps) file.
   If this file doesn't exist yet create it and add some dependencies to it.
   Use tox's [factor-conditional settings](https://tox.wiki/en/latest/config.html#factors-and-factor-conditional-settings)
   to limit which environment(s) each dependency is used in.
   For example:

   ```
   lint: flake8,
   format: autopep8,
   lint,tests: pytest-faker,
   ```

2. Re-run the cookiecutter template:

   ```terminal
   make template
   ```

3. Commit everything to git and send a pull request
