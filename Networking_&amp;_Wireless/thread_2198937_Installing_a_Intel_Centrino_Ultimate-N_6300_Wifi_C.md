---
title: "Installing a Intel Centrino Ultimate-N 6300 Wifi Card into an Aspire Revo"
date: 2014-01-11
forum: Networking &amp; Wireless
---

### Post by kara.l.walker on 2014-01-11
First thing's first, I am a total Ubuntu noob and have doing much googling to try and solve my issue before arriving here, but it appears I have hit a wall.  I have recently installed XBMCbuntu onto an Asus Aspire Revo R3700 in hopes to make it a nice little HTPC for my bedroom.  The wifi card died on it a while ago and I recently replaced it with an Intel Centrino Ultimate-N 6300 card.  The problem I am having is that when the new card is installed in the system, Ubuntu initially boots fine and has me go through some loading screens, but I eventually lose the video connection to my monitor.  I have troubleshot this with the system by removing the wifi card entirely and booting and it has no issues.  It boots without a wifi card and it boots with the old wifi card, but whenever the new card is installed, buh bye video.  I assumed this was a driver issue and went through the process to install the new driver for the wifi card.  When I pasted the ucode into lib/firmware, it produced an error (unfortunately I cannot remember what the error was off the top of my head).

Any suggestions on where I should go from here?  I'm a complete Ubuntu noob so navigating this OS has been a bit of a pain.  I could always find the original wifi card on ebay or something and simply replace that, but I would prefer the upgraded card.

Thanks!

---

### Post by praseodym on 2014-01-11
Hi,

try these things:

First:
Reset the BIOS to default settings and reboot (for the new wifi card)
Second:
Please show the terminal outputs of these commands:
```
uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```
Does LAN work?

---

### Post by kara.l.walker on 2014-01-12
The LAN does work.  

Before I jump into the terminal outputs, I tried to paste the driver file into lib/firmware again to see what my actual error was.  It is telling me that the permission is denied to open that file, so I'm assuming it never pasted in the first place and is likely at least one of the reasons why this still isn't work.  Any insight on why the permission would be denied?

EDIT:  Okay, I got the new file pasted without the error, loaded default settings in the BIOS and still getting the video to shut off with the new wifi card installed.  I may need a little assistance on how to output the terminal outputs so I can post them here.

---

### Post by praseodym on 2014-01-12
Copy them into a text file and upload it or copy them herein. Open the terminal with CTRL+ALT+T

---

