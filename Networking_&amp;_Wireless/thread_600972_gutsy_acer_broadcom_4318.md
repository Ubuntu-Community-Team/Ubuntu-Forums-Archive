---
title: "gutsy acer broadcom 4318"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by SpikeyMike on 2007-11-02
I have installed ndiswrapper and network manager but still cannot figure out how to set up my wireless network, I cannot find how to start the network manager, it doesn't appear in any menu and when I use the command ndiswrapper -m in the terminal I get the following error:

[COLOR="Red"][I]mikey@Mikeys-laptop:~$ ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
sh: cannot create /etc/modprobe.d/ndiswrapper: Permission denied
couldn't add module alias:  at /usr/sbin/ndiswrapper-1.9 line 804.
mikey@Mikeys-laptop:~[/I][/COLOR]

how do I start the network manager and how can I get the wireless network to connect, any advice greatly appreciated as I have been trying to get this working but without success.....

Spikey

---

### Post by rewrittenfromscratch on 2007-12-04
Whenever you're told that you don't have permission to do anything in the command line, assume it's because you're not the root user.

So. Try that same thing again, but prepend it with *sudo*.

That will give you root permissions.

---

