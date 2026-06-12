---
title: "how to remove invalid driver"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by GolfGeek on 2007-01-06
I have been following a thread (201902) to install the bcm4306 wireless diver in my compaq presario 2100. I got to the point where the code said

"sudo ndiswrapper -i /bin/bcmwl5.inf

The first time I tried this i was using a fifferent folder and the .sys file was not there. At this point, when I type the command, I am told it is already installed. So I proceed to the code

"ndiswrapper -l"
and see the bcmwl5 listed with "invalid driver" next to it. Si I went back and entered

sudo ndiswrapper -e bcmwl5

I get a prompt but when I try to reinstall the driver, I get the message that it is already installed. Not sure how to proceed next.

When I run ifconfig I get the following:
eth0      Link encap:Ethernet  HWaddr 00:0F:20:20:05:82  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:20ff:fe20:582/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:429 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:341562 (333.5 KiB)  TX bytes:49908 (48.7 KiB)
          Interrupt:11 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

---

### Post by spd106 on 2007-01-06
If you can't remove the driver within ndiswrapper, then remove the whole of ndiswrapper and reinstall it, i.e. back in the [howto]("http://www.ubuntuforums.org/showthread.php?t=201902"), go to problem 2.

---

