---
title: "wireless wrt54g help"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by ortwein on 2008-01-23
Here is my problem:

I purchased a linksys wrt54g v8 wireless router this morning, but the software that it comes with is Windows only.  So I didn't install anything.   I can now connect to the internet through my laptop, but my desktop connection no longer works.  Also, I'm positive that I hooked everything up right...followed the instructions on the box to the letter.

What gives?

By the way, I'm a newbie to linux...so simple steps are a big help.

Mark

---

### Post by chewearn on 2008-01-23
You can configure the linksys router via web interface; type the following into your web browser address bar: 192.168.1.1 (I think this is the default IP for linksys router,  but I could be wrong; if it doesn't bring up the web interface, check the user's manual).

.

---

### Post by ortwein on 2008-01-24
I confirmed that that was the correct IP for my router, and I tried typing it in to my browser, but it just sits there and tells me it couldn't connect.   Any other suggestions?

Mark

---

### Post by Zack McCool on 2008-01-24
Is your PC on the 192.168.1.x subnet?  If not, it won't be able to get there, as it doesn't know how to route to that subnet.

If that is the case, temporarily change the IP on your PC to 192.168.1.100 (or whatever), and then try the web interface again.  It will ask for a login.  I believe the default is no ID, password is admin.

I have had the wrt54g for a few years, and never installed the windows software.  It is a very good router.

---

### Post by ortwein on 2008-01-24
I'll give it a try and report back...thanks

---

### Post by ortwein on 2008-01-24
Well, somehow I managed to access my linksys router...but now what?  My laptop runs perfectly on the signal, but my poor desktop can't do anything (including access my modems ip)

Mark

---

### Post by chewearn on 2008-01-24
-
Ok, now you can access the linksys configuration, there is no need for the Windows install disc; so some info are needed to understand your issue:

1. what IP subnet are you using for your network?
2. are you using DHCP or static IP assignments?
3. is it wired, or wireless connections?
4. can you ping devices in your network?

-

---

### Post by DapperMe17 on 2008-01-25
Just to chime in here...I've also been using the WRT54G V8, as you have.

It works like a charm, with Windows & Ubuntu. 

Perhaps your software firewall is blocking access, in Windows? 

Reset the router, which gives you full, unencrypted access. Then, both machines should "see" your default "linksys" network. 

You don't use the CD at all, with either Windows or Linux. Once your on the internet with both machines, access the router by typing 192.168.1.1 in your browser address bar. You'll see your login page, then type "admin" in the password field. This will get you in the router, where you can customize your settings. Be sure to mirror those settings in both of your machines wireless connection settings. (Windows, turn off built-in Microsoft firewall if your using a third-party software firewall).

---

### Post by ortwein on 2008-01-25
> **AstalaVista said:**
> -
Ok, now you can access the linksys configuration, there is no need for the Windows install disc; so some info are needed to understand your issue:

1. what IP subnet are you using for your network?
2. are you using DHCP or static IP assignments?
3. is it wired, or wireless connections?
4. can you ping devices in your network?

-

1.  I don't know how to check this; I'm still quite new to linux.
2.  DHC P
3.  The wireless router is connect via a cable to my desktop computer, and sends a wireless signal to my laptop.
4.  I know how to ping in windows...but not in linux *blush*

---

### Post by ortwein on 2008-01-25
> **DapperMe17 said:**
> Just to chime in here...I've also been using the WRT54G V8, as you have.

It works like a charm, with Windows & Ubuntu. 

Perhaps your software firewall is blocking access, in Windows? 

Reset the router, which gives you full, unencrypted access. Then, both machines should "see" your default "linksys" network. 

You don't use the CD at all, with either Windows or Linux. Once your on the internet with both machines, access the router by typing 192.168.1.1 in your browser address bar. You'll see your login page, then type "admin" in the password field. This will get you in the router, where you can customize your settings. Be sure to mirror those settings in both of your machines wireless connection settings. (Windows, turn off built-in Microsoft firewall if your using a third-party software firewall).

Thanks for the response.  I'm not running windows at all, just kubuntu.  How do I alter my network connections so the "mirror" each other?  If you give me some commands, I can paste results here...if that will help you evaluate my situation.

---

### Post by bwtranch on 2008-01-25
It would be helpful to post the output of ifconfig, also lsusb and lspci . I don't remember which one you have. But, anyway, yeah, we need some output of your config to help.

---

### Post by mozetti on 2008-01-25
You have multiple LAN ports on the back of the WRT54G

1 WAN port - this is your connection to the internet. If you have a cable or DSL modem, then this should be plugged into the WAN port.

4 LAN ports - this is how you connect computers/devices to the router. Your desktop computer should be plugged into one of these ports.

Once that's set, go to System-Admin-Networking and set the properties for the connection. Since you're using DHCP, just set it to DHCP and you should have a connection to the router, and therefore the internet.

Here are some commands for the terminal (command line) that are useful:

To see your network settings: ```
 ifconfig - this shows the network settings of all your network connections.

ifconfig eth0 - this shows the network settings of the connection "eth0", which is usually what your first (or only) network connection is named.
```

To ping, it's the same as windows:```
 ping 192.168.1.1
```
However, unlike windows, in Linux the "ping" command continues until you stop it. To do that, just press "control-C".

---

### Post by ortwein on 2008-01-25
Hope this helps.


harpo@harpo:~$** ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:14:BF:5F:40:DE
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::214:bfff:fe5f:40de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2580475 errors:2 dropped:0 overruns:0 frame:3
          TX packets:2495750 errors:10 dropped:0 overruns:0 carrier:10
          collisions:0 txqueuelen:1000
          RX bytes:2171884920 (2.0 GB)  TX bytes:1248614456 (1.1 GB)
          Interrupt:20 Base address:0xde00

eth1      Link encap:Ethernet  HWaddr 00:13:20:76:FB:83
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3913 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4122768 (3.9 MB)  TX bytes:378671 (369.7 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1965092 (1.8 MB)  TX bytes:1965092 (1.8 MB)

harpo@harpo:~$** lsusb**
Bus 004 Device 019: ID 1516:8628
Bus 004 Device 004: ID 046d:08ce Logitech, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 413c:3200 Dell Computer Corp.
Bus 001 Device 003: ID 413c:2005 Dell Computer Corp.
Bus 001 Device 001: ID 0000:0000

harpo@harpo:~$** lspci**
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 Display controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
01:01.0 Communication controller: Conexant HSF 56k Data/Fax Modem
01:02.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
harpo@harpo:~$

 Link encap:Ethernet  HWaddr 00:14:BF:5F:40:DE
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::214:bfff:fe5f:40de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2580490 errors:2 dropped:0 overruns:0 frame:3
          TX packets:2495822 errors:10 dropped:0 overruns:0 carrier:10
          collisions:0 txqueuelen:1000
          RX bytes:2171886324 (2.0 GB)  TX bytes:1248617480 (1.1 GB)
          Interrupt:20 Base address:0xde00

---

### Post by chewearn on 2008-01-26
Your ifconfig showed eth0 having IP address of 192.168.2.4.  This is not the same subnet as your router, which is in 192.168.1.1.  There are two solutions I can propose:

1. re-check your router DHCP assignment; ubuntu is configured to use DHCP by default, so it should already be OK, unless you have fiddled with it and change it to static IP

2. just use static IP address; then go to System > Administration > Network; select eth0, click Properties, specify the static IP of 192.168.1.x (x is a number from 2 to 254, that is not used by any other devices in your network).  Notice it's 192.168.**1**.x and not 192.168.**2**.x, which you currently have.

---

