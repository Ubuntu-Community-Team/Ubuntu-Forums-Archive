---
title: "Lenovo T60 Gutsy Wireless causes Freezes"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by kikazaru on 2007-11-04
Please help me.. I managed to get wireless working to some extent... except that the computer pretty much locks up after an unpredictable length of time... sometimes if I try to fiddle with wireless settings and sometimes even when I'm doing nothing at all. 

What do I need to do to get wireless working stably...?


```

 ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:16:41:E3:B9:F2  
          inet addr:192.168.3.4  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::216:41ff:fee3:b9f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9402 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:7117922 (6.7 MB)  TX bytes:1839834 (1.7 MB)
          Base address:0x3000 Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.43.1  Bcast:172.16.43.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.105.1  Bcast:192.168.105.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lsmod | grep ath
ath_rate_sample        15104  1 
ath_pci               114856  0 
wlan                  211120  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               233952  3 ath_rate_sample,ath_pci


```

Here are the notes from the wireless card reported by windows xp

```


11a/b/g/n Wireless LAN Mini-PCI Express Adapter
PCI Slot 1 (PCI bus 3, device 0, function 0)
Manufacturer: Atheros

11d Mode Switch : disable
802.11b Preamble : Long and Short
Map Registers : 256

Driver Atheros 6.0.2.75

IRQ 17
Memory Range EDF00000-EDF0FFFF

```

Anything else I can usefully add...? Please help me... I've been going round in circles for two days now.

Recently upgraded to 7.10 from 7.04.

---

### Post by stix213 on 2008-02-11
I'm having the same problem.  At my work I have multiple wifi access points that all have the same name (so we can seamlessly move around the office I suppose), but I have noticed that the freezing coincides with the wifi changing access points.  

Running "iwevent" I see that it looses association and then gets it again, sometimes with a different AP and sometimes with the same.  This happens maybe 5 times per minute, so it is ridiculous how often it is trying to change access point.  

Running "iwconfig" I also can see that it switches between our G & A access points over and over and over.  

Unfortunately I have tried just disabling what I thought was the correct wifi kernel module "ipw3945" but the freezing continues.  Moving the wifi kill switch always immediately clears up the problem temporarily.  I'm at a loss on how to permanently correct the problem.

---

### Post by dca on 2008-02-11
I hate to tell you this, but depending on the errors coming up in your logs, it may be NetworkManager specific.  Have you tried installing WICD and trying that to command your network card(s)???  It completely removes gnome-network-manager and applet upon installation requiring you to add the service manually to your session settings under preferences.  This could verify if it's specific to NM (bug or glitch) or your drivers...

---

### Post by stix213 on 2008-02-11
No I haven't tried that yet.  I'll give it a try if the problem keeps happening.  

I just tried temporarily removing the ipw3945 kernel module, and the problem continued.  The machine would freeze, then I move the kill switch to the opposite position (either turning on or off) and then it immediately resumes.  I noticed that the kill switch also controls the blue tooth device, so now I've tried disabling the blue tooth device in the BIOS, and so far the machine is running great even using the wireless with the blue tooth device disabled.  

Crossing my fingers that this continues to work well :)

---

### Post by dca on 2008-02-11
Good luck, that's actually interesting...  On my laptop the Bluetooth doesn't work, however, there's an error after the GRUB screen that warns that it was not able to allocate that resource or something like that...

---

### Post by stix213 on 2008-02-13
ehhh, the problem returned the next day even with the bluetooth device disabled still.

---

### Post by dca on 2008-02-13
Are you running VMWare on your laptop?

---

### Post by stix213 on 2008-02-25
No, not running vmware, although I sometimes have a copy of XP running under VirtualBox, but the problem occurs even with that not running.  I've found a work around for my problem though by forcing the AP and channel that I let my T60 talk using.  

eth1 is the interface of my wireless adapter

1) run command iwevent to watch for events such as access point changes
2) Pick one of the access points from the iwevent output that I want to force to stay on then run
sudo iwconfig eth1 essid <my_essid> ap <ap_address>
replace <my_essid> with the Id of the network and replace <ap_address> with the address for my access point listed in the iwevent output
3) wait a few seconds for the wifi to get connected to the access point, then check what channel it is connected on using:
iwlist eth1 channel
4) Now force the channel as well so it can't change that either
sudo iwconfig eth1 essid <my_essid> ap <ap_address> channel <channel>
replacing <channel> with the channel number listed in the "iwlist eth1 channel" output

Now as long as I'm not moving to different access points around the office my problem is solved.  It looks like the freezing problem has to do with my wireless card always trying to get link to the access point with the best signal, but there are so many overlapping signals in my office (A,B,& G all supported and with access points that broadcast on multiple channels simultaniously, all using the same ESSID) that it can continuously switch back and forth causing the T60 to appear frozen. 

Hope this helps anyone else with this problem.

---

