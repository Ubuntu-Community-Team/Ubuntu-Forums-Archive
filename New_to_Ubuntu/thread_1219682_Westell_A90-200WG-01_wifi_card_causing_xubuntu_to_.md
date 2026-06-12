---
title: "Westell A90-200WG-01 wifi card causing xubuntu to lock"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by Bavitz on 2009-07-22
Hi,

I have been having trouble with my westell wifi card, whenever I insert it after a short while it causes my nice new install of jaunty to freeze. From my research I believe this is called a kernel panic as the caps lock light blinks and everything stops. I thought that there was a driver problem so I installed nsidwrapper and loaded the TNET1130 driver as recommended by several sources. Still hanging when it goes in. It is detected, and I have about enough time to type in lspci to list it but then my laptop dies. I have read many posts with similar problems but not with this card or version of ubuntu, can anyone out there please shead some light on my problem?

Many thanks

---

### Post by Bavitz on 2009-07-22
p.s. I thought it could be my cardbus controller:(O2 Micro OZ601/6912/711E0)

someone had a similar problem here: [http://lists.infradead.org/pipermail/linux-pcmcia/2005-April/001867.html](http://lists.infradead.org/pipermail/linux-pcmcia/2005-April/001867.html) 

...but I have no idea whether yenta_socket is causing my problem or how to apply the suggested patch if it is

...is this a red herringr or the solution i have been looking for??

---

### Post by Bavitz on 2009-08-05
Ok, so I feel as if I have uncovered a dirty little secret of Linux - wireless support is not comprahensive!

So after 2 weeks of messing around I still have an umbilical cord to my router. Here is my progress so far:

I solved the kernel panic buy blacklisting the acx driver in modprobe.d. I also blacklisted all of the broadcom drivers for good measure

Then installed ndiswrapper and used the tnet1130 windoze driver as recommended by others for this card.

No crashing, and the card appeared to be recognised and was on, could detect wireless networks but not able to connect to my wireless network even when I lowered the security from WPA to WEP.

I then decided to remove network manager and replace it with wicd since this appears to have a more user friendly interface and is easier to customise. Still no joy. I can detect wireless networks but cannot connect. I have tried every way I can think of to configure the security settings including writing my own wpa_supplicant file to no avail. This card used to run fine in windows XP with WPA-PSK security, I am baffled as to why it is not working in linux when all the settings I can think of are correct. Can anyone shed some light on this please?

---

