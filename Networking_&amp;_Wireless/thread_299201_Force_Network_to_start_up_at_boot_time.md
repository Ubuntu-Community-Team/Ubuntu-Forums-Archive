---
title: "Force Network to start up at boot time"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by Yeuclid on 2006-11-13
After about a week I finally got my wireless USB adapter to work on Ubuntu 6.10, after reverting to Wlan-ng and the standard Prism2 drivers.

Only problem is that I have to enable the connection each time after a boot to get it to connect.

Is there any way I can put a command in the start up stream somewhere to force this to happen automatically, i.e. to make Wlan0 the default connection and kick off the wireless connection to my router.

I'm sure I've seen other posts about this on here.

---

### Post by jamesr on 2006-11-13
To enable the connection what are you having to do. 
Goto Terminal```
sudo ifconfig
sudo iwconfig
```and post the outputs

---

### Post by ironopolis on 2006-11-14
Hi,
Sorry to jump in on a thread but i'm having the same problem with my wired connection, eth1.

I have to activate eth1 every time I start up, which is getting a bit frustrating.
Does the 

sudo ifconfig
sudo iwconfig

work with my problem as well.

I am new Ubuntu so any help will be greatly appreaciated.

Thanks.

ironopolis

---

### Post by Yeuclid on 2006-11-14
> **jamesr said:**
> To enable the connection what are you having to do. 
Goto Terminal```
sudo ifconfig
sudo iwconfig
```and post the outputs

Here are the details you requested:

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:D0:09:FE:13:CA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5276 (5.1 KiB)  TX bytes:5276 (5.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0A:E9:0B:D7:DE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1474 (1.4 KiB)  TX bytes:1720 (1.6 KiB)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

sit0      no wireless extensions.



AFTER ENABLING WIRELESS WITH NETWORK MANAGER: 


$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:D0:09:FE:13:CA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5276 (5.1 KiB)  TX bytes:5276 (5.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0A:E9:0B:D7:DE  
          inet addr:10.0.0.149  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e9ff:fe0b:d7de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4752 (4.6 KiB)  TX bytes:8078 (7.8 KiB)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11-b  ESSID:"SpeedTouchB2609E"  Nickname:"SpeedTouchB2609E"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:F5:A1:43:29   
          Bit Rate:11 Mb/s   Tx-Power:2346 dBm   
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Link Quality=29/92  Signal level=-59 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


To get it to work I have to disable and then re-enable the connection through Network Manager.

It would be much more convenient if it worked without this manual intervention

Maybe I need a script file to do this, although it seems a bit of an overhead

---

### Post by jamesr on 2006-11-15
To Ironopolis
Yes but only sudo ifconfig

---

### Post by jamesr on 2006-11-15
To Yeuclid,

In a terminal window try```
sudo ifup wlan0
```because a script might the best way but we need to know why and where it fails.

---

### Post by Yeuclid on 2006-11-15
I did that, and it just informed me that Wlan0 was already configured.

It knows it is there, but just seems to need this manual kickstart which I'd like to avoid.

Once it's up and running, it's great

The more I use it, the more I like Ubuntu. It takes me back to my days as a Mainframe Systems Programmer back in the 70s.... ahhh   nostalgia, when things didn't always work as they should.

---

### Post by jamesr on 2006-11-15
I know the feeling well but my history was minis PDP8s etc.

I really meant you to try upif before you ran the wireless manager.

---

### Post by dmizer on 2006-11-16
post the contents of dmesg (please contain it in [code] tags so the post doesn't get so long), and we'll see if there's an error causing it to fail.

---

### Post by Yeuclid on 2006-11-19
What is the Wireless Manager? I only use the Networking utility in Administration, and Wifi-Radar to check the router.

---

### Post by FrodoB on 2006-11-19
A previous post was on the right track.  Run these commands:

sudo ifdown wlan0

then bring it back up:

sudo ifup wlan0;

Hopefully you may see what the issue is.

Also dmesg as dmizer asked.

---

