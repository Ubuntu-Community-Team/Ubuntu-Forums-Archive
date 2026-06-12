---
title: "network troubles"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by 7Sasha on 2008-10-31
network card was defined as &#1077;th0.  ifconfig says

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
...
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Explain me what to write and where? Totally new to ubuntu
--

I've tried to connect with system -> administration -> network
choosing automatic configuration(dhcp) and static ip.
none worked

Now i'm sitting under windows from another comp . ipconfig as follows:

[IMG]http://img222.imageshack.us/img222/9049/84048312wd2.png[/IMG]
( [http://img222.imageshack.us/img222/9049/84048312wd2.png](http://img222.imageshack.us/img222/9049/84048312wd2.png) )

help please

---

### Post by 7Sasha on 2008-11-01
any suggestions? please

---

### Post by vitorgatti on 2008-11-01
Welcome to Ubuntu :KS

Please paste what fully shows when you execute "ifconfig".
As I can see you're using a wireless connection, so paste what shows with the command "iwconfig".

And try to just click once at the two-computers-icon top-right at screen, and see if your wifi connection shows up.

Good luck

---

### Post by 7Sasha on 2008-11-01
thanks for reply.
I'm using laptop to access the internet now. Yhe computer I'm trying to set up has wired connection.

> eth0      Link encap:Ethernet  HWaddr 00:13:8f:91:3b:8c  
          inet6 addr: fe80::213:8fff:fe91:3b8c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:300 (300.0 B)  TX bytes:6992 (6.8 KB)
          Interrupt:21 Base address:0xd800 

eth0:avahi Link encap:Ethernet  HWaddr 00:13:8f:91:3b:8c  
          inet addr:169.254.6.141  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:950 errors:0 dropped:0 overruns:0 frame:0
          TX packets:950 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47500 (46.3 KB)  TX bytes:47500 (46.3 KB)

with enabled roaming:
[IMG]http://img523.imageshack.us/img523/1117/screenshotconnectioninfso0.png[/IMG]
( [http://img523.imageshack.us/img523/1117/screenshotconnectioninfso0.png](http://img523.imageshack.us/img523/1117/screenshotconnectioninfso0.png) )

---

### Post by vitorgatti on 2008-11-01
Are you using a router to distribute internet?
There should not be any problems for you to connect using cables.
Just connect the cable as you would do in Windows.
Ubuntu recognized your Ethernet Adaptor, so it's really weird if it can't just get a DHCP IP...

---

