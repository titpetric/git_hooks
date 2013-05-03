git_hooks
=========

Common git hooks to be used with git-hooks and git submodules across several projects


What does it do?
----------------

The provided git hooks are pre-commit hooks. They are currently dealing with LINT
checks for various file types. What this means is, that if a file has invalid
syntax, git will not let you commit it into your repository, forcing you to fix it.

Short term goals are to verify:

- Javascript (catches some IE specific bugs which are hard to track down)
- JSON checks
- PHP checks
- XML checks
- CSS checks

Additional checks in the future could enforce

- Unit testing (phpunit,...)
- Commit message policy


Requirements
------------

- [git-hooks](https://github.com/titpetric/git-hooks) binary to install hooks
- php, bash, perl, diff, sed, awk (most of these probablly)
- Per-hook dependencies (...)


How to use it?
--------------

Adding the git_hooks to your project is dead simple.

First, be sure to install the [git-hooks](https://github.com/titpetric/git-hooks) binary:

```
wget https://raw.github.com/titpetric/git-hooks/master/git-hooks
chmod a+x git-hooks
```

Place the `git-hooks` file somewhere in your executable path.
In your git project root create a git_hooks submodule like this:

```
git submodule add git://github.com/titpetric/git_hooks.git git_hooks
```

Install the git hooks by running `git-hooks --install`. This will automatically
run the relevant git hooks for your project, and you can still cherry pick
which git hooks you wouldn't like to run manually. Running git-hooks without
--install option lists the hooks you have currently installed. You can take
a look at the [git-hooks project page](https://github.com/titpetric/git-hooks)
for more information about this.

If you want to update your git hooks, just go into the git_hooks
folder and issue a `git pull` to update them to the latest version.


Why?
----

I don't like to commit any kind of files with syntax errors. Improving our
development environment introduces policies and standards that need to be
enforced - if possible with automation.
