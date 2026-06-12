---
title: "Feisty and Orinoco"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by crux19 on 2007-06-25
Hello,
I just installed Feisty on my Thinkpad T20 and having some difficulty getting my wireless card (Orinoco Gold) to work correctly.  I understand it should just work out of the box, which it did when I installed Kubuntu a few weeks ago.  

Network manager shows the wireless card present, but is not able to activate it and get a DCHP address.  I started searching forums and someone mentioned they had to install linux-wlan-ng drivers.  Did that with no luck.  

Continued reading and found that some people have multiple drivers running.  Did a 
lsmod | grep prism
lsmod | grep hostap
lsmod | grep orinoco

The first two came back with no results, the third came back with what I would expect, showing all of the orinoco drivers loaded.

Read some more and found that people have had success with Wicd, so I uninstalled Network Manager and installed Wicd.  Configured correctly but still no luck getting a DHCP address (I know everything should work fine since I had router and everything set up with Kubutnu a few weeks ago).

I'm not sure where it was originally set, but "iwconfig" shows that my card is using the Hermes1 chipset and has the correct AP ESSID of "charles_gerald" set.  When I attempted to change the ESSID with "iwconfig eth0 ESSID any", it stayed at "charles_gerald."

When I search for access points with Wicd, I get no results found even though my AP is right next to the laptop.  Something is off with my driver setup.

Thanks for any help.

---

### Post by crux19 on 2007-06-26
Here is some actual output.  I'm not sure I understand why there are two eth0 entries in the first output below.

```
ifroot@holmes:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:2D:4C:B1:28  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100 

eth1      Link encap:Ethernet  HWaddr 00:10:A4:8B:BC:1B  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:a4ff:fe8b:bc1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3408768 (3.2 MiB)  TX bytes:2054215 (1.9 MiB)

eth0:avah Link encap:Ethernet  HWaddr 00:02:2D:4C:B1:28  
          inet addr:169.254.4.205  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:3 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:710 (710.0 b)  TX bytes:710 (710.0 b)

```

```
root@holmes:~# iwconfig eth0
eth0      IEEE 802.11b  ESSID:"charles_gerald"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:0F:66:CD:FE:ED   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=47/92  Signal level=-46 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
root@holmes:~# lsmod | grep hostap
root@holmes:~# lsmod | grep prism
root@holmes:~# lsmod | grep orinoco
orinoco_cs             16900  1 
orinoco                43028  1 orinoco_cs
hermes                  8448  2 orinoco_cs,orinoco
pcmcia                 39212  1 orinoco_cs
pcmcia_core            40852  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
```

Thanks so much for any assistance.

---

### Post by t4thfavor on 2007-06-26
the link quality indicates that the card is connected.  Try assigning a static ip in the correct range and pinging stuff.

sudo ifconfig ethX 192.168.1.100 (modify accordingly)

I can never get network manager to work on my Cisco A/B/G card either (Atheros chipset), but it works fine with an intel card (ipw2200).

---

### Post by crux19 on 2007-06-26
Thanks.  Looks like Wicd kind of sees it now.  It shows that it's connected in the bottom (status bar) but still doesn't show the actual network being found.  I'll just set the rest up manually.

Seems like default route is already set and also netmask.  Looks like I just need to set the dns servers now.

Strange.

---

### Post by crux19 on 2007-06-27
So, Wicd kind of saw the wireless card, but not really - I couldn't do any configuration.  I switched back to network manager and assigned a manual ip address, subnet mask and gateway.  Still no luck.  I go to ping my router and get:
```

root@holmes:~# ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.250 icmp_seq=1 Destination Host Unreachable
From 192.168.1.250 icmp_seq=4 Destination Host Unreachable
From 192.168.1.250 icmp_seq=5 Destination Host Unreachable
From 192.168.1.250 icmp_seq=8 Destination Host Unreachable
From 192.168.1.250 icmp_seq=9 Destination Host Unreachable
```

Iwconfig shows:

```
root@holmes:~# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

irda0     no wireless extensions.

eth0      IEEE 802.11b  ESSID:"charles_gerald"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:0F:66:CD:FE:ED   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=55/92  Signal level=-33 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
root@holmes:~# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:02:2D:4C:B1:28  
          inet addr:192.168.1.250  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100
```


I'm really stuck on this one so any help would be greatly appreciated.
Thanks!

---

### Post by crux19 on 2007-07-02
Sorry for the bump, but I've been working on this for days now with no additional progress.  Not sure why this is giving me so much trouble.

Thanks for any help!

---

