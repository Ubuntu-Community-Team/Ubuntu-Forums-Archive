---
title: "Possible to deselect &quot;automatically installed&quot; packages from terminal?"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by kansasnoob on 2009-10-16
I know that I can go to Synaptic and click on a package that's marked for Automatic Installation and simply untick that option so it's no longer installed during an update, but wondered if the same can be achieved using the command line.

For instance, in the process of converting Jaunty to Grub2 (package name: grub-pc) os-prober was "automatically installed" and remains marked as such even if I revert to legacy-grub. Certainly it's easy enough to go to Synaptic and just search for "os-prober" and untick the auto-install, but wondered if the same can be accomplished safely using the command line.

BTW, simply using apt-get -f install (or install -f) does not always dump these "auto-installed" dependencies, so every time an update installs it reinstalls the unwanted package. It's hardly a "big deal" because I know how to fix it using Synaptic, but I rather like learning the cli, and it's ultimately sweeter to use a command like:

> sudo apt-get --purge remove grub-pc grub-common os-prober && sudo apt-get install grub

Than having to say, "go to synaptic and mark grub-pc, grub-common, and os-prober for complete removal, then mark grub for installation".

It's also less time consuming:)

Oh and I don't want to "ignore all"!

---

### Post by lukjad on 2009-10-19
I wouldn't try and do that, the automatic dependancies are usually a good thing. I suppose dkpg might be what you are looking for, but I'm not sure.

---

### Post by louieb on 2009-10-19
IIRC Synaptic uses aptitude and aptitude uses apt-get. If you can do it in Synaptic - aptitude probably does it too.  

Besides install aptitude/apt-get has other **actions **

> 
...
       aptitude [<options>...] {changelog | full-upgrade | download |
                forbid-version | hold | install | markauto | purge | reinstall
                | remove | show | unhold | unmarkauto | build-dep |
                build-depends} <packages>...



and actions have **options** such as
--no-new-upgrades
--without-recommends
--with-recommends
....

and  apt-get  has its own actions and options.  

:guitar:I don't mind using the cli but there are times when I'm sure glad Synaptic is there too.

---

### Post by martrn on 2009-10-19
Type ```
sudo dpkg -l
``` to list all the installed packages you have installed and ```
sudo apt-get autoremove
``` to automatically remove dependence-ies no longer needed.

type ```
man apt-get
``` to explain how to use apt-get utility and read the cli way APT package handling utility manual.

---

