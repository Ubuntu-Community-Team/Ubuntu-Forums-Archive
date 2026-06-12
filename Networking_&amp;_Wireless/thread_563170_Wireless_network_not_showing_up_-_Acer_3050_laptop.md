---
title: "Wireless network not showing up - Acer 3050 laptop"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by mrmoney on 2007-09-29
Hi guys,

I am fairly new to Linux and Ubuntu, so I would appreciate any help anyone can give. I recently bought an Acer 3050-1270 laptop (Mobile AMD Sempron) and have two problems:
- my wireless connection is nowhere to be found
- and I have no sound via the front speakers (plugging in external speakers works though)

Most important is the wireless not working. It does not show up under System->Administrator->Network. The light on the front has never lit up. I am not sure what to do.

Any help greatly appreciated.

Thanks in advance

---

### Post by nosrednaekim on 2007-09-29
I have a 5050, same thing except with a turion X2,

see my tutorial for getting both of those things working here 

[http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/](http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/)

note that if you have the atheros card, BOTH issues are fixed in the gutsy release.

---

### Post by Jesterday on 2007-09-29
I have the same Laptop, the 3050 and I solved those problems by installing Gutsy, it was easy and has been running very stable!

---

### Post by mrmoney on 2007-09-29
Hi guys,

thanks for the responses. I actually found that link earlier but was unable to get it working even after following the instructions. The sound card didnt work from the instructions in the article,
and I used apt-get to grab ndsiwrapper. Not sure what, if anything, else I was supposed to do.

---

### Post by mrmoney on 2007-09-29
Also, I am on Feisty Fawn, is that going to be a problem?

---

### Post by mrmoney on 2007-10-03
Hi guys,

I am not sure what I have. When I use 'lspci'
it shows

```

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
**02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)**
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


```

the highlighted line I think is my problem. The os doesnt know what I have on there. Under System->Admin->Network it had only listings for wired connection and modem.

If I upgrade to Gutsy should this be fixed?

---

### Post by mrmoney on 2007-10-03
Ok Ive upgraded to Gutsy, and now the wireless card is recognized as an Atheros AR5006EG. 

Though it still does not show up under System->Admin->Network. Any thoughts on what I need to do next to get this sucker working?

Thanks again

---

### Post by nosrednaekim on 2007-10-03
paste the outputs of "iwconfig" and "ifconfig"

---

### Post by mrmoney on 2007-10-03
Hi thanks again for the help. Here are the outputs:

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

```

eth0      Link encap:Ethernet  HWaddr 00:1B:24:6E:C1:07  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe6e:c107/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1351 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:683457 (667.4 KB)  TX bytes:231987 (226.5 KB)
          Interrupt:20 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1500 (1.4 KB)  TX bytes:1500 (1.4 KB)


```

Also, I have since lost my sound completely after upgrading to Gutsy. The sound control no says when I click on it:
```

The volume control did not find any elements and/or devices to control. This means either that you do not have the right GStreamer plugins installed, or that you do not have a sound card configured

```

---

### Post by mrmoney on 2007-10-03
I found this link:

[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

which describe installing some drivers for the sound card I have. THough it goes through steps for installing already downloaded drivers. How do I know which drivers I need? Sorry if this is a really stupid question...

---

