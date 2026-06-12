---
title: "IPW2200+intrepid wouldn't connect"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by pagin on 2008-11-05
Hello all,

I just upgraded to intrepid and so I am using the intrepid -generic kernel instead of my previous, self-compiled one (2.26.4.3).
I had a wireless network configured and working, but with the new kernel I cannot connect. Network-manager clearly shows me all the networks around (so the interface should be up and running), but I always get connection timeouts when I try to connect to mine.
I already tried to install a fresh firmware from ipw2200.sf.net, but that would break completely my network installation (the device wouldn't configure). When I run my old kernel, networking works (but I had a very hard time compiling the new fglrx driver, so it's network without graphics with one kernel, graphics without network with the other. I already broke both kernels trying to manage the one or the other problem, but I just broke everything and had to reinstall a fresh linux-image packgeset in order to get fglrx back running...

Here are some details:
```
pagin@magellan:~$ uname -a
Linux magellan 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i686 GNU/Linux
pagin@magellan:~$ lspci | grep Wireless
01:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
pagin@magellan:~$ lsmod
ieee80211_crypt_tkip    17024  0 
ieee80211_crypt_ccmp    13568  0 
ieee80211_crypt        13572  2 ieee80211_crypt_tkip,ieee80211_crypt_ccmp
lbm_cw_ieee80211       38728  1 ipw2200
lbm_cw_ieee80211_crypt    13828  1 lbm_cw_ieee80211
ipw2200               150216  0 
```

My package versions are:
[LIST]
[*]linux-image-2.6.27-7-generic (2.6.27-7.15)
[*]linux-backports-modules-2.6.27-7-generic (2.6.27-7.4)
[*]linux-firmware (1.2)
[*]linux-restricted-modules-2.6.7.-7-generic (2.6.27-7.12)
[*]wireless-tools (29-1ubuntu2)
[*]wpasupplicant (0.6.4-2)
[*]network-manager (0.7~~svn20081018t105859-0ubuntu1)
[*]network-manager-gnome (0.7~~svn20081020t000444-0ubuntu1)
[/LIST]

Here's the relevant messages from syslog.log
```
Nov  5 15:37:28 magellan kernel: [   25.544284] ieee80211_crypt: registered algorithm 'NULL'
Nov  5 15:37:28 magellan kernel: [   25.551777] ieee80211: 802.11 data/management/control stack, git-1.1.13
Nov  5 15:37:28 magellan kernel: [   25.551829] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Nov  5 15:37:28 magellan kernel: [   25.588480] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Nov  5 15:37:28 magellan kernel: [   25.588541] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Nov  5 15:37:28 magellan kernel: [   25.618845] ipw2200 0000:01:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Nov  5 15:37:28 magellan kernel: [   25.619374] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Nov  5 15:37:28 magellan kernel: [   25.619465] firmware: requesting ipw2200-bss.fw
Nov  5 15:37:28 magellan kernel: [   29.477586] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
Nov  5 15:37:35 magellan NetworkManager: <info>  starting... 
Nov  5 15:37:35 magellan NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/ipw_wlan_switch 
Nov  5 15:37:35 magellan NetworkManager: <info>  eth0: driver is 'r8169'. 
Nov  5 15:37:35 magellan NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Nov  5 15:37:35 magellan NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_03_0d_36_28_ad 
Nov  5 15:37:35 magellan NetworkManager: <info>  eth1: driver is 'ipw2200'. 
Nov  5 15:37:35 magellan NetworkManager: <info>  eth1: driver supports SSID scans (scan_capa 0x21). 
Nov  5 15:37:35 magellan NetworkManager: <info>  Found new 802.11 WiFi device 'eth1'. 
Nov  5 15:37:35 magellan NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_13_ce_61_3e_61 
Nov  5 15:37:35 magellan NetworkManager: <info>  Trying to start the supplicant... 
Nov  5 15:37:35 magellan NetworkManager: <info>  Trying to start the system settings daemon... 
Nov  5 15:37:35 magellan nm-system-settings:    SCPlugin-Ifupdown: init!
Nov  5 15:37:35 magellan nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Nov  5 15:37:35 magellan nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Nov  5 15:37:35 magellan nm-system-settings:    SCPlugin-Ifupdown: devices added (udi: /org/freedesktop/Hal/devices/net_00_03_0d_36_28_ad, iface: eth0)
Nov  5 15:37:35 magellan nm-system-settings:    SCPlugin-Ifupdown: devices added (udi: /org/freedesktop/Hal/devices/net_00_13_ce_61_3e_61, iface: eth1)
Nov  5 15:37:35 magellan nm-system-settings:    SCPlugin-Ifupdown: end _init.
Nov  5 15:37:35 magellan nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Nov  5 15:37:35 magellan nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov  5 15:37:35 magellan nm-system-settings:    SCPlugin-Ifupdown: (152510704) ... get_connections.
Nov  5 15:37:35 magellan nm-system-settings:    SCPlugin-Ifupdown: (152510704) connections count: 0
Nov  5 15:37:35 magellan NetworkManager: <info>  (eth1): supplicant manager is now in state 1 (from 0). 
Nov  5 15:37:35 magellan nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Nov  5 15:37:39 magellan NetworkManager: <info>  (eth1): device state change: 1 -> 2 
Nov  5 15:37:39 magellan NetworkManager: <info>  (eth1): bringing up device. 
Nov  5 15:37:39 magellan NetworkManager: <info>  (eth1): preparing device. 
Nov  5 15:37:39 magellan NetworkManager: <info>  (eth1): deactivating device (reason: 2).Nov  5 15:37:39 magellan NetworkManager: <info>  (eth1): device state change: 2 -> 3 
Nov  5 15:37:39 magellan kernel: [   46.987684] NET: Registered protocol family 17
Nov  5 15:37:39 magellan NetworkManager: <info>  (eth1): supplicant interface state change: 1 -> 2. 
Nov  5 15:37:39 magellan NetworkManager: <info>  (eth1): device state change: 2 -> 3 
Nov  5 15:37:39 magellan kernel: [   46.987684] NET: Registered protocol family 17
Nov  5 15:37:39 magellan NetworkManager: <info>  (eth1): supplicant interface state change: 1 -> 2. 
Nov  5 15:38:31 magellan NetworkManager: <info>  Activation (eth1) starting connection 'Auto Bad Connection' 
Nov  5 15:38:31 magellan NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Nov  5 15:38:31 magellan NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  5 15:38:31 magellan NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  5 15:38:31 magellan NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  5 15:38:31 magellan NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  5 15:38:31 magellan NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  5 15:38:31 magellan NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Nov  5 15:38:31 magellan NetworkManager: <info>  Activation (eth1/wireless): access point 'Auto Bad Connection' has security, but secrets are required. 
Nov  5 15:38:31 magellan NetworkManager: <info>  (eth1): device state change: 5 -> 6 
Nov  5 15:38:31 magellan NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  5 15:38:31 magellan NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  5 15:38:31 magellan NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  5 15:38:31 magellan NetworkManager: <info>  (eth1): device state change: 6 -> 4 
Nov  5 15:38:31 magellan NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  5 15:38:31 magellan NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  5 15:38:31 magellan NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  5 15:38:31 magellan NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Nov  5 15:38:31 magellan NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto Bad Connection' has security, and secrets exist.  No new secrets needed. 
Nov  5 15:38:31 magellan NetworkManager: <info>  Config: added 'ssid' value 'Bad Connection' 
Nov  5 15:38:31 magellan NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Nov  5 15:38:31 magellan NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Nov  5 15:38:31 magellan NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Nov  5 15:38:31 magellan NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Nov  5 15:38:31 magellan NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Nov  5 15:38:31 magellan NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Nov  5 15:38:31 magellan NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  5 15:38:31 magellan NetworkManager: <info>  Config: set interface ap_scan to 1
Nov  5 15:38:31 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 0 
Nov  5 15:38:31 magellan anacron[6164]: Anacron 2.3 started on 2008-11-05
Nov  5 15:38:31 magellan anacron[6164]: Normal exit (0 jobs run)
Nov  5 15:38:35 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Nov  5 15:38:35 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Nov  5 15:38:35 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Nov  5 15:38:35 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Nov  5 15:38:35 magellan kernel: [  103.141304] ieee80211_crypt: registered algorithm 'NULL'
Nov  5 15:38:35 magellan kernel: [  103.182813] ieee80211_crypt: registered algorithm 'CCMP'
Nov  5 15:38:35 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 6 
Nov  5 15:38:35 magellan kernel: [  103.247945] ieee80211_crypt: registered algorithm 'TKIP'
Nov  5 15:38:45 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 0 
Nov  5 15:38:45 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Nov  5 15:38:45 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 0 
Nov  5 15:38:45 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 3 
Nov  5 15:38:45 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Nov  5 15:38:45 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Nov  5 15:38:46 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 6 
Nov  5 15:38:46 magellan NetworkManager: <info>  eth1: link timed out. 
Nov  5 15:38:55 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 0 
Nov  5 15:38:55 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Nov  5 15:38:55 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 0 
Nov  5 15:38:56 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 3 
Nov  5 15:38:56 magellan NetworkManager: <info>  Activation (eth1/wireless): association took too long. 
Nov  5 15:38:56 magellan NetworkManager: <info>  (eth1): device state change: 5 -> 6 
Nov  5 15:38:56 magellan NetworkManager: <info>  Activation (eth1/wireless): asking for new secrets 
Nov  5 15:38:56 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 0 
Nov  5 15:38:56 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 4 
Nov  5 15:38:56 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 0 
Nov  5 15:39:09 magellan NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Nov  5 15:39:11 magellan NetworkManager: <info>  eth1: link timed out.
Nov  5 15:41:21 magellan NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  5 15:41:21 magellan NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  5 15:41:21 magellan NetworkManager: <info>  (eth1): device state change: 6 -> 4 
Nov  5 15:41:21 magellan NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  5 15:41:21 magellan NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  5 15:41:21 magellan NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  5 15:41:21 magellan NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Nov  5 15:41:21 magellan NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto Bad Connection' has security, and secrets exist.  No new secrets needed. 
Nov  5 15:41:21 magellan NetworkManager: <info>  Config: added 'ssid' value 'Bad Connection' 
Nov  5 15:41:21 magellan NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Nov  5 15:41:21 magellan NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Nov  5 15:41:21 magellan NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Nov  5 15:41:21 magellan NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Nov  5 15:41:21 magellan NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Nov  5 15:41:21 magellan NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 

[etc. / Timeouts]

Nov  5 15:42:12 magellan NetworkManager: <info>  (eth1): device state change: 6 -> 9 
Nov  5 15:42:12 magellan NetworkManager: <info>  Activation (eth1) failed for access point (Bad Connection) 
Nov  5 15:42:12 magellan NetworkManager: <info>  Marking connection 'Auto Bad Connection' invalid.

```

Any idea what could be wrong?
Network-manager gives me only one option for encryption (WPA2), where hardy would give me several ones. May this be a hint (some encryptions deactivated)? But it's the same for both kernels...

---

### Post by raiwo on 2008-11-05
WPA is broken, try without encryption

---

### Post by klausner on 2008-11-05
> **raiwo said:**
> WPA is broken, try without encryption

That (unfortunately) makes some sense. I can't connect to my own network with WEP using 2.6.27-7, but I can connect to my neighbor's unsecured access point. 

I also noticed that my access point shows up twice in the available list, once with encryption, and once without. But I the access point is running only in secured mode, and you can't connect to the phantom unsecured entry (which is also stronger for some reason!)

---

### Post by pagin on 2008-11-06
Logging in without encryption is not an option unfortunately (or fortunately, on the privacy perspective), because it's my neighbor's access point. He won't allow unencrypted connections.

So we agree that this is a bug in the -generic kernel? What would be the workaround? Recompiling my own kernel?

---

### Post by klausner on 2008-11-09
Bump. Does someone have a working solution yet?

---

### Post by borris.morris on 2008-11-10
Mine's working with encryption. I copied firmware into the /lib/fireware directory and it works. However, for some odd reason, I can't suspend/resume now. I'm gonna get a different card soon...... lol

---

### Post by klausner on 2008-11-10
> **borris.morris said:**
> Mine's working with encryption. I copied firmware into the /lib/fireware directory and it works. However, for some odd reason, I can't suspend/resume now. I'm gonna get a different card soon...... lol

Where did you copy the firmware *from*?

---

### Post by neilmusgrove on 2008-11-10
I seem to be having exactly these problems since an upgrade, before this it worked perfectly in 8.10.

---

### Post by klausner on 2008-11-11
OK. In my ongoing efforts to get the darned 2200BG working properly with 8.10, I tried to reinstall the drivers from the Intel site. That left me completely dead as far as wireless networking, and I couldn't seem to undo what I had done.

So I reluctantly decided to do a re-install of Intrepid. Fortunately, /home, /usr/local, and another data partition I use are separately mounted, and I had a current aptoncd image.

To my astonishment, when the install was done, and the reboot finished, wireless AND encryption were working properly! It seems the problem happens when you upgrade from 8.04 to 8.10, but doesn't happen with a clean install!

It's a bit of a drastic solution, but it worked for me.

---

### Post by al_mckin on 2008-11-13
Hi,

I'm glad I found this thread because I thought I was the only one having this problem!

I thought it was related to this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264104]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264104") but the report claims that this is fixed, but it is definitely not fixed for me in fully up to date intrepid.

I cannot connect to any encrypted network with my internal ipw2200 card although I can cannot to an unencrypted one.

Trying to set the wep key with iwconfig leads to this:

```
alastair@alastair-laptop:~$ sudo iwconfig eth1 key CCCC-CCCC-CC
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Operation not supported.
```

However, I can connect to an encrypted network with another card.

Anyone got anything?

---

### Post by klausner on 2008-11-13
It's a Windoze-type, brute-force solution, but you can try re-installing as I detailed above.

---

### Post by pagin on 2008-11-16
I'm still waiting for a "softer" solution, as I did a lot of personalizations on the system. I'll try with the live-CD for a first stance...

---

### Post by alge on 2009-01-02
I got ipw2200 + WEP working again after removing the linux-backports module package:

```

sudo apt-get remove --purge linux-backports-modules-2.6.27-9-generic
```

I have a Hardy install with backported Intrepid kernel, but I guess it will apply to a clean Intrepid the same way. 

Albrecht

---

### Post by The Soundophiliac on 2009-01-06
I didn't have linux-backports-modules installed. Any solutions for me?

---

### Post by taralluccio on 2009-03-27
Alge is right, currently linux-backport-modules will prevent encrypted wireless (WEP or WPA) from working.

See also [this thread]("http://ubuntuforums.org/showthread.php?t=975684").

---

