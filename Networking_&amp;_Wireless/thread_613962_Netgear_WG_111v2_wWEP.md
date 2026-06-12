---
title: "Netgear WG 111v2 w/WEP"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by kirmie on 2007-11-15
Ok, I have installed Ubuntu 7.10 but I have not been able to get my Netgear WG 111v2 to work with 128-bit WEP.  I have used multiple inf files with ndiswrapper (1.49) including Realtek's (tried every OS in there) which was something like netrtuf.inf (at school right now) and the net111v2.inf that I use in Windows XP.  When I use ndiswrapper -l I get a message that essentially says Driver Installed, Device {ID} Present ( alternate driver rtl8187).  I have the line blacklist rtl8187 in /etc/modprobe.d/blacklist and I have tried turning off Network Manager and still no results.  With ndiswrapper I do not even get wlan0 as a device, though the rtl8187 driver would allow me to configure wlan0 while not connecting to my WEP router.  I have used ndiswrapper -m, and modprobe ndiswrapper, removed rtl8187 from /proc/modules, and I have had multiple restarts to see if I needed to reboot to get this to work.  I have read that Realtek's WIN98 inf should work but it doesn't seem to even bring up my device.  Any ideas?  Thanks in advance for any help.

PS: I will be at school for the next 8 hours so I won't really be able to respond again till then.  Though I may be able to check between a few classes.

---

