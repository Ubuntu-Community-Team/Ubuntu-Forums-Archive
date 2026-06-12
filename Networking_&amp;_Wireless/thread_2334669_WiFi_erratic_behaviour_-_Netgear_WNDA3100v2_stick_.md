---
title: "WiFi erratic behaviour - Netgear WNDA3100v2 stick and Ubuntu 16.04 LTS"
date: 2016-08-21
forum: Networking &amp; Wireless
---

### Post by shinryu2 on 2016-08-21
Hi all,
fairly new to Ubuntu. I recently installed version 16.04 and have been using a Netgear USB dongle for WiFi with Windows.
I ran through all the system updates and installed the drivers as per this thread:
[https://ubuntuforums.org/showthread.php?t=1964173](https://ubuntuforums.org/showthread.php?t=1964173)

After installing the drivers and rebooting, I could indeed get a WiFi signal (i.e. see the wireless networks around me) but the network manager would just attempt to connect forever without success.
After scouring through some forum threads I attempted to disable power management and this seemed to improve the situation - I could connect to my home router and reach the internet. However, after a while my connection dropped and I couldn't get it back.
After many, many attempts, I've had the following situations occur seemingly at random:
1) WiFi adapter is not recognized. Unplug it, plug it back in, go to 2.
2) WiFi adapter is recognized but cannot connect to the internet.
3) Connect to the router, router sees the PC connected, but PC cannot access the internet. Any other device connected to the same router working fine.
4) Connect successfully and able to reach the internet. Connection drops after a few minutes, go to 2.

Another annoying quirk is that when I shutdown Ubuntu and boot into Windows 10 (dual boot installation), Windows seems to have trouble identifying the Netgear adapter and I have to unplug/plug it back in several times and sometimes even shutdown and boot again to get it to work.

As of right now, changing the power management setting doesn't seem to make a difference anymore (and it turns back on automatically after a while anyway). 9 times out of 10 I end up in situation #2 and cannot connect. I am using a wired connection right now and ran the wireless info script (from [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)). Output is attached. 

[ATTACH]270794[/ATTACH]

Many thanks in advance for any help.

---

### Post by shinryu2 on 2016-08-23
Anyone?

---

### Post by shinryu2 on 2016-08-24
So it seems this is indeed an issue with the hardware and erratic behaviour is the best you can get.
I found an old Netgear WN111v2 and it worked as soon as I plugged it in. I also had an even older D-Link DWL-G132 which also worked.

---

