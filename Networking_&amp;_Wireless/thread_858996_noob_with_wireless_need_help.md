---
title: "noob with wireless need help"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by halln on 2008-07-14
I've been using ubuntu with more than a year now, everything working fine with my wired desktop until I bought a laptop and a wireless cable router. I bought a ZyXEL router because It support linux (written on the box), but there is no installation CD inside(driver). I know, we usually don't need driver in linux. I installed ndiswrapper, etc. to make your Dell inspiron 1525 work wirelessly, I can see my router and some wireless network around, I had about 90+ wireless signal on my panel but I couldn't connect tru the net. no internet at all. Did I miss something? I am totally noob with wireless, I dont even have any idea to secure it. I've read the how to on top of this thread but its very complicated for me, is there any simpler than that?. Thanx in advance.:)
This is my Iwlist scan:-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:06:CB:CC
                    ESSID:"SKY99980"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:19:CB:3A:2D:CC
                    ESSID:"ZyXEL"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:87/100  Signal level:-40 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:18:4D:C9:AB:36
                    ESSID:"netgear"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:57/100  Signal level:-59 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

---

### Post by halln on 2008-07-14
knock knock! anybody home? pls. help

---

### Post by kevmitch on 2008-07-14
You shouldn't need to worry about what operating systems your router supports. Any router that I've seen has a decent web interface that can be viewed from any browser on any operating systems. Installation CD's for routers almost always just contain crapware. 

Did you try to connect to YOUR router by clicking on it? You should then see the network manager do a little animation while it's connecting. 

You can get more information about the state of your wireless card with

```
/sbin/iwconfig
```

My output looks like this

```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"hendecagon\x00"  Nickname:""
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:1B:11:68:C9:F9   
          Bit Rate:54 Mb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-31 dBm  Noise level=-96 dBm
          Rx invalid nwid:2960  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

My wireless card is wlan0 and it says that I'm connected to the "hendecacon" network. 

You can also get information about more general networking with

```
/sbin/ifconfig
```
```

eth0      Link encap:Ethernet  HWaddr 00:15:58:86:70:ee  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1204 (1.1 KiB)  TX bytes:1204 (1.1 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7E-41-09-C1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73337 errors:0 dropped:0 overruns:0 frame:2207
          TX packets:13861 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:195 
          RX bytes:33498950 (31.9 MiB)  TX bytes:2273042 (2.1 MiB)
          Interrupt:17 

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:41:09:c1  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43972 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13847 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47824980 (45.6 MiB)  TX bytes:1718579 (1.6 MiB)

```
Here it's saying that wlan0 has ip address 192.168.1.102. Unless there is some nameserver issue, and provided the router itself has an internet connection, you should be able to browse the web if you have an IP.

---

### Post by halln on 2008-07-14
This is what I've got:
-laptop:~$ /sbin/iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"ZyXEL"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:CB:3A:2D:CC   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:87/100  Signal level:-40 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

noel@noel-laptop:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:44:e9:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:0e:5c:ed:30:ad  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:498218 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:422579212 (403.0 MB)  TX bytes:15810743 (15.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2629 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2629 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:131512 (128.4 KB)  TX bytes:131512 (128.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:bf:1d:37  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:febf:1d37/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4704 (4.5 KB)  TX bytes:44251 (43.2 KB)
          Interrupt:17 Memory:fe7fc000-fe800000

---

### Post by kevmitch on 2008-07-15
Allright, well it looks like you're associated, and you have an ip address. 
Can you ping your router?
```
ping 192.168.1.1
```

Can you access the internet if you plug into the router with wired Ethernet?

---

### Post by kevmitch on 2008-07-15
You can also see if you can access the router's web interface by typing

[http://192.168.1.1](http://192.168.1.1) 

into your web browser's address bar.

---

### Post by BobMurray999 on 2008-07-15
I have a similar problem with my wireless setup.  I am running WUBI.  I wind up with a wlan0 and a wlan0-acpi partially defined.  wlan0 with no IP address and wlan0-acpi with some goofy address assigned.  Neither works to connect to anything.  I cannot connect to my router or ping anything.  

I am proceeding through the troubleshooting docs and I am at the point where it says to "reboot the Kernel with acpi turned off".  How?

I have no internet or LAN/WAN access through WUBI.  I have to reboot Windows XP SP3 to get back to use my browser.  

Another suggestion was to "install ndisgtk",  when I run "sudo apt-get install ndisgtk"  I just get not found.

---

### Post by halln on 2008-07-15
here it goes:
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=254 time=1.96 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=254 time=1.85 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=254 time=1.92 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=254 time=2.89 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=254 time=2.36 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=254 time=1.97 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=254 time=2.66 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=254 time=2.84 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=254 time=1.88 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=254 time=1.95 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=254 time=2.13 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=254 time=2.91 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=254 time=2.89 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=254 time=1.92 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=254 time=1.93 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=254 time=2.66 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=254 time=1.97 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=254 time=1.97 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=254 time=1.95 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=254 time=2.06 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=254 time=2.70 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=254 time=2.14 ms
64 bytes from 192.168.1.1: icmp_seq=23 ttl=254 time=2.06 ms
64 bytes from 192.168.1.1: icmp_seq=24 ttl=254 time=1.98 ms
64 bytes from 192.168.1.1: icmp_seq=25 ttl=254 time=2.81 ms
64 bytes from 192.168.1.1: icmp_seq=26 ttl=254 time=1.97 ms
64 bytes from 192.168.1.1: icmp_seq=28 ttl=254 time=3.10 ms
64 bytes from 192.168.1.1: icmp_seq=29 ttl=254 time=2.41 ms
64 bytes from 192.168.1.1: icmp_seq=30 ttl=254 time=1.96 ms
64 bytes from 192.168.1.1: icmp_seq=31 ttl=254 time=2.19 ms
64 bytes from 192.168.1.1: icmp_seq=32 ttl=254 time=2.07 ms
64 bytes from 192.168.1.1: icmp_seq=33 ttl=254 time=1.77 ms
64 bytes from 192.168.1.1: icmp_seq=34 ttl=254 time=1.86 ms
64 bytes from 192.168.1.1: icmp_seq=35 ttl=254 time=1.99 ms
64 bytes from 192.168.1.1: icmp_seq=36 ttl=254 time=1.92 ms
64 bytes from 192.168.1.1: icmp_seq=37 ttl=254 time=1.98 ms
64 bytes from 192.168.1.1: icmp_seq=38 ttl=254 time=2.03 ms
64 bytes from 192.168.1.1: icmp_seq=39 ttl=254 time=2.85 ms
64 bytes from 192.168.1.1: icmp_seq=40 ttl=254 time=2.15 ms
64 bytes from 192.168.1.1: icmp_seq=41 ttl=254 time=2.08 ms
64 bytes from 192.168.1.1: icmp_seq=42 ttl=254 time=1.89 ms
64 bytes from 192.168.1.1: icmp_seq=43 ttl=254 time=1.87 ms
64 bytes from 192.168.1.1: icmp_seq=44 ttl=254 time=2.13 ms
64 bytes from 192.168.1.1: icmp_seq=45 ttl=254 time=2.02 ms
64 bytes from 192.168.1.1: icmp_seq=46 ttl=254 time=1.93 ms
64 bytes from 192.168.1.1: icmp_seq=47 ttl=254 time=2.81 ms
64 bytes from 192.168.1.1: icmp_seq=48 ttl=254 time=1.98 ms
64 bytes from 192.168.1.1: icmp_seq=49 ttl=254 time=2.03 ms
64 bytes from 192.168.1.1: icmp_seq=50 ttl=254 time=2.57 ms
64 bytes from 192.168.1.1: icmp_seq=51 ttl=254 time=2.72 ms
64 bytes from 192.168.1.1: icmp_seq=52 ttl=254 time=1.96 ms
64 bytes from 192.168.1.1: icmp_seq=53 ttl=254 time=3.01 ms
64 bytes from 192.168.1.1: icmp_seq=54 ttl=254 time=5.28 ms
64 bytes from 192.168.1.1: icmp_seq=55 ttl=254 time=2.26 ms
64 bytes from 192.168.1.1: icmp_seq=56 ttl=254 time=1.85 ms
64 bytes from 192.168.1.1: icmp_seq=58 ttl=254 time=2.86 ms

---

### Post by kevmitch on 2008-07-15
Ok, so you're definitely connecting to the router. Now you can try pining the outside world

```
ping google.com
```

Given what you've described so far, I'm guessing that that will not work. It's possible that it's just a DNS issue, in which case, 

```
ping 64.233.187.99
```

will work. 

In any case, you will want to go into your router's config page

```
http://192.168.1.1
```

Somewhere in there, you'll be able to release and renew the ip address of your router on the internet. You want to make sure that you have an address. You also want to make sure that you have addresses for one or two DNS servers. These should all be automatically assigned unless your Internet provider has some strange setup.

---

### Post by halln on 2008-07-15
I did try to reconfigure my router again this morning, just in case I did something wrong during configuration but I'm bit confused what to type in this field:(attach file)

---

### Post by halln on 2008-07-15
This is some info of my wired connection (attach)

---

### Post by halln on 2008-07-15
still can't make internet to work, more help pls.:guitar:

---

### Post by kevmitch on 2008-07-15
Ok, I'm assuming that the screenshot you've shown for your wired connection is with your computer connected directly to your modem or whatever it is that gives you your internet connection. If this is the case, then you essentially want the router to take the place of the computer in this connection. To first order, just copying the values might work, however it is probably better if you can get these values filled in automatically because they might change in the future and you don't want to have to worry about updating them. Did step 1 or 2 in the router config ask you if you wanted to use "DHCP" or to get your ip address "dynamically". If so, you want to say yes to either or both of those questions. 

Depending on how your ISP is set up, this, by itself may or may not work. Your isp might only assign an ip address to devices that it knows about, (or rather MAC addresses that it knows about). You computer that you plug directly into the modem is clearly one such device since it gets an ip address. The easiest thing is if you can somehow clone the mac address of your computer on your router (that should also be in the menu somewhere). Otherwise, you'll have to go the process of registering the mac address of your router with your ISP.

When all is working, you want to have the "WAN IP address" on the router to be the same (or possibly just similar to) the "IP address" of the computer (though they can't be using the same address at the same time).

You also want "WAN IP subnet mask" to match the "subnet mask" of the direct connection. The "Gateway ip address" should be the same as "default route" and you want at least "first dns server" to have either the address of the "primary dns server" or "secondary dns server" listed in the direct connection.

---

### Post by halln on 2008-07-16
I think I already did those things during router configuration, I just follow the instruction in setting up the router using their wizard but still cant connect to internet, I still got a good signal. I think I have to isolate this problem by returning back the router to the store to eliminate defective router issue then start all over again. I hope you're still on my side by then. Thanks a lot mate, till next.

---

### Post by halln on 2008-07-16
Got the replacement today, configured it but still, again no wireless  internet

---

### Post by halln on 2008-07-16
Still can't get wireless to work. I reinstalled hardy today on my dell inspiron 1525 (purely ubuntu) but still no joy, so it's not my router coz I replaced it already this morning plus the clean hardy install. Run out of idea what to do next. I can still see my router and some network around.What to do, What to do:confused::confused:

---

### Post by kevmitch on 2008-07-17
what were the first two configuration pages on the router before the screenshot you showed?

---

### Post by halln on 2008-07-17
> **kevmitch said:**
> what were the first two configuration pages on the router before the screenshot you showed?

First you have to type 192.168.1.1 on your internet browser then a page would pop up telling you to enter temp. password just 1234 then login.
Then a page shows that you can change your password then confirm, etc.

And a page again asking you to run the Wizard, Basic, Advance set up. I choose wizard, Do this according to the leaflet, (By the way I'm doing this setup with 98% signal on my router.)Next few pages are autofill(to confirm the name of the router or you wish to change it). Security, I choose Auto WPA-PSK with self generating key. (I choose WPA-PSK with customized key aswell previously, so that I will not forget it, no luck..wont connect).

Next it will check for WAN connection (takes some time). Found ETHERNET.

Internet Configuration: I just follow the wizard. Clicked Automatically from your ISP then next.

WAN MAC ADDRESS: Three choices, Factory Default, Clone the comp. mac address, Set the wan mac address. I choose Factory Default as the leaflet suggested.

BANDWIDTH MANAGEMENT: Tick the box ENABLE BM FOR ALL TRAFFIC AUTOMATICALLY (as suggested).

Set up complete: click apply to save your settings but always it hangs from here it will never reach the FINISH button to highlight.I waited for an hour or so, but no joy, have to force quit. Do same thing all over again, sometimes it reach the finish and some congratulations but still wont connect using either self generated or customized password.

Hope this helps.:confused:

---

### Post by halln on 2008-07-17
Thanks to kevmitch for his time trying to help me. My wireless connection finally working now, YEHAAAAAA!!. It's so easy by just unplugging the modem and turning it on again while I was on my wireless connection and presto!! I got connected to the net. Now I have to sort lot of things to my ubuntu install coz of re installation I did, compiz,emerald,codecs,themes,awn, etc. and I had multiple users in this lappy. I think I have to start now.:lolflag:

---

### Post by kevmitch on 2008-07-18
I'm glad you got it working! The problem you're describing at the end of the router configuration is likely due to the fact that the router reboots after the last step. You are then not able to actually load the final page because you get booted off the wireless network during the reboot and the connection times out before you can reassociate. I would recommend doing any router setup via a wired connection since this can usually recover from the disconnection associated with a reboot much faster.

---

### Post by kevmitch on 2008-07-18
Oh, and did you get wpa-psk working. You should really use some sort of authentication otherwise people will steal you bandwidth and worse you might be held responsible if they do anything nasty over your connection.

---

