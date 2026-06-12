---
title: "D-Link 642 and my Lenovo T60 -- doesn't work"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by mr_e_uss on 2008-06-19
I apologize if this has been answered before - -but I couldn't find a clear answer.

My Lenovo T60 has 802.11a/b/g built in (and I can connect wirelessly just fine).  However, I'd like to benefit from my D-Link 625's "N" support.  I have plugged in my D-Link DWA-642 Rangebooster N Notebook Adapter -- but it doesn't seem to be recognized by Ubuntu (8.04 LTS).  Neither the Link nor Activity LEDs blink.

I am not sure if the card is being recognized at all...  (It's a PCMCIA card.)

Any help would be greatly appreciated.

Thanks!

---

### Post by mr_e_uss on 2008-06-19
It appears that my card is being "noticed".  I executed "lspci", and this is what I see:

16:00.0 Ethernet controller: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter (rev 01)

---

### Post by AVT- on 2008-06-19
If the card is being recognized and it's an Atheros card, you need to enable two drivers in restricted drivers manager for it to work.

---

### Post by mr_e_uss on 2008-06-19
Thanks for responding, AVT.

Both drivers are already enabled (assuming you mean the "Atheros HAL" driver and the "Atheros 802.11 wireless LAN cards" driver).  The T60's built-in wireless chipset is also Atheros -- and I have been using the internal chipset for some time.

Maybe the issue is that there is no eth1 or ath1 interface associated with the PCMCIA wireless card?

---

### Post by AVT- on 2008-06-19
Post the output of:

ifconfig

And the contents of:

/etc/network/interfaces

Also, are you using network manager?

---

### Post by mr_e_uss on 2008-06-19
I am using Network Manager.  Here's the other info you requested...

ltub:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:16:cf:b9:85:b0  
          inet addr:192.168.1.119  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:feb9:85b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29046 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22024 errors:14 dropped:14 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23861597 (22.7 MB)  TX bytes:3066452 (2.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1372 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69448 (67.8 KB)  TX bytes:69448 (67.8 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.100.1.81  P-t-P:10.100.1.81  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:224 (224.0 B)  TX bytes:125 (125.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CF-B9-85-B0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:221466 errors:0 dropped:85 overruns:0 frame:111335
          TX packets:25826 errors:10 dropped:14 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:52472522 (50.0 MB)  TX bytes:4216202 (4.0 MB)
          Interrupt:21 

ltub:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by AVT- on 2008-06-19
In network-manager, go to manual configuration. Do you see the wireless card? If so, then everything should already be working.

What happens when you try to connect using network-manager?

---

### Post by mr_e_uss on 2008-06-19
Hmmm.  I've got roaming enabled, so everything is grayed out in the Manual Configuration mode.  I do not see any way to me to determine if my card is there or not...

Is there something in /proc I can look at?

---

### Post by AVT- on 2008-06-19
Wait a minute, I just realized your laptop has onboard wifi.

Can you try disabling it in BIOS? If so, does iwconfig show any wireless cards?

---

### Post by mr_e_uss on 2008-06-19
Also, the thing that concerns me most is that there is no LED activity on the card -- ACT and LINK are solid off.

---

### Post by mr_e_uss on 2008-06-19
I missed your most recent post.

I can try to disable it -- but, not right now :-)

I'll give it a try and see what happens.  I'll post back later.

Thanks for your help...

---

### Post by mr_e_uss on 2008-06-20
Well, when I disable the internal wireless device (via the BIOS), the PCMCIA wireless card still doesn't do anything (and I am left with no wireless support at all).

I have Device Manager installed. For the internal wireless card (after I re-enable it in the BIOS), Device Manager shows the following "tree"

PCI Bridge
   Ethernet Controller
       WLAN Interface
       Networking Wireless Control Interface

For the PCMCIA wireless card, this is what I see:

PCI Bridge
   Ethernet Controller

Any ideas?

Thanks...

---

