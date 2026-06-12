---
title: "need a lil bit of help"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by Lunatrix on 2007-07-09
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

step 6

my code thingy is

00:06.0 0280: 14e4:4320 (rev 03)

i dont know what to do! can anyone PLEASE help me?

---

### Post by kevdog on 2007-07-09
Who makes your wireless card, and what is the chipset??? Need this information.  If you have a windows driver on CD, then mostly we can bypass this step (the lspci lspci -n stuff).

---

### Post by Lunatrix on 2007-07-09
i have a belkin(<<wireless card) but idk how to get the chipset. and yup i have a CD that i use with windows to install the actual wireless card.

---

### Post by kevdog on 2007-07-09
Please provide following 

lspci -nn
lshw -C network
32 or 64 bit Ubuntu installation?

Thanks

---

### Post by Lunatrix on 2007-07-09
THATS A LOT OF TYPING.

and i forgot what version i downloaded. is there any way i can check. 

and is there anyway i can copy and paste all that info and save it onto a disk?

thanks.

---

### Post by kevdog on 2007-07-09
Ok here are the parts I want:

lspci -nn
Type the whole line that identifies the chipset of your wireless card -- Could be broadcom,atheros,marvell,ra,realtek.  Usually the line starts with Network Controller

lshw -C network
Give me what it says after driver=

Which did you install 32 or 64 bit Ubuntu??

You could burn a CD, but wouldnt using a USB stick be faster??

---

### Post by Lunatrix on 2007-07-09
lshw-bcm43 xx

lspci- broadcom corporation BCM4306 802.11b/g Wireless LAN Controller  [14e4:4320] (rev 03)

and i guess 32 but cause i chose this option

Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)

from this link

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Lunatrix on 2007-07-09
were you able to gather like a driver download so i can put it on a disk or something like that?

---

### Post by Lunatrix on 2007-07-09
nothing?

---

### Post by kevdog on 2007-07-09
Can you give me the exact model of your belkin card?? Ive looked based on the info you have given me, however there are too many cards with the exact criteria so far.  (I take it you have no driver or installation CD)

---

