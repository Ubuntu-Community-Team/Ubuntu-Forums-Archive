---
title: "Wireless Card is Physically Not Being Detected"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by shy_wolf3x4 on 2007-06-30
Hi! I'm running feisty fawn with Dlink's DWL-G122 wireless card on a usb dongle. I have used feisty before(the exact same version, although the cd is newly downloaded) on the same computer and this card worked out of the box, it only had to be downed, configured and then upped. I was originally running a ubuntu / windows dual boot but I wiped my HD and now only have Ubuntu.
Now however the card is physically not being detected.

For example:

sudo iwconfig 

shows eth0 and lo(I also have an ethernet card which I don't use) 

If I then remove the card and reinsert it it is not detected and sudo iwconfig shows the same thing.
There does not even appear to be a message created in the system log.

Is there anything I can do to make ubuntu detect it?

Ps. I am not asking for help with ndiswrapper at all, I did not need it before.

Thank You

---

### Post by kevdog on 2007-06-30
Please provide the following to see if the card is physically detected as present:

lshw -C network
lspci
lsusb

---

### Post by shy_wolf3x4 on 2007-06-30
lshw -C network

SCSI flashes briefly(wrong command maybe?)

lsusb

Bus  002  Device  002: ID 0a48:3239 I/O Interconnect
Bus  002  Device  001: ID 0000:0000
Bus  004  Device  001: ID 0000:0000
Bus  005  Device  001: ID 0000:0000

lshw without options and lspci are very extensive, I am currently using a windows vista compuyer to access these forums, the only way I have to transfer the output is by cd. Is there a ubuntu program I can save them in and transfer them to windows with?

I should also mention that I connected the wifi card without the usb dongle to every usb port on the computer and there were still no results, I also connected to my vista pc and new hardware was detected, so its not the card.

If this isn't enough info and there is no wasy to transfer output from lshw and lspci then let me know, if it is necessary I will type them out. I should also mention there is an hp printer hhoked up through usb.

Thanks again.

---

### Post by kevdog on 2007-06-30
Wow!! Im not sure what to tell you.  This basically is a wireless USB device.  Im trying to find the chipset of the wireless device but the lsusb command is not helping me find that.  

Do not post the entire output.  Do lshw.  Is there anything listed under the subsection usb??

---

