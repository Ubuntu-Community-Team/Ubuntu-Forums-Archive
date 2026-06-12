---
title: "WiFi issue with Ubuntu 11.04: WiFi stops working"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by Jary316 on 2011-08-13
Hello,

I have a technical problem with my WiFi on Ubuntu 11.04. I did a clean install using the live CD on my Asus N61J laptop.

My problem is that WiFi works most all the time, BUT when I am doing heavy downloads (ie: getting the Android SDK or some packages), the WiFi will stop working in a matter of minutes. That is, the transfer just stops, I cannot load any new web page, it's like if the WiFi is dead, but I am STILL connected and no error gets reported. If I click on my WiFi it will disconnect and reconnect, and the transfer will go on. The same thing will happen when viewing a live streaming video from Youtube for example.

My router is not far at all from my laptop, and the signal strength is maximum. When I run Windows 7, I don't have this problem.

If I do not use any bandwidth angry application, then the WiFi will keep working for hours without any problem.

I have been looking around but all the WiFi questions I found were about WiFi not working at all. I will try switching to an Ethernet cable and seeing if it is the WiFi itself or not, but I'd be happy to try any idea.

These are the informations on my graphic card (running lspci | grep Wireless):

```

03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

Thank you very much.

EDIT: Tested Ethernet (deactivated WiFi) and it has not disconnected me so far. It seems to only be WiFi.

---

### Post by robgraves on 2011-08-13
i have had the exact same problem but have yet to resolve this, i'm 5 feet from my wireless router using a laptop, the suggestion i was given was to try to install backported drivers, which i did, but still did not resolve the issue

---

### Post by varunendra on 2011-08-14
I can't promise a solution, but anyone who can may need outputs of the following:

When the wireless is working-
```
ifconfig -a
```
```
iwconfig
```
```
sudo lshw -C network
```
```
lsmod | grep ath
```


and when the wireless stops working-
```
dmesg | grep -iE "ath|wlan|net"
```
(plus above outputs if any of them shows a difference)

---

### Post by Jary316 on 2011-08-14
Thanks a lot varunendra!

I will provide the logs below:

(The ethernet cable was unplugged during those tests)

**While the WiFi still works:**

ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 48:5b:39:6c:d5:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:62 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:d0:ad:77  
          inet addr:192.168.0.112  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1e4b:d6ff:fed0:ad77/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:770351 (770.3 KB)  TX bytes:157477 (157.4 KB)

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"JaryNetwork"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:23:69:EB:9A:5C   
          Bit Rate=65 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:29   Missed beacon:0

```

sudo lshw -C network
```

  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 1c:4b:d6:d0:ad:77
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-10-generic firmware=N/A ip=192.168.0.112 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d3e00000-d3e0ffff
  *-network
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c0
       serial: 48:5b:39:6c:d5:a7
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:62 memory:d0200000-d023ffff ioport:8000(size=128)

```

lsmod | grep ath
```

ath9k                 118238  0 
mac80211              294370  1 ath9k
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
cfg80211              178528  3 ath9k,mac80211,ath

```

**After the WiFi crashed**

dmesg | grep -iE "ath|wlan|net"
```

[    0.001664] Initializing cgroup subsys net_cls
[    1.513006] NET: Registered protocol family 16
[    2.073092] NetLabel: Initializing
[    2.073094] NetLabel:  domain hash size = 128
[    2.073095] NetLabel:  protocols = UNLABELED CIPSOv4
[    2.073108] NetLabel:  unlabeled traffic allowed by default
[    2.184499] NET: Registered protocol family 2
[    2.189986] NET: Registered protocol family 1
[    2.527203] audit: initializing netlink socket (disabled)
[    2.870056] device-mapper: multipath: version 1.2.0 loaded
[    2.870059] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.871158] NET: Registered protocol family 10
[    2.871724] NET: Registered protocol family 17
[   15.036801] type=1400 audit(1313306536.666:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=449 comm="apparmor_parser"
[   15.137195] NET: Registered protocol family 31
[   15.206693] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.206712] ath9k 0000:03:00.0: setting latency timer to 64
[   15.260532] ath: EEPROM regdomain: 0x60
[   15.260534] ath: EEPROM indicates we should expect a direct regpair map
[   15.260538] ath: Country alpha2 being used: 00
[   15.260539] ath: Regpair used: 0x60
[   15.267662] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   15.268250] Registered led device: ath9k-phy0::radio
[   15.268279] Registered led device: ath9k-phy0::assoc
[   15.268301] Registered led device: ath9k-phy0::tx
[   15.268330] Registered led device: ath9k-phy0::rx
[   15.268337] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90011240000, irq=17
[   15.602952] type=1400 audit(1313306537.226:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=809 comm="apparmor_parser"
[   15.679387] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.854336] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.011140] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.142809] wlan0: authenticate with 00:23:69:eb:9a:5c (try 1)
[   27.146891] wlan0: authenticated
[   27.163715] wlan0: associate with 00:23:69:eb:9a:5c (try 1)
[   27.167793] wlan0: RX AssocResp from 00:23:69:eb:9a:5c (capab=0x411 status=0 aid=3)
[   27.167800] wlan0: associated
[   27.174942] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   37.892822] wlan0: no IPv6 routers present

```

Finally: I re-run the previous command and did a diff with the files listed above (The output of stdout and stder was saved to a file). I only show the diff when 2 commands give different results.

diff of ifconfig -a
```

<           RX packets:24 errors:0 dropped:0 overruns:0 frame:0
<           TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
---
>           RX packets:160 errors:0 dropped:0 overruns:0 frame:0
>           TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
16c16
<           RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)
---
>           RX bytes:14574 (14.5 KB)  TX bytes:14574 (14.5 KB)
22,23c22,23
<           RX packets:1115 errors:0 dropped:0 overruns:0 frame:0
<           TX packets:1178 errors:0 dropped:0 overruns:0 carrier:0
---
>           RX packets:116668 errors:0 dropped:0 overruns:0 frame:0
>           TX packets:68958 errors:0 dropped:0 overruns:0 carrier:0
25c25
<           RX bytes:770351 (770.3 KB)  TX bytes:157477 (157.4 KB)
---
>           RX bytes:169731649 (169.7 MB)  TX bytes:6877766 (6.8 MB)

```

diff of iwconfig
```

           Tx excessive retries:0  Invalid misc:29   Missed beacon:0
---
>           Tx excessive retries:0  Invalid misc:35   Missed beacon:0

```

I hope this is useful.

Thank you very much.

---

### Post by varunendra on 2011-08-14
All of the above seems normal to me. The differences are obvious too. However, it may be an old bug with the ath9k driver itself as reported here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/660864](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/660864)

Some possible fixes:

[http://blog.homelinux.org/?p=327](http://blog.homelinux.org/?p=327)

[http://linuxwireless.org/en/users/Drivers/ath9k/bugs#Loss_of_connectivity_after_large_file_transfer_on_2.6.28](http://linuxwireless.org/en/users/Drivers/ath9k/bugs#Loss_of_connectivity_after_large_file_transfer_on_2.6.28) (it says it was already fixed in kernel 2.6.28.1)

[http://ubuntuforums.org/showthread.php?t=874097&page=19](http://ubuntuforums.org/showthread.php?t=874097&page=19) (post#190 says try wicd, although doubt the poster might have had a different /problemreason than yours)

[http://opennomad.com/content/ubuntu-1104-natty-narwhal-and-ath9k-wireless-drops-or-slowness](http://opennomad.com/content/ubuntu-1104-natty-narwhal-and-ath9k-wireless-drops-or-slowness)


Apart from these, regardless of whether or not it is related, I'd suggest you to disable IPv6 by following one of these:
[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)
or
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)


It'd be really interesting to see if any of these can fix the issue for you. If not, please confirm the kernel version you are using
```
uname -rm
```

Also, you should confirm the bug on the bug-report page I gave you link of. This ensures attention of developers to the issue.

---

### Post by Jary316 on 2011-08-14
Hi varunendra,

Thanks a lot for your help.

uname -rm
```

2.6.38-10-generic x86_64

```

Thanks a lot for all those pages suggestions!

I will try this solution. It will take me time to go through them as I have setting some live streaming.

I've realized that ([http://opennomad.com/content/ubuntu-1104-natty-narwhal-and-ath9k-wireless-drops-or-slowness](http://opennomad.com/content/ubuntu-1104-natty-narwhal-and-ath9k-wireless-drops-or-slowness)) mentions that the fix was in kernel 2.6.39. My kernel seems to be 2.6.38. I've ran the two commands but I am still in 2.6.38. Could it be because I use the 64 bits kernel and the 32 bits and 64 bits don't get released at the same time? (I would think they do).

I have also just tried the solution ([http://blog.homelinux.org/?p=327](http://blog.homelinux.org/?p=327)) and it may have fixed my problem. I have to test a little more to be sure, so I'll update soon.

Thanks for your help.

---

### Post by Jary316 on 2011-08-14
It actually does seem pretty stable right now, I have been streaming a few videos and it did not hang up.

The solution that fixed it was: [http://blog.homelinux.org/?p=327](http://blog.homelinux.org/?p=327)

I assume that that is not the proper solution though. It seems that the update kernel, 2.6.39 may be the proper fix but until my kernel gets updated, this patch sounds good.

varunendra, should I still report on the bug post? It may well be that this issue has already been fixed, I just don't have the updated kernel. What do you think please?

I will mark this post as SOLVED unless the problem reappears, but I think it is gone.

Thanks for your help.

---

### Post by varunendra on 2011-08-14
> **Jary316 said:**
> 
varunendra, should I still report on the bug post? It may well be that this issue has already been fixed, I just don't have the updated kernel. What do you think please?
I'd like to watch its stability too, as it's side effects (if any) and stability were not confirmed.

As for the bug-report, the page shows the status as 'incomplete' and 'assigned to' => 'unassigned'. So I think it is worth confirming that it still exists and needs to be fixed. I'm not sure about this but I think once a bug gets fixed in a later kernel, the bug report page should display its status as 'fix released'. So if a kernel update fixes the problem without the workaround you tried, you should confirm that too on the same bug report page. It is a valuable contribution to the community.

---

### Post by Jary316 on 2011-08-14
Thanks varunendra. I just posted a comment explaining my hardware, my problem and my current fix.

Everything seems to work fine so far. My connection speed on speedtest is as usual, everything seems smooth (so far).

Any idea why my kernel is 2.6.38 and not 2.6.39 please? Has 2.6.39 officially been released or is it because I use a 64 bit version please?

Thank you again.

---

### Post by varunendra on 2011-08-14
You're welcome! Hope it proves to be permanently stable :)

> **Jary316 said:**
> Any idea why my kernel is 2.6.38 and not 2.6.39 please? Has 2.6.39 officially been released or is it because I use a 64 bit version please?

It seems to have been removed from the ppa: [http://www.ubuntuupdates.org/ppas/37](http://www.ubuntuupdates.org/ppas/37)

You may try to download and install it manually from the alternative source:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/)

To install any .deb package, you simply have to double-click it.

But if the current setup is satisfactory, I'd suggest to just stick with it since a newer kernel, although expectedly better than older ones, sometimes creates new problems due to new bugs in it.

But then again, going back to an older kernel is just a matter of selecting it at the boot time in the grub menu :)

---

### Post by Jary316 on 2011-08-14
Ha interesting! Nice job at finding that out varunendra.

Thanks a lot for your help again, you helped me a lot! Thank you.

---

### Post by Jary316 on 2011-08-16
Update: Although it seemed that the solution fixed my problem, I noticed the problem has been reappearing. They are some improvements with the solution, but the problem is not completely gone.

---

