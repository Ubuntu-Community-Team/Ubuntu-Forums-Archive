---
title: "Wireless detected and connected, but no internet &gt;:|"
date: 2006-12-24
forum: Networking &amp; Wireless
---

### Post by HyperFlexed on 2006-12-24
I am using Edgy Eft.

My laptop is an Acer Aspire 5102, and it has one of those troublesome Atheros wireless cards.

I have attached a screenshot of my wireless information. A picture is worth a thousand words. It seems like my wireless card is detecting the signal, and the signal is strong, but it is unable to aqquire an IP. As far as I know, no driver for this device has been installed, and frankly, I can't find it. Not even the manufacturer offers it.

But the fact that a signal can be detected is a good indication to me that this card is working in some capacity. Why no internets?

---

### Post by meng on 2006-12-24
Try opening a terminal/console and typing
sudo dhclient ath0

---

### Post by HyperFlexed on 2006-12-24
```

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:16:cf:49:98:49
Sending on   LPF/ath0/00:16:cf:49:98:49
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

---

### Post by meng on 2006-12-24
Is the wireless router working on DHCP?

---

### Post by HyperFlexed on 2006-12-25
Yup, this is visible in the original screenshot.

---

### Post by meng on 2006-12-25
> **HyperFlexed said:**
> Yup, this is visible in the original screenshot.
Well sorry to mention it, but as I see your original screenshot, your CARD is expecting DHCP, but that doesn't mean that the access point or router is DHCP-enabled. Also, we haven't excluded (although it's unlikely that it would be the case and you haven't realized it) that your router is MAC-restricted.

I doubt this is the cause of your problems, but we need to consider the other side of the equation here, i.e., there may be a problem with the router.

---

### Post by HyperFlexed on 2006-12-25
oops, I misread your post. My appologies.

I know my router is DHCP enabled. I can flip over to my windows partition, and the wireless connection works perfectly. (windows is set up to use DHCP)

I am familiar with MAC specific routers. As far as I know it my router is not set up to be MAC specific. Unless my laptop has a different MAC under different OSes, I don't think there would be a MAC issue.

---

### Post by meng on 2006-12-25
No need for you to apologize. Misunderstandings occur all the time. Unfortunately, my knowledge is limited.

---

### Post by HyperFlexed on 2006-12-29
bump? :(

---

### Post by Silentvoice on 2006-12-29
do sudo ifconfig ath0
and sudo iwconfig

print the results, see what we can do.

---

### Post by HyperFlexed on 2007-01-06
```
johnny@Johnny-Laptop:~$ sudo ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:16:CF:49:98:49
          inet6 addr: fe80::216:cfff:fe49:9849/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```


```
johnny@Johnny-Laptop:~$ sudo iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Ferguson Wireless"
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:9 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:4338-3936-4145-3531-3536   Security mode:restricted
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
```

---

### Post by derrylynne on 2007-01-07
If you have firefox type 'about:config' in the address bar. Scroll down to network.dns.disableipv6. If that is set to false with the mouse toggle it si it is set to true. Worked for me....

---

### Post by mgaskell on 2007-01-19
I have been reading this thread because I am having the exact same problems as HyperFlexed. This difference is that this is a recent problem. Everything was working fine yesterday. I don't know what I could have done.

I have an Intel internal wireless adapter that I understand should work "out of the box" with Edgy. Signal strength is strong and apparently the card is communicating with my network. It is DHCP. It works booting into the Windows partition. I just cannot get a wireless internet connection booting to Ubuntu.

Here are the printouts as suggested by Silentvoice:

mike@mike-laptop:~$ sudo ifconfig ath0
ath0: error fetching interface information: Device not found
mike@mike-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"LinksysDownStairs"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:D0:5C:D6   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=97/100  Signal level=-28 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Hope this is OK to mix posts.

](*,) 

Thanks,
Mike

---

### Post by stoic1973 on 2007-01-20
Hi,
I have been monitoring this thread, becoz I have a similar problem.
I am using UBUNTU 6.06, wireless card Netgear WG511T, and Netgear router. This combination works flawlessly with winXP. If I hard connect with the router I can get internet connectivity. The card is behaving as if connected, but no internet :( .

Network connection manager shows only eth0 & l0, PLease help !!! :confused: 


```

g@g-laptop:~$ sudo ifconfig ath0
Password:
ath0      Link encap:Ethernet  HWaddr 00:14:6C:07:A2:5C
          inet6 addr: fe80::214:6cff:fe07:a25c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:79 dropped:0 overruns:0 frame:79
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:6810 (6.6 KiB)  TX bytes:4334 (4.2 KiB)
          Interrupt:11 Memory:e0ac0000-e0ad0000

```

```

g@g-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"NETGEAR"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:DB:40:0E
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:3132-3334-3132-3334-3132   Security mode:restricted
          Power Management:off
          Link Quality=68/94  Signal level=-27 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


```

---

### Post by stoic1973 on 2007-01-24
hi,
still have not been able to resolve the situation. any help ???  

](*,)

---

### Post by Arabian on 2007-02-04
Hmm, I have Acer Aspire 5102 WLMi it works with no problems in DesktopBSD 1.6-RC1, I was going to try ubuntu, but this issue make me afraid of doing so.

---

