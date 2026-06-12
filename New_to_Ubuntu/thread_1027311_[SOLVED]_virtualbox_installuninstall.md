---
title: "[SOLVED] virtualbox install/uninstall"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by MaxVK on 2009-01-01
Hi, and Happy New Year to all.

I'm running 7.10 for the moment and I suddenly have the need to use IE for testing some web development. I already have Virtualbox OSE installed with Windows running in it, but it has stopped working, apparently due to the updated kernel.

The solution seems to be to install the latest version of virtualbox and add it to the sources file so that it stays up to date.

However, the version to install is not the OSE version and this leaves me with a concern.

I'm pretty sure that installing the non-free over the OSE version is not a great idea, so I'm thinking that I need to uninstall the OSE version first, but I am concerned that my virtualbox windows installation may be unable to boot with the new version.

Can anyone shed any light on this please? Do I need to remove the OSE version first, and will my virtualbox windows installation still work with the non-free version?

Cheers

Max

---

### Post by nhasian on 2009-01-01
nothing wrong with installing the nonfree version of virtualbox.  you even get USB support with it :)

follow my instructions here:

[http://ubuntuforums.org/showthread.php?t=1015045](http://ubuntuforums.org/showthread.php?t=1015045)

but replace the word intrepid with gutsy in the repo lines.  so in */etc/apt/sources.list* you would put:

```
deb http://download.virtualbox.org/virtualbox/debian gutsy non-free
```

---

### Post by Dedoimedo on 2009-01-01
Did you try IEs4Linux:
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

Tutorial:
[http://www.dedoimedo.com/computers/ie_linux.html](http://www.dedoimedo.com/computers/ie_linux.html)

BTW, you can also use user agent switcher extension for Firefox and Opera per-site user agent switcher to change the way your browser identifies, for testing/compatibility purposes.

Dedoimedo

---

### Post by MaxVK on 2009-01-01
Thanks nhasian

Max

---

