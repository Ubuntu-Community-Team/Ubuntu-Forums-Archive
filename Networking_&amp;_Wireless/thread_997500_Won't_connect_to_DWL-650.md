---
title: "Won't connect to DWL-650"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by lady_hybrid on 2008-11-29
To start off I'm not a computer whiz I can't type code or hack I'm just ur basic user that seems to have gotten lost along the way. I have no idea what's going on I have a D-Link Air DWL-650 card I went through the trouble shooting thing and it recognizes the device. Apparently it recognizes that it's on when I did the iwconfig it said the ESSID but when I tried to boot the kernel with the pci=noacpi nothing happened. Tell me what I'm doing wrong and let urselves feel superior to my measly intellect. As I said the only reason I even touched the terminal was cause the trouble shooter told me to otherwise I would never have touched it:confused: Help please

---

### Post by Fir3chi3f on 2008-11-30
download the windows driver for your card and put it in your home folder (under 'Places', at the top of your screen). unzip it

copy and paste this into the terminal and hit enter:
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk

```

Then go to System>Administration>Windows Wireless Drivers

Type in your password and direct it to your wireless driver you downloaded earlier, specifically the file with .inf at the end of it.

Reboot and post back if it doesn't work 

Good Luck!

---

### Post by Death_Sargent on 2008-12-27
Is there a way to do this in Kubuntu without networking since I can't find the laptops wired networking card.

---

