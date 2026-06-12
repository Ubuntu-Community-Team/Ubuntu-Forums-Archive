---
title: "Best wireless choice"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by blackfly on 2007-07-30
I am at the end of my rope with my Broadcom 4318 card on my Inspiron 2200.  It did work once, but never again...  

I have decided to buy a new card/usb I need that will automatically work out of box and be dependable in both secure and insecure wireless network settings.  

I have searched through the working wireless adapters above, but I want an opinion out of experience.  Anyone have any ideas on the best adapter for me to get that will just slide in to my laptop (PCMIA/PCI or whatever it's called) slot or usb adapter.

What do you think?

---

### Post by kevdog on 2007-07-30
If you can confirm that the card you have is not physically "dead" (like does it work in a Windows box), then Im not sure why it doesnt want to work in Ubuntu??  Did you try bcm43xx or ndiswrapper??  Do you have windows xp drivers for the card (or have access where you can download them??).

---

### Post by blackfly on 2007-07-30
I did use the GTK NDISwrapper + Windows driver method which I found in this forum.  It worked perfectly the first time, but I after I restarted, it never worked again...

It does work in windows.

---

### Post by kevdog on 2007-07-30
I suspect based on the information you just told me, that the module is not loading at boot.  Did you add ndiswrapper as a one word line to the /etc/modules file??

You can do it through gedit or by just typing:
more /etc/modules <---- allows you to view the file
echo ndiswrapper | sudo tee -a /etc/modules <---- adds ndiswrapper to the last line of the file.  

Modules listed in the modules file will get loaded on boot!

---

### Post by blackfly on 2007-07-30
I checked the file and it is set with ndiswrapper.  See, the problem is that it can see the networks, but it can't connect to them.  Don't know why.

---

### Post by kevdog on 2007-07-30
Can you post the following:

lshw -C network
ndiswrapper -v
ndiswrapper -l
modinfo ndiswrapper
iwlist scan
lsmod | grep ndiswrapper

/etc/iftab
/etc/network/interfaces
/etc/modprobe.d/blacklist

Is your router set without WEP/WPA/MAC filtering?
Is your router set to broadcast its ssid?

---

### Post by blackfly on 2007-07-30
The thing is though is that I never changed the settings on my router, so they are default.  I want to be able to connect to any insecure network with my laptop, so I don't want to  need specialized networks (I travel often).  I'll post the results of those tests tomorrow when I'm more awake...

---

