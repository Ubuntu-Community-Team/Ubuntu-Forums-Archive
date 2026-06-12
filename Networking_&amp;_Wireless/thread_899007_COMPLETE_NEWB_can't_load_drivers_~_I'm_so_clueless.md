---
title: "COMPLETE NEWB can't load drivers ~ I'm so clueless...."
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by jal301 on 2008-08-23
My attempt is to install my wireless card: D-Link DWA-542.

Currently, when I run iwconfig, it shows lo and eth0 have "no wireless extensions."

So far, I found that it has an Atheros AR5416 chip which needs to be installed.

So I found this site which says that ath5k is the way to go since so many people are having issues with other drivers, etc....

I downloaded the "compat-wireless-2.6.tar.bz2" dated for 2008-08-06 and I get a set of instructions to enable ath5k and mac80211 and that is where I begin to be completely lost.  Can somebody please let me know what EXACTLY is to be done for the enable ath5k step of the process below.  Assume I know absolutely nothing about Ubuntu since this is my first day on it.  There is a code window shown with this instruction and I know how to bring up the terminal window but I cannot get it to do anything beyond showing that I am on the Desktop level of my computer within that terminal window.  Thank you very much in advanced for your help!

Josh

[http://linuxwireless.org/en/users/Drivers/ath5k](http://linuxwireless.org/en/users/Drivers/ath5k)

---

### Post by jal301 on 2008-08-24
The problem comes in with following the supplied directions which are to be very explanatory but I just don't know how to follow some of the simpler code related commands - as far as how to run/execute them and from what window.

---

### Post by wreckedcarzz on 2008-09-01
I am having issues getting my WPC300N card working as well, but that's another topic.

Most commands need to be run from the Terminal window - some need you to type 'sudo' (no quotes) before a command (sudo means **S**uper **U**ser **DO**) to allow the computer full "admin" access (root in Ubuntu).

I can't really help, but at least you can enter the commands now :)

---

