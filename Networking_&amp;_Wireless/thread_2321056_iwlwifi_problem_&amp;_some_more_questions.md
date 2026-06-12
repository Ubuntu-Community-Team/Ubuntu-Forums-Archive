---
title: "iwlwifi problem &amp; some more questions"
date: 2016-04-20
forum: Networking &amp; Wireless
---

### Post by manmath_sahu on 2016-04-20
**Problems**:

I've just installed ubuntu 16.04 and updated fully. I'm facing 2 issues:

#1 Booting takes long with a big pause with error message: 

[    8.698707] iwlwifi 0000:09:00.0: Unsupported splx structure
[    8.813606] iwlwifi 0000:09:00.0: Direct firmware load for iwlwifi-3160-17.ucode failed with error -2

 It's a lenovo laptop with built-in Intel(R) Dual Band Wireless AC 3160 card

There after it takes long at resolvconf, "systemd-analyze blame: shows

30.085s systemd-networkd-resolvconf-update.service

#2 Shutdown also takes long with a big pause at:

systemd-networkd-wait-online.service

#3 It's a broadwell pentium dual core, and sometimes the screen flickers.

---

### Post by Bucky Ball on 2016-04-20
*Thread moved to **Networking & Wireless**.*

Do you get online when you eventually get to a desktop or the card doesn't work at all? When you're at a desktop, open a terminal and paste this in:

```
sudo lshw -C network
```

Hit enter. Post back the output between code tags (green link in my signature at bottom of my post).

---

### Post by chili555 on 2016-04-20
> [ 8.813606] iwlwifi 0000:09:00.0: Direct firmware load for iwlwifi-3160-17.ucode failed with error -2
That could be entirely normal. Generally, the driver looks for the newest firmware and, failing that, looks for the next newest, -16 in your case, and then proceeds. In fact, I am not sure that -17 even exists yet.

In order to see if there is really a problem, we need to see more. Please run and post:```
dmesg | grep iwl
```> #2 Shutdown also takes long with a big pause at:

systemd-networkd-wait-online.service

#3 It's a broadwell pentium dual core, and sometimes the screen flickers. I suggest you ask those questions here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by manmath_sahu on 2016-04-21
> **Bucky Ball said:**
> *Thread moved to **Networking & Wireless**.*

Do you get online when you eventually get to a desktop or the card doesn't work at all? When you're at a desktop, open a terminal and paste this in:

```
sudo lshw -C network
```

Hit enter. Post back the output between code tags (green link in my signature at bottom of my post).

This is what I get:

```
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: enp8s0
       version: 10
       serial: f0:76:1c:db:a4:70
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=172.16.2.211 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:49 ioport:3000(size=256) memory:c3104000-c3104fff memory:c3100000-c3103fff
  *-network
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlp9s0
       version: 93
       serial: e4:f8:9c:41:92:90
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-21-generic firmware=16.242414.0 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:54 memory:c3000000-c3001fff
```

> **chili555 said:**
> That could be entirely normal. Generally, the driver looks for the newest firmware and, failing that, looks for the next newest, -16 in your case, and then proceeds. In fact, I am not sure that -17 even exists yet.

In order to see if there is really a problem, we need to see more. Please run and post:```
dmesg | grep iwl
```I suggest you ask those questions here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

That's right. -17 update is not there. And it's definitely not a big problem, but it pauses the booting for some long. Anyways, dmesg | grep iwl throws:

```
[    9.425985] iwlwifi 0000:09:00.0: Unsupported splx structure
[    9.519289] iwlwifi 0000:09:00.0: Direct firmware load for iwlwifi-3160-17.ucode failed with error -2
[    9.748219] iwlwifi 0000:09:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[   10.282822] iwlwifi 0000:09:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[   10.283160] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled
[   10.283670] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled
[   10.425212] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   10.426657] iwlwifi 0000:09:00.0 wlp9s0: renamed from wlan0
[   20.441021] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled
[   20.441531] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled
[   20.550682] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled
[   20.551298] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled
```

Strange solution to 1st problem. Out of curiosity I just copied [COLOR=#000000][FONT=Ubuntu Mono]iwlwifi-3160-16.ucode and renamed it [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]iwlwifi-3160-17.ucode. After that booting is almost normal, takes around 30 sec (previously it was almost 1 minute, with some 30 sec pause for searching firmware).

The 2nd problem still persists. It's regarding slow shutdown. The third problem regarding screen flickering is not that frequent now after the latest updates.


[/FONT][/COLOR]

---

### Post by chili555 on 2016-04-21
> Strange solution to 1st problem. Out of curiosity I just copied iwlwifi-3160-16.ucode and renamed it iwlwifi-3160-17.ucode. After that booting is almost normal, takes around 30 sec I doubt that is the problem and I doubt that is the solution. Look at the timestamp:> [    9.425985] iwlwifi 0000:09:00.0: Unsupported splx structure
[    [COLOR="#FF0000"]9.519289[/COLOR]] iwlwifi 0000:09:00.0: Direct firmware load for iwlwifi-3160-17.ucode failed with error -2
[    [COLOR="#FF0000"]9.748219[/COLOR]] iwlwifi 0000:09:00.0: loaded firmware version 16.242414.0 op_mode iwlmvmSo it took 0.23 seconds, during which other things were going on, being started, etc., for the driver to look for and not find -17 but then find and use -16. That's not 30 seconds or one minute or even suspicious.

There is something deeper going on here. I suggest that you do:```
dmesg | less
```Use the arrow keys to scroll back and forth and find the big discontinuity in the log. By discontinuity, I mean an entry that has a big gap in time between two entries. It may in fact be the entry a couple of lines earlier. If in doubt, post your entire *dmesg* here and we'll look at it with you: [http://paste.ubuntu.com](http://paste.ubuntu.com)

Get out of less with q.

---

### Post by manmath_sahu on 2016-04-21
My system admin at office reinstalled some packages, I could peek a few related to systemd, network and so like. Now, booting is almost instantaneous. systemd-analyze result is:

```

sqyuser@SqyUser:~$ systemd-analyze
Startup finished in 2.426s (kernel) + 15.197s (userspace) = 17.623s

```

Shutdown also takes a few flip seconds. Means most of the problem solved except for screen flickering. Please suggest what should I do now, this problem is an occasional show-stopper.

Please take a look at the attached dmesg output.

---

### Post by chili555 on 2016-04-21
> Means most of the problem solved except for screen flickering. Please suggest what should I do now, this problem is an occasional show-stopper.

Please take a look at the attached dmesg output. I suggest you start a new thread here as screen flicker is no doubt not a networking and wireless issue.

[http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

I'm glad the wireless is working as expected.

---

### Post by kurogami555 on 2016-11-19
i am having the same problem of unspported splx structure how can i solve it ???

---

### Post by chili555 on 2016-11-19
> **kurogami555 said:**
> i am having the same problem of unspported splx structure how can i solve it ???If you mean that you have the message in the logs, it may or may not be significant. If you are having some difficulty with your connection, please tell us in detail what it is.

---

### Post by Bucky Ball on 2016-11-19
Probably better to post a new thread with a description of your issue and the details chili555 has asked for than to wake this old thread. Post a link to it here if you like. This thread has been dead for six months. ;)

---

