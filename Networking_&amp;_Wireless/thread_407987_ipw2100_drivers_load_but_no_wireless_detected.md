---
title: "ipw2100 drivers load but no wireless detected"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by SadaraX on 2007-04-12
I am using Kubnuntu/Ubuntu 6.10, Kernel 2.6.17-11-generic. I am having wireless network card troubles. Before in Kcontrol I used to see my wireless card in the network devices area. But it was not working. So...

I installed IPW2100 drivers from [http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/). I installed 

the drivers ipw2100-1.2.0.tgz
the firmware v1.3
and ieee80211 version 1.2.17.

I compiled and installed them successfully, and then used their scripts to load the modules into the kernel. The loading looks like this:

> 
user@computer1[ipw2100-1.2.0]$ . load
Unloaded: ipw2100 ieee80211 ieee80211_crypt
Loaded: ieee80211_crypt ieee80211_crypt_wep ieee80211_crypt_tkip ieee80211_crypt_ccmp ieee80211 ipw2100


Dmesg reports:
> 
[17181216.424000] ieee80211_crypt: unregistered algorithm 'NULL'
[17181216.484000] ieee80211_crypt: registered algorithm 'NULL'
[17181216.488000] ieee80211_crypt: registered algorithm 'WEP'
[17181216.496000] ieee80211_crypt: registered algorithm 'TKIP'
[17181216.500000] ieee80211_crypt: registered algorithm 'CCMP'
[17181216.508000] ieee80211: 802.11 data/management/control stack, 1.2.17
[17181216.508000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17181216.512000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.2.0
[17181216.512000] ipw2100: Copyright(c) 2003-2006 Intel Corporation


However, now the wireless card in my system is gone from Kcontrol's network device list. The 'iwconfig' command says that I do not have a wireless card. I am baffled about what to do, because everything looked like it loaded compiled and loaded successfully, however I cannot do any of the iwconfig/iwlist command. Help please?

---

### Post by and_mar on 2007-08-22
I am experiencing the same problem with linux kernel 2.6.22 (debian patched) and ipw2100-1.2.2

Aparently the modules are loaded:

%> dmesg|tail -5
ieee80211_crypt: registered algorithm 'WEP'
ieee80211_crypt: registered algorithm 'TKIP'
ieee80211_crypt: registered algorithm 'CCMP'
ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.2.2
ipw2100: Copyright(c) 2003-2006 Intel Corporation

But iwconfig does not detect any suitable device:

%> iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

But I have the hardware:
%> lspci |grep -i net
0000:01:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05) 

Any help or hint?

---

### Post by and_mar on 2007-08-22
OOPS! I realised I was installing the ipw2100 instead of the ipw2200...

I have installed ipw2200 and the device gets recognised by now, though I have some problems since it complains about the firmware (ipw2200-bss.fw request firmware failed: Reason -2)
I will check again...

---

### Post by and_mar on 2007-08-23
I installed the new version of udev (0.114-2) and everything is working fine now.

---

