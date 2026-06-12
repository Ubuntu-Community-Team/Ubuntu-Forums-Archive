---
title: "Cisco Aironet 350, Fiesty, and an IBM T30 - Wireless not working"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by shadowimmage on 2007-06-30
I'm a new user to try out Ubuntu, so I started with the latest distribution-7.04. I set it up as a dual boot for my Laptop, since I wasn't sure I wanted to go full Linux.

I am having a problem with my wireless card, a Cisco Aironet 350 series (model AIR-PCM352) in that it won't connect to my wireless network, and I can't get it to do any sort of configuration. All I can get it to do is see the networks in range and some information about them (encrypted or not, signal strength...). When I try to connect to my wireless, it'll give me the window to input my 128 bit WEP key, and after I put that in, it looks like it's connecting, but nothing happens. After about 20 seconds, the card returns to the state it was in before I selected a network for it in the first place, and I have no connection. 

I have included the following output from the terminal to help you help me:

With the card installed:
```
shadowimmage@shadowimmage:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:0C:9E:F6   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=1/100  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:1  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:105   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:0C:9E:F6   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=1/100  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:1  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:105   Missed beacon:0

```

Without the card installed:
```
shadowimmage@shadowimmage:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

```

Looking at those, does this mean that Linux is registering the card as two network interfaces? And if so, then why? and how do I fix that? 

I also got this: 
With the card installed:
```
shadowimmage@shadowimmage:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:09:6B:D0:CE:E3  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:6bff:fed0:cee3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18615 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8030119 (7.6 MiB)  TX bytes:453430 (442.8 KiB)

eth1      Link encap:Ethernet  HWaddr 00:0F:F8:4F:86:A5  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:6279 dropped:0 overruns:0 frame:6279
          TX packets:2 errors:1 dropped:0 overruns:0 carrier:1
          collisions:22 txqueuelen:1000 
          RX bytes:332 (332.0 b)  TX bytes:144 (144.0 b)
          Interrupt:3 Base address:0x4100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:622283 (607.6 KiB)  TX bytes:622283 (607.6 KiB)


```

And without the card installed:
```
shadowimmage@shadowimmage:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:09:6B:D0:CE:E3  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:6bff:fed0:cee3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18697 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8056299 (7.6 MiB)  TX bytes:453430 (442.8 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:622283 (607.6 KiB)  TX bytes:622283 (607.6 KiB)


```

---

### Post by shadowimmage on 2007-06-30
bump...

---

### Post by chili555 on 2007-06-30
Network Manager, where you are trying to enter the connection details, is designed to **not** connect wirelessly if a wired connection is available. Please check here: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

However, you have a wired connection:```
eth0      Link encap:Ethernet  HWaddr 00:09:6B:D0:CE:E3  
          inet addr:192.168.1.4 
```I would detach the cable, issue a terminal command *sudo ifdown eth0* and try the wireless again.

---

### Post by shadowimmage on 2007-06-30
I have tried using the card without the network cable plugged in. It does the same thing, which is nothing... apparently. 
I only have the network cable in right now because I'm home, but I'd like not to be tethered to my network switch if at all possible.

---

### Post by Bugrit on 2007-08-18
I hope you have cured this by now , but just on the off chance:

I nearly went mad with this one also, turned out a clue from from [COLOR="Blue"][PRGSDW]("http://ubuntuforums.org/showthread.php?t=398144&highlight=Network-Manager")[/COLOR] solved it for me.
Everthing seemed to be working, but no DHCP request would be satisfied.
Everything looked like it should work.
Finally I took the advice from the aforementioned post and removed the network manager using 
**sudo apt-get remove network-manager**
I rebooted and it was all working happily!
Sad loss of about 4 hours of my life trying all the other options tho :(

Thanks to all the posters.
My setup..an old IBM Thinkpad T30 using the Cisco Aironet 350 series wireless mini-PCI adapter.
Ubuntu Desktop 7.04.

Buggy

---

