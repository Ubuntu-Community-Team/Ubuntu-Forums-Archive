---
title: "wired card not working, wireless is..."
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by komma on 2007-08-08
Hi 

I have a starnge problem:

My IBM T60 is running Ubuntu 7.04 just fine, exept for one annoying thing.
My wired network card isn't working, the wireless card is working ok.

I am a newbie, please help.
Jakob

---

### Post by stryc9 on 2007-08-08
Same thing with me on a T41.  Do you have a link light when you plug in the cable?

---

### Post by komma on 2007-08-08
yes, all seems fine.

lspci lists the device allright, but the rest of the system can't see it.

(I am a total newbie)

---

### Post by komma on 2007-08-08
Found this:

[http://ubuntuforums.org/showthread.php?t=409281&page=2](http://ubuntuforums.org/showthread.php?t=409281&page=2)

---

### Post by komma on 2007-08-09
I solved the problem.

It seems that (as some guy correctly said) the EEPROM is corrupted on the NIC.

Downloaded proboot.exe and extracted it onto a cd.
After this i booted into DOS, using an old win98 cd, inserted my proboot cd and wrote "ibautil - defcfg".

You can download Proboot.exe from intel.com, just use search.

After reboot it works just perfect.

komma

---

