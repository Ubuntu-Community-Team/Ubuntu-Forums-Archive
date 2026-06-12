---
title: "Working wireless connection, non-working nm-applet"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by Reedbeta on 2007-02-18
Hi all,

I have a bit of a strange problem.  I recently put Ubuntu 6.10 on my laptop, and I have gotten my wireless card working with ndiswrapper.  I have installed nm-applet, and it correctly lists the available wireless networks; however, when I select a wireless network, it tries to connect for awhile and then apparently fails and reconnects to the wired network (if available).

Using 'sudo ifup wlan0' from the terminal works correctly, and I have Internet access after doing so (and disconnecting from the wired network).  The wireless card and its driver seem to be working fine, it's just that nm-applet doesn't seem to realize that fact...:confused:

Does anyone know what might be causing this behavior and how I can correct it?

Also, random minor issue, when I press the hardware wireless key (Fn+F2 on my laptop), the wireless card turns off and won't turn back on till I reboot.  Is there any way to prevent this?

Thanks,
Reedbeta

---

### Post by Reedbeta on 2007-02-19
Never mind; I've gotten it to work.

For reference, what I had to do was comment out all the network interfaces (except lo) in /etc/network/interfaces, and i had to add ndiswrapper to /etc/modules.  After doing that and rebooting it seemed to function correctly.

---

