---
title: "Intel Wireless 7260 very unstable"
date: 2016-07-31
forum: Networking &amp; Wireless
---

### Post by afonso2 on 2016-07-31
I have had an unstable wi-fi for a long now, but just found out it's the Intel Wireless 7260 card causing this.

What I mean is that the wi-fi will drop randomly, and only rebooting fixes it (temporarily until it drops again).

I tried plugging an external wi-fi card and it worked perfectly.

How can I fix this issue with my laptop's wifi card?

```
afonso@afonso-ubuntu:~$ lspci | grep -i wireless
03:00.0 Network controller: Intel Corporation Wireless 7260 (rev 6b)

```
```
afonso@afonso-ubuntu:~$ dmesg | grep iwl | grep firmware
[   10.013116] iwlwifi 0000:03:00.0: loaded firmware version 25.17.12.0 op_mode iwlmvm
[ 2454.141227] iwlwifi 0000:03:00.0: loaded firmware version 25.17.12.0 op_mode iwlmvm
[ 2460.110637] iwlwifi 0000:03:00.0: Failed to load firmware chunk!

```

```
afonso@afonso-ubuntu:~$ lsmod | grep iw
iwlmvm                278528  0 
iwlwifi               196608  1 iwlmvm
mac80211              724992  2 rtl8187,iwlmvm
cfg80211              540672  4 iwlwifi,mac80211,rtl8187,iwlmvm

```

```
afonso@afonso-ubuntu:~$ uname -a
Linux afonso-ubuntu 3.19.0-26-generic #28-Ubuntu SMP Tue Aug 11 14:16:32 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```





I appreciate any help you guys can give me!
Thanks a lot!

---

### Post by Keith_Helms on 2016-07-31
I had the same problems with Xubuntu 16.04 and the 7260 adapter while on vacation earlier in the month.  Network traffic would sometimes just halt.  I didn't have to reboot - clicking on the network again in the network manager applet would reestablish the connection and start it working again.  The odd thing is I never had problems for the month before that when I was at home and after installing 16.04.  The problem seems to somehow be router specific or at least more common on certain networks.  I also never had problems while on Xubuntu 14.04.

I recently downloaded the iwlwifi-7260-17.ucode firmware and I haven't seen the problem again.  Today I'm using the hotspot on my android tablet instead of my home router, since the tablet hotspot was one network that gave me problems when I was out of town.  So far, it's working with no problems.

If you're on the 3.19 kernel, I assume you're running 14.04.n or 14.10, so an older driver may not recognize or use the -17 firmware I mentioned.

A couple of things that are usually mentioned are to make sure the regulatory domain is set and to disable power management for the wifi adapter.

To set the regulatory domain, edit /etc/default/crda and add the correct country code to REGDOMAIN=

To disable power management, substitute the correct name for your wifi adapter into the following command.
```
sudo iwconfig wlan0 power off

```

If setting power management off helps, there are multiple ways to set that command to be executed at started.  I ended up creating a system crontab entry that executed a script containing the command.  
```
#!/bin/bash

sleep 20
/sbin/iwconfig wlp3s0 power off
```

---

