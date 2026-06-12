---
title: "Wireless Problem on Asus Eee PC"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by RelativelyQuantum on 2008-08-08
I've installed the old Hardy beta (I still had the ISO) onto my eeepc, but can't get wireless connectivity. The "networking" section in the system menu doesn't have wireless as an option, so I'm assuming it's not recognizing my card.

How would I solve that?

---

### Post by ubuntuguru on 2008-08-08
you will need to get a kernel with the module for your wireless card

---

### Post by dca on 2008-08-08
I wouldn't go with the Beta either because even if you updated packages, some still might get missed because of possible changes made from Beta to release.
 
The Asus eeeeeeeeePC (correct me if I'm wrong) uses a mini-PCI-e (express) WiFi card.
 
if you type: lscpi
at CLI, it should reference as 'Atheros AR242x' if you installed the complete 8.04 or 8.04.1 Ubuntu 32-bit desktop release.
 
If it lists anything else I'm out.  I got the card to work on non-Asus laptop by using this:
 
[http://ubuntuforums.org/showthread.php?t=662877](http://ubuntuforums.org/showthread.php?t=662877)
 
...it's kind of confusing because if it uses the same card I'm thinking of it lists in pre 2.6.23 kernels as AR5007eg, and in Windows as AR5006.
 
...if it's any consolation and you can't get it figured out, Mandriva offers a eeeeeeeeePC rebuild of their distro that I believe includes the patched 'MadWifi' driver ready to go out of the box.
 
Good luck.

---

### Post by RelativelyQuantum on 2008-08-16
Really appreciate the information! As I'm in a technological hole it'll be some time before I can actually test the drivers, but when I do I'll be sure to post my results.

---

### Post by VMan on 2008-08-18
Go to the eeeuser.com forums.  One of the members has compiled a custom kernel and modules for Ubuntu 8.04.1 i386 for the EeePC.  He has complete and detailed instructions.  All of my hardware (as far as I can tell, I've only had the laptop just over a week) works perfectly.  Look in the Ubuntu subforum for adamm's custom kernel and modules.  I kinda wish they would add a subforum here for EeePC users like there is for Macs.

---

