---
title: "internet cuts out"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by chap the hat on 2008-10-14
hello there. I am quite new to linux so this may be a stupid fault. I do hope so? I am running 8.04 and I have got it to recognise a wi-fi adapter and conect to the internet. easy and fast. love it.

but after about 5mins quite random in actual length, firefox just stops working. the little blue bars that show conection drop to nothing but if you go and look at the network conection it still shows i am connected to my router and that i have an IP and conection speed and everything. It just will not go to any page what so ever.

It's so bad that I am having to right this in windows because i can't stay online for long enough in xubuntu.

If anyone can either help me out with this problem or explain to me what info i would need to give to get help, it would be very welcome.

thanks.

---

### Post by thomax on 2008-10-14
Post the output of iwconfig and ifconfig when your wifi is working AND when it's down.

When your wifi is down, try to ping your router.

---

### Post by chap the hat on 2008-10-14
thanks for replying... here is the iwconfig.

**_whilst working_**

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"BTVOYAGER2110-87"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:16:E3:E7:55:87   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=59/64  Signal level=60/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**_and not working_**

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"BTVOYAGER2110-87"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:16:E3:E7:55:87   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=56/64  Signal level=49/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chap the hat on 2008-10-14
and the ifconfig...

**_whilst working_**

eth0      Link encap:Ethernet  HWaddr 00:0c:76:69:a3:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3600 (3.5 KB)  TX bytes:3600 (3.5 KB)

wlan1     Link encap:Ethernet  HWaddr 00:0f:b5:d0:95:5f  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fed0:955f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1304 (1.2 KB)  TX bytes:6734 (6.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0F-B5-D0-95-5F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**_and not working_**

eth0      Link encap:Ethernet  HWaddr 00:0c:76:69:a3:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24639 (24.0 KB)  TX bytes:24639 (24.0 KB)

wlan1     Link encap:Ethernet  HWaddr 00:0f:b5:d0:95:5f  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fed0:955f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2423 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2828390 (2.6 MB)  TX bytes:321493 (313.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0F-B5-D0-95-5F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by chap the hat on 2008-10-14
it looks to me... and I know nothing that it is doing more work when not working so surely it sould be working?

but still every time I try to access a new web page it gives this error...

[www.ubuntu.com](www.ubuntu.com) could not be found. Please check the name and try again.
The browser could not find the host server for the provided address.

Did you make a mistake when typing the domain?
 (e.g. "ww.mozilla.org" instead of "www.mozilla.org")

Are you certain this domain address exists?  Its registration may have expired.

Are you unable to browse other sites?  Check your network connection and DNS server settings.

Is your computer or network protected by a firewall or proxy?  Incorrect settings can interfere with Web browsing.

---

### Post by hyper_ch on 2008-10-14
the problem is the rate gets set at 1mb/s run that

```

sudo iwconfig wlan1 rate 54M; sudo /etc/init.d/network restart

```

and I'd appreciate if you could post your wireless card model here also and confirm you get the same thing:  [https://bugs.launchpad.net/ubuntu/+bug/282053](https://bugs.launchpad.net/ubuntu/+bug/282053)

---

### Post by chap the hat on 2008-10-14
that makes sense because when I look at the conection information it says 1mb/s and my connection is faster than that.

As fot the card I am actually using usb addapters... I have tryed three so far. 1 does not work at all but the other two, the netgear wg111v2 and the cnet cwd-854 both experience the same problem.

---

### Post by hyper_ch on 2008-10-14
please also add your info to the bug report :)

---

### Post by chap the hat on 2008-10-14
thanks hyper_ch for your help... have filled out the bug report.

does this mean that this problem can't be fixed just now or should i try typing those comands in your previous message in terminal?

---

### Post by hyper_ch on 2008-10-14
when it happens just run those two commands... it happens at irregular intervals... I'd say it's a bug and it might get fixed (eventually)

---

