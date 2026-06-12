---
title: "0% wireless connection"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by trethomil on 2009-12-17
Hello,

I'm still quite a novice at ubuntu so, here goes explaining th problem.

I recently installed xubuntu 9.10 on my old dell dimension laptop and was able to connect to our wireless network through the laptop's internal wireless card (not sure these come as stansard with this laptop as this is a reconditioned laptop that has been fiddled with by the shop I bought it from) but the connection was only at 14%. That was okay, because it still ran pretty well.

Since then, the hal daemon failed, which I fixed (found help on the internet for this), and the laptop was able to connect to the wireless network once more. After that, I tried to connect to a Orange Livebox. No luck there and I have removed it in favour of our old wireless router.

When I tried to reconnect to the wireless router - whose settings I have not changed at all and all our other device connect successfully to - the dell laptop connects, but only at 0%.

Not knowing what else to do, I reinstalled xubuntu as it had worked previously, but still, 0%. Is there anything I can do to help restore wireless connection?

The laptop's card is a RaLink Wireless PCI adapter RT2400 / RT2460, according to the terminal.

Aopolgies for the long post, I thought a complete history might be useful. Any help at all would be most appreciated.

---

### Post by northern lights on 2009-12-17
Please post the output of```
sudo lshw -C network && ifconfig && iwconfig
```Thank you.

---

### Post by Aaron2694 on 2009-12-17
Did you have a good connection when you were running Windows? It doesnt sound like a driver problem. Are any other computers or laptops able to connect to that router? Maybe your wireless card has just gone bad.

---

### Post by trethomil on 2009-12-17
Thanks for trying to help.

It's very long and I have no way of copying and pasting it across to my other computer. Do you need me to write out the whole thing or just the anything about the wireless?

---

### Post by northern lights on 2009-12-17
> **trethomil said:**
> Thanks for trying to help.

It's very long and I have no way of copying and pasting it across to my other computer. Do you need me to write out the whole thing or just the anything about the wireless?No USB flash-drive? (Re)writable CD? Wired ethernet?

---

### Post by trethomil on 2009-12-17
Sadly, no. But, I should have tomorrow. I'll try to post a copy of what was produced then.

Thanks again.

---

### Post by trethomil on 2009-12-17
Hello,

I have now copied the information you requested. Please find it below:

     *-network:0             
         description: Ethernet interface
         product: 3c905C-TX/TX-M [Tornado]
         vendor: 3Com Corporation
         physical id: 0
         bus info: pci@0000:02:00.0
         logical name: eth0
         version: 78
         serial: 00:0b:db:9f:f9:00
         size: 10MB/s
         capacity: 100MB/s
         width: 32 bits
         clock: 33MHz
         capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10MB/s
         resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:18000000-1801ffff(prefetchable)
    *-network:1
         description: Wireless interface
         product: Wireless PCI Adapter RT2400 / RT2460
         vendor: RaLink
         physical id: 3
         bus info: pci@0000:02:03.0
         logical name: wmaster0
         version: 00
         serial: 00:11:09:08:30:64
         width: 32 bits
         clock: 33MHz
         capabilities: pm bus_master cap_list logical ethernet physical wireless
         configuration: broadcast=yes driver=rt2400pci ip=10.42.43.1 latency=32 multicast=yes wireless=IEEE 802.11b
         resources: irq:5 memory:f8ffc000-f8ffdfff
  eth0      Link encap:Ethernet  HWaddr 00:0b:db:9f:f9:00  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:11 Base address:0xac00 
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:8 errors:0 dropped:0 overruns:0 frame:0
            TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:672 (672.0 B)  TX bytes:672 (672.0 B)
   
  wlan0     Link encap:Ethernet  HWaddr 00:11:09:08:30:64  
            inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
            inet6 addr: fe80::211:9ff:fe08:3064/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:3652 (3.6 KB)
   
  wmaster0  Link encap:UNSPEC  HWaddr 00-11-09-08-30-64-30-38-00-00-00-00-00-00-00-00  
            UP RUNNING  MTU:0  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
   
  lo        no wireless extensions.
   
  eth0      no wireless extensions.
   
  wmaster0  no wireless extensions.
   
  wlan0     IEEE 802.11b  ESSID:"elys1a"  
            Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: F2:98:F9:5D:FF:5D   
            Tx-Power=20 dBm   
            Retry  long limit:7   RTS thr:off   Fragment thr:off
            Power Management:off
            Link Quality:0  Signal level:0  Noise level:0
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0
  
Hope it helps, 'northern lights', or anyone else. Thanks in advance.

---

### Post by Extract_Here on 2009-12-18
I hate this problem the same thing happened to me when i first installed 9.04. Your going to need to achieve a direct connect from the router so you can get the correct software to install your wireless driver. 
 The things you will need to download 
1. ndiswrapper you can get this from the synaptic package manager 
(system>administrator>synaptic) 
2. You will need to find the driver for your wireless card(google search its brand name along with driver. eg. ("Belkin" Driver) download it even if its a Windows Exe. file 
3. Browse the windows exe. file and find the file with .inf on the end eg. (belkin.inf)
4. once you have found that file open up Ndiswrapper It has a different name in the menu its called windows wireless drivers. (system>admin>windows wireless drivers)
5. drag the .inf file into the NDiswrapper and your wireless should connect.

if your still having problems message me and we can talk further.

-may the source be with you

---

### Post by bkratz on 2009-12-18
> **Extract_Here said:**
> I hate this problem the same thing happened to me when i first installed 9.04. Your going to need to achieve a direct connect from the router so you can get the correct software to install your wireless driver. 
 The things you will need to download 
1. ndiswrapper you can get this from the synaptic package manager 
(system>administrator>synaptic) 
2. You will need to find the driver for your wireless card(google search its brand name along with driver. eg. ("Belkin" Driver) download it even if its a Windows Exe. file 
3. Browse the windows exe. file and find the file with .inf on the end eg. (belkin.inf)
4. once you have found that file open up Ndiswrapper It has a different name in the menu its called windows wireless drivers. (system>admin>windows wireless drivers)
5. drag the .inf file into the NDiswrapper and your wireless should connect.

if your still having problems message me and we can talk further.

-may the source be with you

@Extract_Here

I believe you have to install ndisgtk rather than ndiswrapper to get the system>admin>windows wireless driver in the menus.  ndisgtk will actually load two other files related to ndiswrapper automatically.

---

