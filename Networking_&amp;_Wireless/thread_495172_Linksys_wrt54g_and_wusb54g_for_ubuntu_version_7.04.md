---
title: "Linksys wrt54g and wusb54g for ubuntu version 7.04"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by LordDragonSlayer on 2007-07-07
OK I finally got my computer repaired and, I decided to install ubuntu. But now I can't figure out how to get my Internet to work. I am using a router that goes to my dads windows xp and its all connected to a cabel modem. Please help!

I'm using a linksys router model number wrt54g and wusb54g and ubuntu version 7.04

If theres no way to do this then how would I set up a wired connection.

If theres and more information you need please ask.

---

### Post by LordDragonSlayer on 2007-07-07
please help me :cry:

---

### Post by introspectif on 2007-07-10
Hi

I'm not an expert, but I think you need to provide us more information. 

For a start, i suggest posting the output of 'iwconfig'. Go to Applications -> Accessories -> Terminal, type 'iwconfig' (without quotes) followed by <Enter>. Tell us that output.

Alternatively, I might suggest that you tinker with Administration -> Network . See if there are any signs that your wireless network card is detected.

---

### Post by LordDragonSlayer on 2007-07-10
it says 


lo                   No wireless connection

eth0              No wireless connection

---

### Post by LordDragonSlayer on 2007-07-10
and there's no signs its connection

---

### Post by kevdog on 2007-07-10
Please post the following 

Type commands at command prompt and cut and paste output:

lsusb
lshw -C network

Thanks.

---

### Post by LordDragonSlayer on 2007-07-10
I'm sorry but the commands u told me to enter don't go through as valid commands

---

### Post by introspectif on 2007-07-10
how about 'sudo modprobe rt2570' followed by 'iwconfig' again. is there a 'rausb0' now?

---

### Post by be4truth on 2007-07-11
I connected a Linksys WUSB54G Ver.4 to my xeron laptop and installed Ubuntu Mint. After the installation it worked out of the box. Haven't checked with encryption but otherwise works fine.

---

### Post by LordDragonSlayer on 2007-07-11
mines version two...

---

