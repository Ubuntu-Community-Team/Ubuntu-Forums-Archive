---
title: "[SOLVED] Can't get wireless working"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by YakkerZG54 on 2008-07-09
Linux Newbie (yes another one:).  

Just switched from XP. My ISP provided a wireless adapter (Netopia 3-D reach) which plugs into a USB 2.0 slot. Adapter is based on the Ralink 2500 chipset. Wireless worked fine under XP.

I have the latest Ubuntu Linux (Hardy). Researched and found that the driver is included (Rt2x00).

In terminal, at command prompt:

1) typing "lsusb" shows it sees the Ralink adapter
2) typing "sudo modprobe rt2x00usb" appears to work since before that
"lsmod" does not show the rt2x00usb but it shows up with "lsmod" after doing the "modprobe" command.

Also, in file /etc/network/interfaces I've commented out all but top 2 lines (I read that somewhere in my research).

What else do I need to do to get this working?

Note: I am online using my ethernet connection. That worked first time with no effort of any kind. Totally worked "out of the box". Unfortunately, it goes under a couple of doors and across a door-way. A trip hazard. I'd like to lose the ethernet cable and go wireless. Help anyone?  Would be most appreciated.

Thanks in advance.

---

### Post by YakkerZG54 on 2008-07-10
After more research, I'm thinking I'd be best off using ndiswrapper and the windows driver rather than the Linux driver.
I'll consider this thread closed.

---

### Post by Prefix100 on 2008-07-10
In my experience with ralink, its better to get it working nativly than with ndiswrapper.

What does ifconfig output?
What does iwconfig output?

Have you tried connecting to a network yet using the network-tools provided with ubuntu, if so, what happens/doesn't happen?

---

### Post by djfick on 2008-08-17
I had a question about why I couldn't set up my Netopia 3d reach usb adapter.  then I saw that I could go into System-Administration-Network, select and enable my wireless connection and set it up manually!  Now I 'm going to pass out from mental effort.  Good night all

---

