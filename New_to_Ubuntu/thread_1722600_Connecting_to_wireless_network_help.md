---
title: "Connecting to wireless network help"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by pandaEater on 2011-04-05
I'm not able to see(or connect) to my wireless network.
I'm running Ubuntu 10.04 on an HP pavilion dv5
Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

What I've tried so far:

UBUNTU DOCUMENTATION WIRELESS TROUBLESHOOTING
Confirmed my device was turned on

Check for device recognition
Open a Terminal (Applications &#8594; Accessories &#8594; Terminal) and type the command: sudo lshw -C network

You should see an output, along with the words "CLAIMED, UNCLAIMED, ENABLED or DISABLED"

**problem: I don't see any of those words so I'm not sure where to go from there

CHECKING FOR DRIVER TO INSTALL
System > Administration > Hardware Drivers

**problem: no proprietary drivers found


Thanks for any help!

---

### Post by xXkanfirXx on 2011-04-05
I'm difficulty with my wireless too. I'm a newb to Ubuntu, and I just installed 10.10 on my lap top today. It's a Dell Latitude D620. My wireless is a Broadcom BCM4312. I'm confused cause I can turn on my wireless card and it will show my wireless network and I can connect to my network but when I try and use firefox or do anything internet related it doesn't work. Anyone dealt with a problem like this?

---

### Post by Razorback on 2011-04-06
xXkanfirXx - that sounds like a DNS problem.  Make sure your DNS servers for your ISP are entered in your wireless setup.

panda there are lots of threads on the broadcom chipsets and what to do.  Here is one of them.


[http://ubuntuforums.org/showthread.php?t=1480524&highlight=BCM4328](http://ubuntuforums.org/showthread.php?t=1480524&highlight=BCM4328)

---

### Post by spik3r on 2011-04-06
Hi I'm having a similar problem. I've just recently installed Ubuntu 10.10 on a toshiba laptop. Sometimes it see's the network and connects fine then after a while the internet stops working. If I then try to disable it and re enable it it doesn't find the network at all.
Ethernet works fine, but I need the wireless to work.
Also having trouble getting Vodafone usb modem to work.

Anyone know how to fix these problems?

~Spik3r

---

### Post by xXkanfirXx on 2011-04-06
> **Razorback said:**
> xXkanfirXx - that sounds like a DNS problem.  Make sure your DNS servers for your ISP are entered in your wireless setup.

panda there are lots of threads on the broadcom chipsets and what to do.  Here is one of them.


[http://ubuntuforums.org/showthread.php?t=1480524&highlight=BCM4328](http://ubuntuforums.org/showthread.php?t=1480524&highlight=BCM4328)
My dns is entered in wireless setup..

---

### Post by josephmills on 2011-04-06
> **xXkanfirXx said:**
> My dns is entered in wireless setup..
Hi there I am ver=y new at this but what happens when you go to your termanial and type ```
rfkill list 
``` is the wlan0 blocked? if so type ```
rfkill unblock
```
hope this helps

---

### Post by pandaEater on 2011-04-06
Well I ended up fixing the problem I was having.  I needed to get internet access using an ethernet cable so I could install all the updates(which hadn't been installed because I wasn't able to connect to the internet). Then I went to system>administration>drivers and activated my wireless card.

---

### Post by xXkanfirXx on 2011-04-06
> **josephmills said:**
> Hi there I am ver=y new at this but what happens when you go to your termanial and type ```
rfkill list 
``` is the wlan0 blocked? if so type ```
rfkill unblock
```hope this helps
It came up saying that its not blocked.. Boy this is mind boggling..

---

### Post by josephmills on 2011-04-06
> **xXkanfirXx said:**
> It came up saying that its not blocked.. Boy this is mind boggling..

have you undated ```
sudo apt-get update
```   and also upgraded too?   ```
sudo apt-get upgrade 
``` then ```
sudo reboot
```

---

### Post by josephmills on 2011-04-06
> **xXkanfirXx said:**
> It came up saying that its not blocked.. Boy this is mind boggling..

hi there again could you post ```
lspci
``````
iwconfig 
``` ```
lspci -vnn | grep 14e4
``` thanks

---

### Post by xXkanfirXx on 2011-04-06
> **josephmills said:**
> hi there again could you post ```
lspci
``````
iwconfig 
``` ```
lspci -vnn | grep 14e4
``` thanks

anthony@anthony-Latitude-D620:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

lspci -vnn | grep 14e4
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)

---

### Post by josephmills on 2011-04-06
ok could you paste ```
ifconfig
``` you can take out the inet addr and hwaddr  we don't need to see that just need to see if the wlan0 is there thanks

---

### Post by xXkanfirXx on 2011-04-06
> **josephmills said:**
> hi there again could you post ```
lspci
``````
iwconfig 
``` ```
lspci -vnn | grep 14e4
``` thanks

> **josephmills said:**
> ok could you paste ```
ifconfig
``` you can take out the inet addr and hwaddr  we don't need to see that just need to see if the wlan0 is there thanks

eth0      Link encap:Ethernet Bcast:74.82.231.255  Mask:255.255.248.0
          inet6 addr: fe80::218:8bff:feac:167a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7034822 (7.0 MB)  TX bytes:723741 (723.7 KB)
          Interrupt:18 

eth1      Link encap:Ethernet Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7dff:fe26:4781/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:3969
          TX packets:11 errors:13 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3037 (3.0 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8768 (8.7 KB)  TX bytes:8768 (8.7 KB)

---

### Post by josephmills on 2011-04-06
ok you don't have the driver installed make sure that you are harrd lined in and follow this video [http://www.youtube.com/watch?v=hAHN-YnmrLw](http://www.youtube.com/watch?v=hAHN-YnmrLw) and yes you need the b43 driver hope this helps

---

### Post by josephmills on 2011-04-06
after you get the driver and restart you should update and upgrade

---

### Post by xXkanfirXx on 2011-04-06
> **josephmills said:**
> after you get the driver and restart you should update and upgrade

Thank you, I'll let you know how it turns out.

---

### Post by xXkanfirXx on 2011-04-06
> **xXkanfirXx said:**
> Thank you, I'll let you know how it turns out.

Well I just watched the video and when I went to additional drivers it shows "Broadcom STA wireless driver", and says its activated and in use. When I went to synaptic package manager it showed that the driver is already installed.

---

