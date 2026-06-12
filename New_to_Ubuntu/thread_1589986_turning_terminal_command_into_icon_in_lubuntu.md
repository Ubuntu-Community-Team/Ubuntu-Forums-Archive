---
title: "turning terminal command into icon in lubuntu?"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by dcalvani on 2010-10-07
I'd like to turn the command

*sudo wvdial*

into a desktop icon - so that it's easier for my family members to connect to the internet with an internet dongle. 

How do you do this in Lubuntu 10.04? I seem to recall doing it once in Ubuntu (I think I right-clicked on the desktop and created a launcher or something) but can't find anything of the sort in Lubuntu. 

Can you help?

---

### Post by nikefalcon on 2010-10-07
Maybe you could put a launcher on your desktop. I haven't used lubuntu, so I can't help you with that.

Try this:[http://wiki.archlinux.org/index.php/LXDE#lxpanel_Add_Launcher_.28application.29](http://wiki.archlinux.org/index.php/LXDE#lxpanel_Add_Launcher_.28application.29)

Looks like you'll have to manually make a .dektop file ;don't know how t do that in LXDE though.

---

### Post by dcalvani on 2010-10-08
thanks nikefalcon
I gave it a try + had a look at the link but can't make any sense out of it...
for some reason in Lubuntu (at least on my machine) the GPRS connection doesn't appear on network manager (above the wifi connections) on the taskbar, so I can only activate it on terminal...

---

### Post by madmax75 on 2010-10-08
> **dcalvani said:**
> I'd like to turn the command

*sudo wvdial*

into a desktop icon - so that it's easier for my family members to connect to the internet with an internet dongle. 

How do you do this in Lubuntu 10.04? I seem to recall doing it once in Ubuntu (I think I right-clicked on the desktop and created a launcher or something) but can't find anything of the sort in Lubuntu. 

Can you help?

Do you have a USB broadband dongle, like Huawei or such, which connects to the net via the cell phone network?

Have you tried setting it up through the Network Manager? You should install **usb-modeswitch** and **usb-modeswitch-data** before setting the connection up. They're in the repositories, and enable your USB dongle to switch its mode from flash drive to modem. Ubuntu sees them as flash drives and that's why they often don't seem to work (which seems to be a common problem with these things).

I used wvdial with my old Huawei, but installing usb-modeswitch (plus -data) + Network Manager is somewhat easier.

---

### Post by dcalvani on 2010-10-10
done it. Installed usb-modeswitch + data, to no avail. Nothing shows on Network Manager...
I tried in Ubuntu, though, and it does show there. There seems to be an issue with Lubuntu (?)

any idea?

---

