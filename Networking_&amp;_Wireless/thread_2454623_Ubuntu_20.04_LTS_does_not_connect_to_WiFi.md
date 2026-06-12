---
title: "Ubuntu 20.04 LTS does not connect to WiFi"
date: 2020-12-03
forum: Networking &amp; Wireless
---

### Post by giogiobianco97 on 2020-12-03
Hello guys! I write this post because my laptop cannot connect to my WiFi anymore. I mean, it connects but, after a little time, it disconnects and than I am not able to connect again. I do not know why because until last week I was able to navigate without any problem. Now, sometimes I connect using my phone like hotspot or connecting the ethernet cable. I post also some outputs that maybe can be useful.

```

lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal

```

```

uname -a

Linux silvia 5.4.0-54-generic #60-Ubuntu SMP Fri Nov 6 10:37:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```

```

iwconfig 

lo        no wireless extensions.

wlo1      IEEE 802.11  ESSID:"AndroidAP"            
Mode:Managed  Frequency:2.412 GHz  Access Point: 8E:F5:A3:81:C8:0B             
Bit Rate=72.2 Mb/s   Tx-Power=20 dBm             
Retry short limit:7   RTS thr=2347 B   Fragment thr:off          
Power Management:off          
Link Quality=70/70  Signal level=-30 dBm            
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0          
Tx excessive retries:0  Invalid misc:168   Missed beacon:0

enp8s0    no wireless extensions.

```

```

rfkill list all

0: phy0: Wireless LAN    
Soft blocked: no    
Hard blocked: no

```

```

sudo lshw -c network  

*-network                       
 description: Ethernet interface       
product: RTL810xE PCI Express Fast Ethernet controller      
 vendor: Realtek Semiconductor Co., Ltd.       
physical id: 0       
bus info: pci@0000:08:00.0       
logical name: enp8s0       
version: 07       
serial: f8:a9:63:92:ea:53       
capacity: 100Mbit/s       
width: 64 bits       
clock: 33MHz       
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation      
 configuration: autonegotiation=on broadcast=yes driver=r8169 firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII       
resources: irq:18 ioport:5000(size=256) memory:b5600000-b5600fff memory:b5400000-b5403fff  

*-network       
description: Wireless interface       
product: RTL8188EE Wireless Network Adapter       
vendor: Realtek Semiconductor Co., Ltd.       
physical id: 0       
bus info: pci@0000:0a:00.0       
logical name: wlo1       
version: 01       
serial: 9c:ad:97:98:e7:68       
width: 64 bits       
clock: 33MHz       
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless       
configuration: broadcast=yes driver=rtl8188ee driverversion=5.4.0-54-generic firmware=N/A ip=192.168.178.28 latency=0 link=yes multicast=yes wireless=IEEE 802.11       
resources: irq:53 ioport:3000(size=256) memory:b5500000-b5503fff

```

Thank you very much!

---

### Post by wildmanne39 on 2020-12-03
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Did you install a Linux Mint kernel on Ubuntu?

---

### Post by giogiobianco97 on 2020-12-03
> **wildmanne39 said:**
> Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Did you install a Linux Mint kernel on Ubuntu?

Sorry, I am new in the forum and I am still not sure about how to write a post correctly.

No I did not install a Linux Mint kernel, I do not know what it is. Moreover some time ago I updated ubuntu from 18.04 LTS to 20.04 LTS, I do not know if this information can be useful.

---

### Post by wildmanne39 on 2020-12-03
No worries about the fonts.

Please click on the wireless script in my signature, follow the directions to run it and post the results back here using the pastebin link created and someone should be able to help you.

---

### Post by giogiobianco97 on 2020-12-03
Ok I should have succeeded. I hope I posted the result correctly. If there is any problem I apologize in advance. Thank you.

[ATTACH]287500[/ATTACH]

---

### Post by giogiobianco97 on 2020-12-09
Hi! The wifi seems working but I do not have modified anything so the problem is likely to present again...do anyone see something wrong in the settings of the wifi? In the previous post I attached wireless-info.tar.gz where you should find all the useful information. Thanks.

---

### Post by giogiobianco97 on 2020-12-28
Hello! I made the following attempts:

1. First of all, I disabled IPv6 protocol
2. I also wrote this command:

```
 [COLOR=#005400][FONT=Monaco]echo "options rtl8188ee swlps=0 ips=0 aspm=0 fwlps=0" | sudo tee /etc/modprobe.d/rtl8188ee.conf [/FONT][/COLOR]
```

3. In the end, I disabled the power management

Nothing seems working :( does someone have a idea? Thank you!

I cannot understand why I can connect using my phone as hotspot. So, it is not an  hardware problem.

---

