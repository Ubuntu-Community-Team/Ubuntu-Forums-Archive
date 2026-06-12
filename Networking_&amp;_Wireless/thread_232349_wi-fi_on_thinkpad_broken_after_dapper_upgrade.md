---
title: "wi-fi on thinkpad broken after dapper upgrade"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by jonahsilas on 2006-08-08
Hi there-

I had a working Breezy install on my Thinkpad T41 for the last six months or so. I upgraded to Dapper via the update manager, and after fixing some gnome-session problems, I am left with a functional laptop with no wireless.

I have disabled NetworkManager and nm-applet as I cannot even connect from the command line. The hardware is good as I can connect from my WinXP parallel install. iwlist scanning sees my wireless ap.

All the expected modules appear to be loading. I see ipw2100, ieee80211_crypt ieee80211,ieee80211_crypt_wep in lsmod.

ifconfig eth1:
eth1      Link encap:Ethernet  HWaddr 00:0C:F1:17:02:44
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x8000 Memory:c0214000-c0214fff

I issue
sudo iwconfig eth1 essid upabovetheworld key mykey 
and end up with
eth1      unassociated  ESSID:"upabovetheworld"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power:16 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Concurrent to that this is what appears in dmesg:

[B]ieee80211: 802.11 data/management/control stack, 1.1.14
[17181233.416000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17181233.424000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.2.0
[17181233.424000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[17181233.424000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17181233.424000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[17181417.144000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17181442.516000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17181537.052000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17181640.984000] ADDRCONF(NETDEV_UP): eth1: link is not ready

I also get an occasional
[17182024.092000] ipw2100: Fatal interrupt. Scheduling firmware restart.

I have tried reinstalling the drivers, the firmware, udev (and all of its dependencies - ubuntu base, etc.). I haven't rebuilt my kernel as I was unsure of whether I should try to enable or disable ipw2100 modules.

Any thoughts or suggestions?

Thanks in advance!

Jonah

---

### Post by zwz on 2006-08-23
I am seeing this problem on ThinkPad X32 as well. The wireless adapter is:

0000:02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)


Here are the relevant kernel bootup messages:
[17179587.976000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
[17179587.976000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
[17179587.976000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179587.988000] ieee80211_crypt: registered algorithm 'NULL'
[17179587.988000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17179587.988000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179588.012000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[17179588.012000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179588.012000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!


The wireless LED, which is below the LCD, does not light up after driver gets loaded.

Trying to bring up the wireless interface:
[17179653.004000] ieee80211_crypt: registered algorithm 'WEP'
[17179653.068000] ADDRCONF(NETDEV_UP): eth1: link is not ready


Pressing the Fn+F5 key to switch off the wireless adaptor:
[17181063.588000] eth1: Going into suspend...
[17181063.588000] ACPI: PCI interrupt for device 0000:02:02.0 disabled

Switching it back on:
[17181074.360000] eth1: Coming out of suspend...
[17181074.376000] PCI: Enabling device 0000:02:02.0 (0000 -> 0002)
[17181074.376000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11


The wireless LED still does not light up.


Trying to bring down the interface and bring it up again:
[17181664.360000] ADDRCONF(NETDEV_UP): eth1: link is not ready


Everything used to work well before upgrading to dapper. :(

---

### Post by zwz on 2006-08-23
This bug report [https://launchpad.net/distros/ubuntu/+source/netcfg/+bug/20247]("https://launchpad.net/distros/ubuntu/+source/netcfg/+bug/20247") provides a workaround:

$ sudo iwconfig key restricted your_wep_key_here

It works for me.

But why doesn't the wifi device automatically set the security mode to restricted in dapper when a WEP key is given?? It used to work in breezy.

---

### Post by zwz on 2006-08-23
Well, the better solution to implement the workaround is to edit /etc/network/interfaces, and insert "restricted" between "wireless-key" and your WEP key.

```

$ sudo vi /etc/network/interfaces

------
iface eth1 inet dhcp
wireless-essid <ESSID>
wireless-key restricted <your_wep_key_here>
-------

```

---

### Post by jonahsilas on 2006-08-24
Just to confirm - the iwconfig key restricted my_key_here workaround works for me. Thank goodness - I thought I would forever more be WEP-free...

Now is there a way to make NetworkManager/nm-applet use the restricted mode? Moreover, NetworkManager uses wpa_supplicant on the backend in 6.06 - is there an equivalent workaround for wpa_supplicant? 

I can (apparently) connect succesfully with wpa_supplicant at the command line, although there appears to be some routing/dhcp problem. But wpa_suppplicant at least reports success, unlike when it is called from NetworkManager.

I will do some more exploring and post my results.

JSS

---

