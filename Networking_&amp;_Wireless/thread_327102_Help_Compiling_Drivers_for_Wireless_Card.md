---
title: "Help Compiling Drivers for Wireless Card"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by Famicommie on 2006-12-28
For Christmas my brother gave me a wireless card (probably because he wants his laptop back that I've been networking to in order to use his wireless card). It's a ZyXel ZyAIR G-302 v3On my Windows drive I had no problems getting it up and running. Linux has been an entirely different story...

Since I'm a linux noob, I plugged the laptop back in so I could read up on the forums to see what people were doing to get it to work. The device was recognized right out of the box. Here are the results of ifconfig:

```

wlan0     Link encap:Ethernet  HWaddr 00:13:49:89:8A:46
          inet6 addr: fe80::213:49ff:fe89:8a46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:25950 dropped:892 overruns:0 frame:0
          TX packets:39988 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:50 (50.0 b)  TX bytes:2007245 (1.9 MiB)
          Interrupt:217 Memory:f8a52000-f8a52100

```

I used the Network manager and set up the ESSID and the key in hex format. Changing the default gateway device to wlan0 proceeded to kill my internets. So I figured that maybe the driver was the problem. Since my brother knows how hard I'm trying to become M$ free he made sure to get me a card featuring the tux penguin on the box.

Figuring that maybe reinstalling the drivers was in order, I proceeded to try and install. The command specified by the instructions was to run the script ./makedrv. BASH denied me permission, so I sudo- i into root mode and got the following:

```
root@integral:/home/fami/Desktop/Linux_26x-8185(v1.0.0)# ls
Linux 2.6.x(1.0)  release_note.txt
root@integral:/home/fami/Desktop/Linux_26x-8185(v1.0.0)# cd Linux\ 2.6.x\(1.0\)/root@integral:/home/fami/Desktop/Linux_26x-8185(v1.0.0)/Linux 2.6.x(1.0)# ls
ifcfg-wlan0  rtl818x.tar.gz  wlan0down  wpa_supplicant-0.3.8.tar.gz
makedrv      stack.tar.gz    wlan0up
readme       wlan0dhcp       wpa1.conf
root@integral:/home/fami/Desktop/Linux_26x-8185(v1.0.0)/Linux 2.6.x(1.0)# ./makedrv
-bash: ./makedrv: Permission denied
```

No luck. Haven't really tried ndiswrapper yet, but I'd prefer to use the Open Source drivers if possible. Halp?

---

### Post by bernied on 2006-12-28
I'm almost certain that the problem is not the driver, since you have a sane response in ifconfig. It's just the network stuff you need to figure out.

---

### Post by bernied on 2006-12-28
I think you can do all this with the iwconfig command, something like:
```
sudo iwconfig wlan0 essid "Wireless SSID name"
sudo iwconfig wlan0 key 0123-4567-89
```If that works, then you need to turn off your wired, and turn on the wireless:
```
sudo ifconfig eth0 down
sudo ifconfig wlan0 up
```

You can make all this permanent in /etc/network/interfaces

Read the man pages for more details:
```
man iwconfig
man ifconfig
man interfaces
```

---

### Post by Famicommie on 2006-12-29
When I ran your commands it completely killed my internets.

I set the proper ESSID and set the WEP key to the hex code that allowed my card to run on my Windows partition. But, as soon as I disabled my eth0 and eth1 I lost the internet and I couldn't get it back until I restarted (could that have something to do with the way Beryl interacts with the kernal?)

At this point, I'm considering returning the card and finding one more Ubuntu friendly. Does anyone have any advice on how to troubleshoot my current card, or on what cards work best with Ubuntu out of the box?

---

### Post by bernied on 2006-12-29
If you are connected to the network via a cable, then this command (that I asked you to do):
```
sudo ifconfig eth0 down
```will disconnect you from the internet. But it is easy to bring it back up again with:
```
sudo ifconfig eth0 up
```without having to restart.

If you start your machine with the LAN cable plugged in, it will default to using that for your internet connection. 

If you are using the internet, say with firefox, via the cable, then you disconnect the cable and connect the wireless, you will probably need to close all windows of firefox (or whatever you are using), then restart firefox, before it will work. Firefox will be trying to continue connections through the cable, rather than through the wireless.

Does the output of 'ifconfig' change between before and after issuing those commands? And were there any errors displayed? The computer is trying to tell you what is going on, it's just a matter of knowing its language.

I also suspect that the network manager is working for you - you perhaps just need to shut down your 'internets' then restart them after connecting to the wireless. Does Network Manager say that you are connected to the wireless network?

---

### Post by Famicommie on 2006-12-29
ifconfig while using eth0:

```
eth0      Link encap:Ethernet  HWaddr 00:14:85:BF:02:9C
          inet addr:192.168.0.129  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:febf:29c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2066 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:982427 (959.4 KiB)  TX bytes:268483 (262.1 KiB)
          Interrupt:201

eth1      Link encap:Ethernet  HWaddr 00:11:95:1D:4A:2A
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:85 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3616 (3.5 KiB)  TX bytes:3616 (3.5 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:13:49:89:8A:46
          inet6 addr: fe80::213:49ff:fe89:8a46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:32 dropped:102 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:32 (32.0 b)  TX bytes:6775 (6.6 KiB)
          Interrupt:209 Memory:f8a12000-f8a12100

```

I then unplugged the ethernet cable and restarted. No internet. ifconfig reported this about the wlan0:

```

wlan0     Link encap:Ethernet  HWaddr 00:13:49:89:8A:46
          inet6 addr: fe80::213:49ff:fe89:8a46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:63 dropped:979 overruns:0 frame:0
          TX packets:150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:70 (70.0 b)  TX bytes:26971 (26.3 KiB)
          Interrupt:209 Memory:f89cc000-f89cc100

```

And iwconfig displayed:

```
wlan0     802.11b/g linked  ESSID:"Ordinance"
          Mode:Managed  Frequency=2.484 GHz  Access Point: 00:12:17:CD:D9:07
          Bit Rate=54 Mb/s
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The MAC address is correct, but I still don't get internet.

---

### Post by meng on 2006-12-29
You may have to
sudo dhclient wlan0

after all the other stuff.

---

### Post by Famicommie on 2006-12-29
Okay, but before I go through the entire dance again, I just want to confirm the steps involved (I still have to restart after turning off eth0 for some reason).

To clarify, I am running Dapper Drake 32bit. I have a Zyxel ZyAIR G-302 v3 wireless card. Also, I have Beryl running right now (don't know if that changed anything, but I feel it should be noted just to make sure). Any other questions about the system: please ask.

First I will create a txt file and save the ifconfig information and the iwconfig information. From there I will disable eth0 and eth1. After those are deactivated, I will enable wlan0.

Information from ifconfig and iwconfig will be saved in a txt file. Then I will run the dhclient command and again save the ifconfig and iwconfig.

Anything I'm missing before I begin?

---

### Post by meng on 2006-12-29
You don't have to save that stuff in a text file (will if you do, it may make it easier for you to post the result here, but it's not part of the process of activating the card).

To clarify:
sudo ifconfig eth1 down
sudo ifconfig eth0 down
sudo iwconfig wlan0 essid [your essid] key restricted [your wep key in hexadecimal]
sudo ifconfig wlan0 up
sudo dhclient wlan0

---

### Post by Famicommie on 2006-12-29
Didn't work. I ran the commands exactly as you specified:

```
sudo ifconfig eth1 down
sudo ifconfig eth0 down
sudo iwconfig wlan0 essid Ordinance key restricted lolthiswasmyhexcode
sudo ifconfig wlan0 up
sudo dhclient wlan0
```

ifconfig before I started:

```
eth0      Link encap:Ethernet  HWaddr 00:14:85:BF:02:9C  
          inet addr:192.168.0.129  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:febf:29c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4085 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3777 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3013224 (2.8 MiB)  TX bytes:476535 (465.3 KiB)
          Interrupt:201 

eth1      Link encap:Ethernet  HWaddr 00:11:95:1D:4A:2A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:85 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3616 (3.5 KiB)  TX bytes:3616 (3.5 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:13:49:89:8A:46  
          inet6 addr: fe80::213:49ff:fe89:8a46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:77 dropped:522 overruns:0 frame:0
          TX packets:183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32 (32.0 b)  TX bytes:21363 (20.8 KiB)
          Interrupt:209 Memory:f8a12000-f8a12100 

```

ifconfig after turning off eth0 and eth1:

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:85 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3616 (3.5 KiB)  TX bytes:3616 (3.5 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:13:49:89:8A:46  
          inet6 addr: fe80::213:49ff:fe89:8a46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:77 dropped:555 overruns:0 frame:0
          TX packets:183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32 (32.0 b)  TX bytes:21363 (20.8 KiB)
          Interrupt:209 Memory:f8a12000-f8a12100 
```

config before dhclient command:

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:85 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3616 (3.5 KiB)  TX bytes:3616 (3.5 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:13:49:89:8A:46  
          inet6 addr: fe80::213:49ff:fe89:8a46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:79 dropped:588 overruns:0 frame:0
          TX packets:191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32 (32.0 b)  TX bytes:23656 (23.1 KiB)
          Interrupt:209 Memory:f8a12000-f8a12100 
```

ifconfig after dhclient command:

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:85 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3616 (3.5 KiB)  TX bytes:3616 (3.5 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:13:49:89:8A:46  
          inet6 addr: fe80::213:49ff:fe89:8a46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:79 dropped:617 overruns:0 frame:0
          TX packets:198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32 (32.0 b)  TX bytes:26232 (25.6 KiB)
          Interrupt:209 Memory:f8a12000-f8a12100 
```

I think I'm about to go and exchange this card for a dlink or something :/

---

