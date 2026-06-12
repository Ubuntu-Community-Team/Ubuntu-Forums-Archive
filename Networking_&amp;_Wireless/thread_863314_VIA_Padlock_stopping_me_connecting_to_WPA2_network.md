---
title: "VIA Padlock stopping me connecting to WPA2 network"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by Sk1nnyMan on 2008-07-18
I am having trouble connecting to a WPA2 network with my Intel 3945ABG wireless chipset using iwl3945, I have detailed this in much more detail in [another thread]("http://ubuntuforums.org/showthread.php?t=859486").

Monitoring my kern.log I found something interesting:

> Jul 18 15:57:09 skinnyman-laptop kernel: [  115.213728] padlock: VIA PadLock not detected.

After this line shows up in my kern.log I am usually able to connect to the network despite numerous disconnects before.

I know roughy what VIA PadLock is and I don't need it as I have no VIA components in my laptop (especially the CPU).

I just want to know why VIA PadLock is showing up, if it is actually related to the issue I am having and how to disable it if it is related.

---

### Post by Sk1nnyMan on 2008-07-19
<Sigh> I thought this was supposed to be a support forum? I have posted twice here with no replies what so ever.

Thanks Ubuntu, your Debian roots serve you well.

---

### Post by chili555 on 2008-07-19
Please try two things. First, *sudo gedit /etc/modprobe.d/blacklist* to add the following:```
blacklist padlock_aes
blacklist geode_aes
```Proofread, save, close and reboot. Is you problem resolved? Please post back for the benefit of the searchers.

Second, there is no need to post with a little jab at the volunteers who try to help.

---

### Post by igorpregoun on 2008-08-24
Similar problem (Same error message on tty1, but no problem with wifi) and your solution worked perfectly.

Thanks a lot chili555.

Do you know what the cause of the problem was, and why blacklisting these two modules solved it ?

---

