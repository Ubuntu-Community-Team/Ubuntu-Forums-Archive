---
title: "No network connection in Gutsy"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by zoqaeski on 2007-12-30
I've got a fresh install of Gutsy on a brand new computer that&#8217;s never had any other OS installed on it. For some reason, the network simply isn&#8217;t connecting 99% of the time; it didn&#8217;t connect on the LiveCD, and it only occasionally connects now that it&#8217;s been installed. It&#8217;s supposed to be receiving a DHCP address from a Windows server, but doesn&#8217;t seem to be. On the off chance that I do get a connection, it is very slow and doesn&#8217;t survive a reboot.
As I&#8217;ve been using Ubuntu in one form or another on a different computer for a couple of years now, but never had any real problems like this come up, I don&#8217;t know how to diagnose the problem correctly, let alone fix it. Can anyone help? I&#8217;ve searched the forums for answers and can&#8217;t find any, so I&#8217;m completely stumped.

EDIT: The network connection is ethernet, and the internet connection is through an ADSL router.

---

### Post by alex1996arm on 2007-12-30
you should mention what the connection is so we can diagnose.
ex:wireless,ethernet modem,bluetooth

---

### Post by zoqaeski on 2007-12-30
More information:
The network connection is wired CAT5e, and the card is an in-built PCI Gigabyte motherboard network connection.

---

### Post by alex1996arm on 2007-12-31
maybe there is a proprietary driver.
to get it go to 
system>Administration>restricted driver manager
if it doesn't work go to system>Administration>software sources>tick all the boxes\


                                             good luck

---

### Post by zoqaeski on 2007-12-31
I’m starting to think that somehow Gutsy has bugs here, because last night we formatted and started again, installed 7.04, and the network worked fine. After that, we then went through and did a manual upgrade and it did that, but now the network doesn’t work!
And the restricted driver manager doesn’t work because the kernel restricted packages aren’t installed, and they can’t be installed without a network connection.
The really odd bit about this is that my main computer, the one which I’m typing this on, has no problems connecting to the network, and yet it’s running Gutsy and has been upgraded over the years as newer distros have come out.

---

### Post by Predator[23rd] on 2007-12-31
what does your computer say when you give the "ifconfig" command in a terminal window?

---

### Post by zoqaeski on 2008-01-01
> **'Predator[23rd] said:**
> what does your computer say when you give the "ifconfig" command in a terminal window?
This is the output of (sudo) ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1A:4D:F6:FC:27  
          inet6 addr: fe80::21a:4dff:fef6:fc27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967280 overruns:0 frame:0
          TX packets:0 errors:0 dropped:46 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe000 

eth0:avah Link encap:Ethernet  HWaddr 00:1A:4D:F6:FC:27  
          inet addr:169.254.8.74  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:784 (784.0 b)  TX bytes:784 (784.0 b)
```Judging from that (if I read it correctly), and the System Monitor network graphs, the computer isn’t sending or receiving any bytes for some reason. The cause may be a proprietary driver, however the network worked on 7.04 without any issues that I’m getting in this version.

EDIT: I dunno if this will help, but just for comparison, this is what my main computer (the one that works) outputs from ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:13:72:D8:CB:70  
          inet addr:192.168.46.15  Bcast:192.168.46.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:fed8:cb70/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:895 errors:0 dropped:0 overruns:0 frame:0
          TX packets:777 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:716872 (700.0 KB)  TX bytes:75404 (73.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5428 (5.3 KB)  TX bytes:5428 (5.3 KB)
```

---

### Post by alex1996arm on 2008-01-02
i like the *.4 versions better:)

---

### Post by Predator[23rd] on 2008-01-02
check your */etc/network/interfaces* file for

[I]auto eth0
iface eth0 inet dhcp
[/I]

looks like your eth0 is not receiving (maybe because it is not asking) DHCP informations. the above entry should solve that. restart your network after adding these two lines (hope they are missing ...) with **sudo /etc/init.d/networking restart**

---

