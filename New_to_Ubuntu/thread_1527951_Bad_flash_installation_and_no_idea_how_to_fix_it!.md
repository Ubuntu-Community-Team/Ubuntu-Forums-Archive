---
title: "Bad flash installation and no idea how to fix it!"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by kmbahar on 2010-07-09
Hi there,

After numerous tests on wubi I finally decided to go all out with Ubuntu on my eee pc 1201t and did a complete install yesterday. Everything was fine out of the box except for the wireless, which I found a great fix for, and was getting the hang of how to install software and such.

However, today I was trying to install the flash plug-in for firefox when the installation froze (best way I can describe it coming from windows) and didn't move at all. A lot of the interface was either incredibly slow or flat out not responsive at all and I did what a windows user would instinctively do - ctrl-alt-del. Since I couldn't find an equivalent to 'task manager' I decided to restart the computer and now the flash plug-in is installed but not properly - it's detected as installed on my software centre, but it's not working. I can't seem to remove it nor re-install it.

Any ideas how I can fix this? I'm guessing I have to fix something manually via the terminal but I have no idea what.

---

### Post by patchwork on 2010-07-10
You can try using ```
sudo apt-get install -f
``` and```
sudo dpkg --configure -a
```where the -f option for apt-get install is described by>  -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution. If packages are
           specified, these have to completely correct the problem. The option
           is sometimes necessary when running APT for the first time; APT
           itself does not allow broken package dependencies to exist on a
           system. It is possible that a system's dependency structure can be
           so corrupt as to require manual intervention (which usually means
           using dselect(1) or dpkg --remove to eliminate some of the
           offending packages). Use of this option together with -m may
           produce an error in some situations. Configuration Item:
           APT::Get::Fix-Broken.
and the dpkg --configure -a is described by> --configure package...|-a|--pending
              Reconfigure  an  unpacked  package.  If -a or --pending is given
              instead of package, all unpacked but unconfigured  packages  are
              configured.

              Configuring consists of the following steps:

              1.  Unpack  the  conffiles, and at the same time back up the old
              conffiles, so that they can be restored if something goes wrong.

              2. Run postinst script, if provided by the package.

---

### Post by lovinglinux on 2010-07-10
Please provide the errors you get from the terminal when trying to install/remove flash.

---

