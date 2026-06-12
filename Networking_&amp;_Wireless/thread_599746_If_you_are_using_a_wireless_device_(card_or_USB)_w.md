---
title: "If you are using a wireless device (card or USB) what is your chipset??"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-11-01
Concurrently with another ongoing thread: [http://ubuntuforums.org/showthread.php?t=594857](http://ubuntuforums.org/showthread.php?t=594857), Im trying to get a feel for the chipsets people are using and compare this with the number of chipset problems.  

Interestingly the top two chipsets people are having problems with are #1 - Ra and #2 - Broadcom -- and these are two chipsets in Gusty with the drivers contained in the distribution.  A proposed "out of the box solution" that isnt really working too well

Please select the wireless chipset you are using!

You can find your wireless chipset by typing at the command line

lspci -nn 

Many devices connected to the pci bus will be listed, however look for the one relating to your wireless (not wired) device

If you select other, can you post your chipset?

---

### Post by kevdog on 2007-11-09
Id vote twice if I could -- Im running Broadcom 4306 along with an Atheros card.  Honestly it seems like my Broadcom/ndiswrapper/bcmwl5 card has better range than my Atheros/madwifi card although I havent tested it scientifically.  Because Im running g-based cards -- both suffer greatly from home cordless phone interference.  When the cordless phone is in use, both cards go down!

---

