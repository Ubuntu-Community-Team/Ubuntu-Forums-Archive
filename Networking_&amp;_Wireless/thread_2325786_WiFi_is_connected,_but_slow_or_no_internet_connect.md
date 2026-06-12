---
title: "WiFi is connected, but slow or no internet connection"
date: 2016-05-25
forum: Networking &amp; Wireless
---

### Post by lavande2 on 2016-05-25
I'm on ubuntu 16.04 (actually this begins to happen with version 14.04).
I can successfully connect to the wifi, and the wifi connection is stable (at least it's always showing 'connected' in the panel).
The internet connection is ok in the first few minutes after connecting to the wifi. However, it gradually becomes slow or sometimes there's no connection at all, while the wifi is still connected.
When this happens, I reconnect to the wifi and there are chances the internet connection would be back, but usually it stays offline.

I tried the following workarounds:
1. changed the driver from broadcom STA to b43
2. editted the /etc/nsswitch.conf file (hosts: files dns)
3. ignored ipv6 in the networkmanager
But none of them worked.


Below is the details of my hardware. Can anyone help? Thanks!

```
~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM57765 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0f0
       version: 10
       serial: 3c:07:54:2f:4e:65
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=57765-v1.37 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:a0400000-a040ffff memory:a0410000-a041ffff
  *-network
       description: Network controller
       product: BCM4331 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:a0600000-a0603fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlp3s0b1
       serial: 68:a8:6d:46:a6:12
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=4.4.0-22-generic firmware=666.2 ip=192.168.1.200 link=yes multicast=yes wireless=IEEE 802.11bg
```

---

### Post by praseodym on 2016-05-25
For b43: Did you install the firmware?

```
wget https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz  
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

For STA: Is it the latest one?
```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-2_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-2_all.deb 
```

---

### Post by lavande2 on 2016-05-26
Thanks for your post
The firmware I use is installed by 'firmware-b43-installer' in ubuntu repo.
I also tried broadcom-wl-6.30.163.46.tar.bz2 firmware and installed it with b43-fwcutter, but the problem is still there.
In order to get connected, I used a usb wireless adaptor, but the wifi connection drops every a few minutes.
BTW, I found that my network interfaces have strange names!
Shouldn't them be something like 'wlan0'?

Now with an extra usb wireless adaptor, the output is:
```

~$ ifconfig 
enp2s0f0  Link encap:Ethernet  HWaddr 3c:07:54:2f:4e:65  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:11168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:5512477 (5.5 MB)  TX bytes:5512477 (5.5 MB)

wlp3s0b1  Link encap:Ethernet  HWaddr 68:a8:6d:46:a6:12  
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6aa8:6dff:fe46:a612/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26750 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33052 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19670078 (19.6 MB)  TX bytes:5586928 (5.5 MB)

wlx0c826852a78e Link encap:Ethernet  HWaddr 0c:82:68:52:a7:8e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:822 overruns:0 frame:0
          TX packets:0 errors:0 dropped:1322 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19072077 (19.0 MB)  TX bytes:3531784 (3.5 MB)


~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM57765 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0f0
       version: 10
       serial: 3c:07:54:2f:4e:65
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=57765-v1.37 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:a0400000-a040ffff memory:a0410000-a041ffff
  *-network
       description: Network controller
       product: BCM4331 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:a0600000-a0603fff
  *-network:0
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1.3
       logical name: wlx0c826852a78e
       serial: 0c:82:68:52:a7:8e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8188eu multicast=yes wireless=unassociated
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlp3s0b1
       serial: 68:a8:6d:46:a6:12
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=4.4.0-22-generic firmware=784.2 ip=192.168.1.200 link=yes multicast=yes wireless=IEEE 802.11bg
```

---

### Post by vincenzo-giovinazzo91 on 2016-05-26
same issue here
ubuntu 16.10 and RTL8821AE

---

### Post by simonn on 2016-05-27
> **vincenzo-giovinazzo91 said:**
> same issue here
ubuntu 16.10 and RTL8821AE

See:

[http://ubuntuforums.org/showthread.php?t=2300379&p=13495605#post13495605](http://ubuntuforums.org/showthread.php?t=2300379&p=13495605#post13495605)

---

### Post by praseodym on 2016-05-27
b32-fwcutter may not be suitable here. Try the other one. Check
```

dmesg | egrep 'b43|bcma|wl'
```
Interface names are new since 16.04, no worries.

---

### Post by lavande2 on 2016-06-03
Thanks for the post. The is the output. Any ideas what is wrong here?

```
~$ dmesg |egrep 'b43|bcma|wl' 
[ 4.423399] bcma: bus0: Found chip with id 0x4331, rev 0x02 and package 0x09
 [ 4.423434] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0) [
 4.423462] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1D, class 0x0) 
[ 4.423513] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x13, class 0x0)
 [ 4.476974] bcma: bus0: Bus registered 
[ 4.796569] b43-phy0: Broadcom 4331 WLAN found (core revision 29) 
[ 4.797114] b43-phy0: Found PHY: Analog 9, Type 7 (HT), Revision 1 
[ 4.797127] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2059, Revision 0, Version 1 
[ 4.797129] b43-phy0 warning: 5 GHz band is unsupported on this PHY 
[ 4.858889] b43 bcma0:1 wlp3s0b1: renamed from wlan0 
[ 7.227521] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready
 [ 7.392570] b43-phy0: Loading firmware version 784.2 (2012-08-15 21:35:19) 
[ 7.504712] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready 
[ 8.671429] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready 
[ 21.936642] wlp3s0b1: authenticate with 38:91:d5:5d:85:07 
[ 21.983920] wlp3s0b1: send auth to 38:91:d5:5d:85:07 (try 1/3) 
[ 21.985427] wlp3s0b1: authenticated 
[ 21.987629] wlp3s0b1: associate with 38:91:d5:5d:85:07 (try 1/3)
 [ 21.990098] wlp3s0b1: RX AssocResp from 38:91:d5:5d:85:07 (capab=0x411 status=0 aid=4) 
[ 21.990568] wlp3s0b1: associated
 [ 21.990579] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0b1: link becomes ready 
[ 1158.534537] wlp3s0b1: deauthenticating from 38:91:d5:5d:85:07 by local choice (Reason: 3=DEAUTH_LEAVING) 
[ 1158.595540] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready
 [ 1163.734526] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready
 [ 1163.900737] b43-phy0: Loading firmware version 784.2 (2012-08-15 21:35:19) 
[ 1164.012903] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready
 [ 1165.089084] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready 
[ 1166.349435] wlp3s0b1: authenticate with 30:fc:68:2b:0c:4c
 [ 1166.384943] wlp3s0b1: send auth to 30:fc:68:2b:0c:4c (try 1/3) 
[ 1166.388924] wlp3s0b1: authenticated 
[ 1166.392817] wlp3s0b1: associate with 30:fc:68:2b:0c:4c (try 1/3) 
[ 1166.397435] wlp3s0b1: RX AssocResp from 30:fc:68:2b:0c:4c (capab=0x431 status=0 aid=7) 
[ 1166.397903] wlp3s0b1: associated 
[ 1166.397949] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0b1: link becomes ready 
[ 1376.040988] wlp3s0b1: deauthenticating from 30:fc:68:2b:0c:4c by local choice (Reason: 3=DEAUTH_LEAVING)
 [ 1377.186442] wlp3s0b1: authenticate with 30:fc:68:2b:0c:4c 
[ 1377.225201] wlp3s0b1: send auth to 30:fc:68:2b:0c:4c (try 1/3) 
[ 1377.230269] wlp3s0b1: authenticated 
[ 1377.232962] wlp3s0b1: associate with 30:fc:68:2b:0c:4c (try 1/3)
 [ 1377.237552] wlp3s0b1: RX AssocResp from 30:fc:68:2b:0c:4c (capab=0x431 status=0 aid=7) 
[ 1377.237962] wlp3s0b1: associated 
[ 1400.635140] wlp3s0b1: deauthenticating from 30:fc:68:2b:0c:4c by local choice (Reason: 3=DEAUTH_LEAVING)
 [ 1401.763218] wlp3s0b1: authenticate with 30:fc:68:2b:0c:4c 
[ 1401.818197] wlp3s0b1: send auth to 30:fc:68:2b:0c:4c (try 1/3) 
[ 1401.820203] wlp3s0b1: authenticated 
[ 1401.822087] wlp3s0b1: associate with 30:fc:68:2b:0c:4c (try 1/3) 
[ 1401.826990] wlp3s0b1: RX AssocResp from 30:fc:68:2b:0c:4c (capab=0x431 status=0 aid=7) 
[ 1401.834308] wlp3s0b1: associated 
[ 1451.936413] wlp3s0b1: authenticate with 38:91:d5:5d:85:07 
[ 1451.956459] wlp3s0b1: send auth to 38:91:d5:5d:85:07 (try 1/3) 
[ 1452.160151] wlp3s0b1: send auth to 38:91:d5:5d:85:07 (try 2/3) 
[ 1452.364175] wlp3s0b1: send auth to 38:91:d5:5d:85:07 (try 3/3) 
[ 1452.568190] wlp3s0b1: authentication with 38:91:d5:5d:85:07 timed out 
[ 1452.785567] wlp3s0b1: authenticate with 30:fc:68:2b:0c:4c 
[ 1452.832352] wlp3s0b1: send auth to 30:fc:68:2b:0c:4c (try 1/3) 
[ 1452.836117] wlp3s0b1: authenticated 
[ 1452.840119] wlp3s0b1: associate with 30:fc:68:2b:0c:4c (try 1/3) 
[ 1452.844702] wlp3s0b1: RX AssocResp from 30:fc:68:2b:0c:4c (capab=0x431 status=0 aid=7) 
[ 1452.852224] wlp3s0b1: associated
```

---

### Post by lavande2 on 2016-06-03
Sorry for pasting this without newlines. I'm using the forum on my phone. I'll try another computer which has internet access.

---

### Post by jeremy31 on 2016-06-03
Posts fixed. Please use code tags, see the link in my signature.  In Advanced reply you should be able to click on the # icon and then paste

---

