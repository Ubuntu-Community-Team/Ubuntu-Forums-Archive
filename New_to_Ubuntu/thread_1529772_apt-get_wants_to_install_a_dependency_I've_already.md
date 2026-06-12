---
title: "apt-get wants to install a dependency I've already installed by hand"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by EricCFlem on 2010-07-12
Okay, I'm confused.  I'm trying to install neverball and neverputt, but I've having issues.  I got into a weird, I-must-have-the-newest-version kind of a mindset, so (totally unrelated to installing the games), I went to the Sourceforge page and downloaded the newest version of the DejaVu fonts.

They installed and they work fine.  But when I try to install neverball and neverputt from the repositories, one of the dependencies is the ttf-dejavu-core package.  It's required and not simply a recommendation, so the "--no-install-recommends" option has no effect.  I have no idea if this will cause issues or not, what with me already having the same fonts installed.

But it brings up a larger point.  How does one get around this?  What if I've installed Firefox from the Mozilla source package, and then try to install mozplugger?  Apt-get attempts to install the repository version of Firefox, which I don't need.

Is there any way to force the installation of the package, even though apt-get or dpkg will be under the impression I don't have all the dependencies installed?

Thanks!

Eric

---

### Post by Zeike on 2010-07-12
```
[brandon@brandon-desktop:~] dpkg --force-help                     (07-12 19:36)
dpkg forcing options - control behaviour when problems found:
  warn but continue:  --force-<thing>,<thing>,...
  stop with error:    --refuse-<thing>,<thing>,... | --no-force-<thing>,...
 Forcing things:
  all [!]                Set all force options
  downgrade [*]          Replace a package with a lower version
  configure-any          Configure any package which may help this one
  hold                   Process incidental packages even when on hold
  bad-path               PATH is missing important programs, problems likely
  not-root               Try to (de)install things even when not root
  overwrite              Overwrite a file from one package with another
  overwrite-diverted     Overwrite a diverted file with an undiverted version
  bad-verify             Install a package even if it fails authenticity check
  depends-version [!]    Turn dependency version problems into warnings
  depends [!]            Turn all dependency problems into warnings
  confnew [!]            Always use the new config files, don't prompt
  confold [!]            Always use the old config files, don't prompt
  confdef [!]            Use the default option for new config files if one
                         is available, don't prompt. If no default can be found,
                         you will be prompted unless one of the confold or
                         confnew options is also given
  confmiss [!]           Always install missing config files
  breaks [!]             Install even if it would break another package
  conflicts [!]          Allow installation of conflicting packages
  architecture [!]       Process even packages with wrong architecture
  overwrite-dir [!]      Overwrite one package's directory with another's file
  remove-reinstreq [!]   Remove packages which require installation
  remove-essential [!]   Remove an essential package

WARNING - use of options marked [!] can seriously damage your installation.
Forcing options marked [*] are enabled by default.

```

Looks like dpkg --force-depends might do it for you.  Be careful with this though!  They aren't lying when it says you can seriously damage your installation.

---

### Post by EricCFlem on 2010-07-13
Thanks for that.  In the end, even after forcing the installation, I still ended up installing the font.  Oh well.  Thanks anyway!

---

