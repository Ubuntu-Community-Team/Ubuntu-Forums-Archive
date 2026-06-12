---
title: "hidden networks and signal strength"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by scales on 2007-06-13
odd, but for some reason i am having a few issues with my atheros based card.

1.  i am unable to connect to hidden protected(wpa) networks using network manager.  does anyone have any suggestions on how i should go about fixing this?

2.  the signal strength in my card seems much weaker than what i get in xp.  is there a way to say re-calibrate these values?

---

### Post by Sendervictorius on 2007-06-13
There are lots of issues with Atheros cards (AR5212 chip sets) and feisty. I haven't got to the bottom of it, but it involves the madwifi drivers. One solution that worked for me was to remove the madwifi drivers and install ndiswrapper.

---

### Post by crazy_vyper on 2007-06-13
connecting to WPA protected networks you need the wpaapplicant (or something like it, search for Ndiswrapper wpa in google)

signal strength is also lower because it is emulated, as far as i know, you can't "rewrite" the data unless you want to "wrap" the drivers yourself, and have a hella job programming :P :popcorn:

---

### Post by scales on 2007-06-13
ok well i will give the ndiswrapper drivers a shot.  just for the record, i believe i have a gigabyte GN-WIAG01 module in my laptop.  i will post back after i have tried ndiswrapper.

---

### Post by scales on 2007-06-13
and i think i need to remove the madwifi drivers first.  right now i have an atheros hal entry in my "restriced drivers" folder.  would unchecking that box do anything?  and how would i remove madwifi?

---

### Post by scales on 2007-06-13
is ndiwsrapper hard?  will it fix my problems, (hidden networks, signal reading rather than the RSSI)? also i tried wicd in hopes that it would connect to hidden networks, it didnt seem to.

EDIT: Also i am sorry for posting so much, i could not figure out how to delete the old messages.

---

### Post by Sendervictorius on 2007-06-14
No, ndiswrapper is not hard. do a search on this forum to get instructions.

A few potential pitfalls though:
- download and install ndiswrapper package (e.g via synaptic) BEFORE you deactivate madwifi (that one got me! and I had to go back to my live CD)
- don't use ndisgk. Better to use the commandline ndiswrapper commands.
- Be sure you identify the correct windows driver .inf file when you install.  If you choose the wrong one, it can be hard to make your system clean again. (Choose win XP not win 98 for example)
- power down your PC when first rebooting. If you simply restart some cards can retain their settings from the previous session, which can cause problems on changing drivers.

Anyway - thats what worked for me.

Whether it will fix your problems - that is for you to find out.

---

