---
title: "Xubuntu don't start"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by AbilioBras on 2009-10-21
Hi, 
 
I just donwloaded a xubuntu-9.04-alternate-i386.iso and installed it on a laptop (CPU: Celeron - 466 MHz - RAM: 192 MB - HDD: 80GB), at the end the system reboot and show me a "xubuntu" image, but the progress bar stops right in the beginning and stays there forever...:(
 
Anyone has any clue about that?
 
Many thanks
 
 
Abilio
 
 
PS: I try to restart on a recovery mode... it stops after
 
"udevd-event[1102]: 'path_id /devices/platform/pcspkr/input/input2/event2' abnormal exit"

---

### Post by Little Girl on 2009-10-28
What happens if you remove quiet splash from GRUB and then try to boot? Instructions for how to do this temporarily and permanently are here: [http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/]("http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/") and will work for Xubuntu the same way they do for Ubuntu. I recommend trying the temporary method. I'm not sure if it will fix the problem, but it may give you more information to work with. :p

---

