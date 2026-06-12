---
title: "[NOOB] Can't see wireless network with RTL8185"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by GabberNYC on 2007-12-30
Hello all!

I am new to Ubuntu and I am having an issue with wireless connectivity using RTL8185.  I have searched the forums for some clues but nothing so far.

The driver seems to be installed but I do not see the wireless networks that are around me.  In Windows I can see 6-7 networks at any time with good--excellent signal strength.  In Ubuntu, however, I can see none.  

Here is the output of some terminal commands, they might be helpful.

```
gabbernyc@CUPCAKE:~$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wlan0
       version: 20
       serial: 00:18:e7:2c:be:ac
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=r8180 multicast=yes wireless=802.11b/g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:16:e6:10:57:b8
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=64 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
gabbernyc@CUPCAKE:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Frequency=2.412 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gabbernyc@CUPCAKE:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:E6:10:57:B8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11056 (10.7 KB)  TX bytes:11056 (10.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:E7:2C:BE:AC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:782 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:40716 (39.7 KB)
          Interrupt:19 Memory:f8904000-f8904100 
```

... And a screenshot to illustrate a bit.

[http://www.shockforce.org/Screenshot.png](http://www.shockforce.org/Screenshot.png)

Thanks in advance!

---

### Post by coolbrook on 2007-12-30
What are the results of commands:

lspci

lspci -n

Perhaps there's a better driver to try.

---

### Post by GabberNYC on 2007-12-30
Hey, thanks for the reply.

Here they are:

```
gabbernyc@CUPCAKE:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
gabbernyc@CUPCAKE:~$ lspci -n
00:00.0 0600: 1106:0204
00:00.1 0600: 1106:1204
00:00.2 0600: 1106:2204
00:00.3 0600: 1106:3204
00:00.4 0600: 1106:4204
00:00.7 0600: 1106:7204
00:01.0 0604: 1106:b188
00:0a.0 0401: 1412:1724 (rev 01)
00:0b.0 0200: 10ec:8185 (rev 20)
00:0f.0 0101: 1106:3149 (rev 80)
00:0f.1 0101: 1106:0571 (rev 06)
00:10.0 0c03: 1106:3038 (rev 81)
00:10.1 0c03: 1106:3038 (rev 81)
00:10.2 0c03: 1106:3038 (rev 81)
00:10.3 0c03: 1106:3038 (rev 81)
00:10.4 0c03: 1106:3104 (rev 86)
00:11.0 0601: 1106:3227
00:11.5 0401: 1106:3059 (rev 60)
00:12.0 0200: 1106:3065 (rev 78)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:00.0 0300: 1002:4e48
01:00.1 0380: 1002:4e68
gabbernyc@CUPCAKE:~$ 
```

If I do need new drivers please include a *detailed* set of instructions on how to install them.  I tried doing that by myself already and it's like they are speaking Greek ... or Linux.

---

### Post by GabberNYC on 2007-12-31
010000100101010101001101010100000010000000101101001011010010000001110000011011000110010101100001011100110110010100100000011010000110010101101100011100000000110100001010

:)

---

### Post by krumble on 2007-12-31
I don't know if you have solved the problem but I had the same problem with my laptop using the same wireless card. I got around it by putting a fake ssid in the wireless networks menu so that the card is active i guess.  When I did that and I used the wireless assistant or wifi radar it would then pick up the networks.  Sorry if it may sound weird, I don't really know all that technical mumbo jumbo

---

### Post by GabberNYC on 2007-12-31
Hey, thanks for the suggestion.

I did what worked for you and still no go.  

Screenshot:
[http://www.shockforce.org/Screenshot2.png](http://www.shockforce.org/Screenshot2.png)

---

### Post by GabberNYC on 2008-01-01
Waaaaa!  I am very persistent and I will not give up on this.

Happy New Years btw!

---

### Post by kevdog on 2008-01-01
read my guide about connecting from the command line.  You need to put an extra character appended to the essid name (its a known bug and workaround)

---

### Post by krumble on 2008-01-01
[http://donnieknows.com/bin/view/Main/GatewayML3109](http://donnieknows.com/bin/view/Main/GatewayML3109)

That site is for my laptop which uses the same wireless card as the one you are talking about.  Just follow his instructions on how to get it to work and see if that helps at all

---

