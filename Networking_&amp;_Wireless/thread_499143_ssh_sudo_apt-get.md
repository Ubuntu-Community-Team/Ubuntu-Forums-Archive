---
title: "ssh sudo apt-get"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by shinji123 on 2007-07-12
Hey guys!!!

I need to connect with ssh for installing ndiswrapper in a remote pc.
But when I type  
  
  sudo dpkg -i ndiswrapper-common_*.deb
  sudo dpkg -i ndiswrapper-utils*.deb
  sudo dpkg -i --force-depends ndisgtk_*.deb

all the three commands seem to work but the konsole doesn't return messages and ndsiwrapper doesn't work. Why? Is there a problem in privileges or ssh doesn't return messages?

Thanks

---

### Post by KRossKoWolf on 2007-07-12
When connected do you have only a terminal displayed to you or is it the full Metacity etc, Interface?

If it's the latter, try using Synaptic Package Manager to install them, search for each and install them from there.

If it's the former, and your connected using SSH, try using the "sudo aptitude install ndiswrapper-common" command's etc.

---

### Post by shinji123 on 2007-07-12
when connected I have only a terminal ....


girardim@agr2959:~$ sudo dpkg -i ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb

I try your command:

girardim@agr2959:~$ sudo aptitude install ndiswrapper-common
Password:
girardim@agr2959:~$

but there is no output as well as


girardim@agr2959:~$ sudo apt-cache showpkg pkgs
girardim@agr2959:~$

---

