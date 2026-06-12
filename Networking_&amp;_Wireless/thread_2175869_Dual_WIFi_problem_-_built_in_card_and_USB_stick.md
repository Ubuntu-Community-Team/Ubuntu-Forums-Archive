---
title: "Dual WIFi problem - built in card and USB stick"
date: 2013-09-21
forum: Networking &amp; Wireless
---

### Post by bravoelf on 2013-09-21
Hello everyone!

I must to apologize and to say that this thread was originally posted by me at Linux Mint forums, but still I decided to post it here cause of similarity of this distros, and also think this problem may be common egardless of distro type.

So here it is:



I've recently installed Linux Mint(and for a good tradition I'm new to all this linux stuff ^_^ ), and I have a kind of problem.. hmm.. not exactly a problem, I will name it an"issue".
According to this issue I have some wifi cards impact. Originally my laptop has an Intel WifiLink 5300 card, but I also want to use my Edimax usb stick(cause of signal strength).
When I connect my Edimax to the laptop, I got this picture: both cards are connected to my router and each one gets it IP address (as I defined in my router's tables). 
Here is some pics: 
1.This is for the WifiLink 5300:
[img]http://s24.postimg.org/oqgjm4omd/pic_1_only_5300_connected.jpg[/img]
2. And this one is for Edimax:
[img]http://s14.postimg.org/5c7jeqwo1/pic_2_both_EDI_and_5300_connected.jpg[/img]

In this situation I have no disturbance at my wifi and everything keeps work fine (kinda weird, but it works)
Now for the interesting cases: when I tried to shut down my WiFiLink 5300 by pushing  laptop's "touch button" it just shut both of them so there was no wifi connection at all(so I turned it on again).
After that I got into "Network Settings" and pushed the "Disconnect"  button at my 5300 and woilla! Only the Edimax stick stayed  to work.
I'll add all the following codes cause I just googled it up a little and thought it may be useful to others.
Here is some "ifconfig" code (within my current settings):
wlan0--->WiFiLink 5300
wlan1--> Edimax usb Card
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:19:cc:de  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1243 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:119465 (119.4 KB)  TX bytes:119465 (119.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6a::83:54  
          inet6 addr: fe80:::6aff:fe6a:8354/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:24220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16629 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23144739 (23.1 MB)  TX bytes:2189614 (2.1 MB)

wlan1     Link encap:Ethernet  HWaddr 00:1f:1f::24:1e  
          inet addr:192.168.1.116  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80:::1fff:fe55:241e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17634854 (17.6 MB)  TX bytes:2397376 (2.3 MB)
```

and this is a Python output:
```
/usr/lib/linuxmint/mintWifi/mintWifi.py
-------------------------
* I. scanning WIFI PCI devices...
  -- Intel Corporation Ultimate N WiFi Link 5300
      ==> PCI ID = 8086:4235
-------------------------
* II. querying ndiswrapper...
-------------------------
* III. querying iwconfig...
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"myhome"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: F8:D1::81:1E:2C   
          Bit Rate=52 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:264  Invalid misc:595   Missed beacon:0

-------------------------
* IV. querying ifconfig...
eth0      Link encap:Ethernet  HWaddr 00:23:8b:19:cc:de  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1243 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:119465 (119.4 KB)  TX bytes:119465 (119.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6a:6a:83:54  
          inet6 addr: fe80:::6aff:fe6a:8354/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:24220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16629 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23144739 (23.1 MB)  TX bytes:2189614 (2.1 MB)

wlan1     Link encap:Ethernet  HWaddr 00:1f:1f:55:24:1e  
          inet addr:192.168.1.116  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80:::1fff:fe55:241e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25045 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21915 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18959733 (18.9 MB)  TX bytes:2536766 (2.5 MB)

-------------------------
* V. querying DHCP...
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd
RTNETLINK answers: File exists
-------------------------
* VI. querying nslookup google.com...
Server:		192.168.1.1
Address:	192.168.1.1#53

```

And this is what I have at:"/etc/network/interfaces"
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```


As for now I would like to ask some questions:

1. What's is going on over there? I mean I Win7 I just push my "touch button" and work only with my Edimax card with no problems at all. On the other hand at Linux Mint I 
    need to disable( I can't even call it "disabling" cause I just disconnected this card, but it's still in active mode) via a "Network Settings" interface. Sounds similar to windows 
    Network Adapter settings. Will disconnect this card (5300) in permanently manner or I'll need to make so each time I log into distro?

2. How to disable/enable this 5300 card permanently(so I be able to use only my Edimax usb card)? How to disable/enable this 5300 card "on the fly"(in case I will want to play with some wifi settings while learning about linux networking ^_^)?

3. What about those intel wif drivers(iwlwifi)? For example in Debian distro they don't have those drivers installed out of the box. But in Mint I just started to surf without installing anything. Still I would like to now, if it is necessarily to make some drivers updates and how to do it(dl and install directly from Intel.com or use some other ways)?

4. Where can I find some useful info for beginners about Linux wifi("conf" files", commands, common description and etc)? I tried to google it, but have found only sites which have partial info or some lame descriptions).

Thanks a lot for your time and will  to help.

---

### Post by Hadaka on 2013-09-21
Hi,sounds like everything is working as it should in linux.
to attempt to answer your 4 questions, I'll do my best with my
limited knowledge.
 #**1.** Linux handles the wireless interface differently than
 #windows. Linux assumes you dont want any wireless when
 #you activate the external "touch button" so it kills
 #usb and internal wireless circuits.
 #**2.** You can disable the 5300 card from loading by simply
 #unchecking the "connect automatically" box (upper left)
 #in the network settings. (wireless icon)
 #**3.** You dont need any driver upgrade, if it works...it works
 #**4.** For info on .conf files, you'll just have to research.
 # for the most part, on wireless type .conf files they are
 #created to allow changes to the drivers parameter variables 
 #to view what paramater variables are used for your 5300
 #card-In terminal enter -> **modinfo iwlwifi**
 #from there you may build a .conf file to change the default parameter settings.
 #example > **sudo gedit /etc/modprobe.d/iwlwifi.conf**
 #enter one line of code.> **options iwlwifi 11n_disable=1**
Have fun !

---

