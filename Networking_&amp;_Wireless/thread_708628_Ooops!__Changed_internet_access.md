---
title: "Ooops!  Changed internet access"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by flyinggreg on 2008-02-26
I am running a dual boot system with Win 2k and Ubuntu 7.1 and installed GPE on my iPaq 3700.  I have been trying to file synch with it and changed access and settings on my desktop.  Of course, the brainiac I am, I forgot to backup the files.  Now I can't seem to access the internet from Ubuntu.  I am pretty much a newb with Linux and I know enough to get into trouble ;)  Can someone give me some guidance where to start looking in the config files to repair my connection?

Thanks

---

### Post by SpaceTeddy on 2008-02-26
please post the output of the following commands

> cat /etc/network/interfaces
ifconfig
iwconfig
route -n

also, how are you connecting to the internet ? wireless or lan ? or do you have a dsl modem directly plugged into your computer ?

---

