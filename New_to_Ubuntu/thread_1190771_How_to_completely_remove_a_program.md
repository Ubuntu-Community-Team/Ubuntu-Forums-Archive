---
title: "How to completely remove a program?"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by The Bright Side on 2009-06-18
Hey guys,

I've been looking for this in the forum and on google, but couldn't seem to find any coherent advice. My problem is: when I remove a program, in my case Aqualung and Audacious, with Synaptic (selecting "completely remove, including configuration), it seems the traces of the program still remain on the system - it is never completely uninstalled.

When I search the system for files containing the program's name, a considerable number of files will show up. They shouldn't be there after an uninstall, should they?

Also, when I reinstall a program, it behaves as if it was never gone. All the configurations and changes are still intact, all plugins installed, everything.

This is a major problem if you have a broken program on your system and want to do a clean reinstall. Aqualung is messed up, so is Audacious, and I don't know what else to install :-(

Thanks for your help!
Matthias.

---

### Post by hayden92 on 2009-06-18
In synaptic click on the "status" button, and look for "residual config" if anything shows up there, you can delete it. This is probably where the files are.

---

### Post by alphacrucis2 on 2009-06-18
```
apt-get remove --purge package
apt-get clean

```

---

### Post by Mornedhel on 2009-06-18
Residual config removal (through Synaptic) and apt-get --purge remove do not take care of user-specific configuration files, only system-wide configuration. Most of the time those are located at ~/.programname (file or folder). These are hidden files in your home directory. (Hidden files are denoted by their first character, a dot, and do not show in Nautilus unless you select View > Show Hidden Files or type Ctrl+H.)

You can safely delete an application's user configuration files once you have removed the package, just be careful not to delete the wrong files by mistake.

---

### Post by LewRockwell on 2009-06-18
it's fairly common for software to "leave" some files related to items such as installation settings, preference settings, and your previous projects utilizing that software

you may have uninstalled programs in the past(maybe in windoze?) where the uninstaller asked you whether or not you wanted to save certain parts

this can sometimes be a benefit, and sometimes a curse

if you really want to uninstall and then hunt down every last remnant then I would recommend attempting to follow that particular software's recommendations for uninstalling/removing

personally, we find that "most" "users" think they "need" bloated operating systems like the bohemouth Windoze and/or Mac OSX, and/or any of the *nix distros that are "chasing" those other two

the fact of the matter is that most people don't need it and it invariably becomes a pain in the behind

why would the average internet user need huge multi-GB operating systems just to check email and surf the interwebs? Most don't.

there is no real reason to chase the big-box-distros except in some mistaken attempt to convince retailers to pre-install such an OS on their offerings.

obviously the backroom arm-twisting of manufacturers, by Microsoft, will continue since no manufacturer wants to be cut off "cold-turkey" from Windoze.

---

