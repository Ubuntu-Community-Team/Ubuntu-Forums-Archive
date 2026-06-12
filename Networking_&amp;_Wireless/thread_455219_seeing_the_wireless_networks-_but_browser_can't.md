---
title: "seeing the wireless networks- but browser can't"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by dsonyay on 2007-05-26
Ok,
After hours of tweaking.  I can now see wireless networks in my neighborhood.  A couple are secure and 2 are not.  I'm getting the icon in the toolbar with the bars, and when I select a wireless network some of the bars light up.  Even when they do my browser will not go to a website.
Under the broser's preferences (Firefox mozilla) I'm selecting auto detect.  Why the heck can't this work?

I've updated the correct drivers from a thread on this forum, installed them, rebooted and that's how I got my wireless card to work.  Now I see signals, but cannot get to websites.

Also-- sometimes, my signal bar shows up, sometimes it goes away, I can't figure out how to get it on the task bar.

Should I be using roam?  Or should I manually pick a strong signal and go that route??

Man this is so frustrating.  I've been working on getting Ubuntu up and running for over 24 hours now.

---

### Post by RudolfMDLT on 2007-05-26
Hi there,

Try to connect to a network, wait about a minute and then open up the terminal and type **ifconfig**, press enter. now type **iwconfig** and press enter and finally type in **route**. please paste all outputs here. I'm betting the unsecured networks don't use DHCP for security reasons.

Cheers,

Rudolf

---

### Post by dsonyay on 2007-05-26
> **RudolfMDLT said:**
> Hi there,

Try to connect to a network, wait about a minute and then open up the terminal and type **ifconfig**, press enter. now type **iwconfig** and press enter and finally type in **route**. please paste all outputs here. I'm betting the unsecured networks don't use DHCP for security reasons.

Cheers,

Rudolf

Thanks!
Here's what I got.  see attached[ATTACH]33530[/ATTACH]

[ATTACH]33531[/ATTACH]

[ATTACH]33532[/ATTACH]

---

### Post by dsonyay on 2007-05-26
oops try again:
ifconfig-
eth0      Link encap:Ethernet  HWaddr 00:1B:FC:44:AB:AE  
          inet6 addr: fe80::21b:fcff:fe44:abae/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:126 errors:0 dropped:173 overruns:0 frame:0
          TX packets:3378 errors:0 dropped:13 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38370 (37.4 KiB)  TX bytes:146983 (143.5 KiB)
          Interrupt:5 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:19:B9:74:A7:EC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:44671 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3149860 (3.0 MiB)  TX bytes:24290 (23.7 KiB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:970 errors:0 dropped:0 overruns:0 frame:0
          TX packets:970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:71564 (69.8 KiB)  TX bytes:71564 (69.8 KiB)

iwconfig-
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


route-
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

---

### Post by RudolfMDLT on 2007-05-26
Okay;

iwconfig tells me that at least the card seems to working

ifconfig and route tell me that no IP-addresses have been assigned to your card. In order to communicate you need 3 things: 1) an IP address 2) netmask 3) gateway.

The networks you are connecting to don't seem to be dishing out IP addresses. are they networks you have worked on before or are you just trying to get onto some random network?

regards,

rudolf

---

### Post by dsonyay on 2007-05-26
> **RudolfMDLT said:**
> Okay;

ifconfig and route tell me that no IP-addresses have been assigned to your card. In order to communicate you need 3 things: 1) an IP address 2) netmask 3) gateway.

The networks you are connecting to don't seem to be dishing out IP addresses. are they networks you have worked on before or are you just trying to get onto some random network?

regards,

rudolf

I'm trying to access local wireless networks that are not secure- (because I did these networks on my XP OS)
and I'm trying to get the cable internet from my ISP (Charter.net) to run in my laptop.
My charter connection comes out of the wall, into a webstar modem, then a ethernet cable goes from the modem to the PC ethernet port in back.  I have no IP addreses assigned on my PC.  Everything is auto-detect (XP-PRO SP2 w/ WinExplorer broweser).  But when I plug the same cable into the laptop, nothing.  NADA.

David

---

### Post by RudolfMDLT on 2007-05-26
very weird.

Okay, plug in the network cable  and,

try **sudo /etc/init.d/networking restart** and see if you can find text that says the eth0 is bound to IP  xxx.xxx.xxx.xxx.

If still nothing, boot into windows, connect to the web. click start, run. In run enter cmd. in Command, enter ipconfig. copy this info down on pen and paper and boot in to Ubuntu. leftclick on the network icon and click manual config. double click on the wired connection and enter the info from windows. apply the settings and give it a couple of seconds to apply the changes. see if it works?

---

### Post by dsonyay on 2007-05-26
[B]here's the results:
david@ubuntu:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                      RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 5756
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:19:b9:74:a7:ec
Sending on   LPF/eth1/00:19:b9:74:a7:ec
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:19:b9:74:a7:ec
Sending on   LPF/eth1/00:19:b9:74:a7:ec
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                     [ OK ]
david@ubuntu:~$ [/B]


Here's my results from ipconfig in XP:

[B]Connection Specific DNS suffix: 
IP address:  71.81.60.244
Subnet mask: 255.255.252.0
Default Gateway:  71.81.60.1[/B]

Thanks a bunch
David

---

### Post by RudolfMDLT on 2007-05-26
> No DHCPOFFERS received.
No working leases in persistent database - sleeping.

 That part states pretty obvious that DHCP client isn't receiving anything.

is there a cable plugged into the back of the pc? when you plug it in, does a light lite up on the router and the pc?

I'm going to try and do things the old school way:

open up the termminal and type

**sudo cp /etc/network/interfaces /etc/network/interfaces~**

this creates a backup of your current network config.

now, pres alt+F2 and type in **gksu gedit /etc/network/interfaces** and press enter.

in the open document, find this line:

> auto eth1
iface eth1 inet dhcp


directly underneath it paste:

> auto eth1:0
iface eth1:0 inet static
address 71.81.60.241
netmask 255.255.255.0
gateway 71.81.60.1


this binds a 2nd IP to the card that points Ubuntu to your router. save the file and then exit. in the terminal type:

**sudo /etc/init.d/networking restart**

and then **ifconfig**

you should see a new adapter eth1:0.

now type in **route** and give it a minute

you should see 71.81.60.1 as a route.

now open up fire fox, and there should be internet. If you still don't have internet then please post back but beyond this my knowledge becomes sketchy. redo the steps and keep an eye out for any errors.

there are some routers that don't conform to standards that i have heard about on the forums not talking to Ubuntu/Linux machines but they are very few.

I'm off to bed - But I'll be up again in about 6 hours to see if you got sorted( and get some work done! :) )!

goodluck,

Rudolf

PS: the above step will only work with a wired connection - with wireless it needs more details!

---

### Post by dsonyay on 2007-05-26
Before I do that I thought I would reload the nic card from Broadcom.com
On my laptop I have a BCM4401-B0 card.
(From my Device manager window.
I went to broadcom's website and downloaded the Linox driver for called linox-1.00g.zip

HOW DO I relaod the driver?
I placed the file in \TMP
then I extracted the files into \tmp\linux

In the folder there's a .tar.gz file and a src.rpm file.

What do I do??

David

I'd prefer to try this first- if necessary
David

---

### Post by RudolfMDLT on 2007-05-27
I don't want to go playing with drivers as I believe that it works. You can see the other networks can't you?

The problem I believe is getting Ubuntu and the DHCP server on your networking talking to each other. Drivers may sort this out, but the fact that neither the Wireless nor the Wired gets any DHCP addresses is worrisome. Thats why I would first like to check if Fixed IP's work.

If you still want to install a driver - I'm the wrong guy to help unfortunately as I have never had to do this. I have asked for extra help in the forum on this issue. I'll keep checking back here to see whats doing on and If no one has posted  then I'll see whether I can't get something done for you.

---

### Post by RudolfMDLT on 2007-05-27
Back again... downloaded the driver and did some searching around! 

found this: [http://ubuntuforums.org/showthread.php?t=449966&highlight=BCM4401](http://ubuntuforums.org/showthread.php?t=449966&highlight=BCM4401), very unfair! :)

anyway, I tried compiling the driver -  didn't work.  I get the following error:

> rudolf@rh:~/Desktop/linux/b44-1.00g$ sudo make
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/rudolf/Desktop/linux/b44-1.00g modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/rudolf/Desktop/linux/b44-1.00g/b44.o
/home/rudolf/Desktop/linux/b44-1.00g/b44.c:10:26: error: linux/config.h: No such file or directory
/home/rudolf/Desktop/linux/b44-1.00g/b44.c: In function ‘b44_open’:
/home/rudolf/Desktop/linux/b44-1.00g/b44.c:1546: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/rudolf/Desktop/linux/b44-1.00g/b44.c: In function ‘b44_resume’:
/home/rudolf/Desktop/linux/b44-1.00g/b44.c:2563: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/rudolf/Desktop/linux/b44-1.00g/b44.o] Error 1
make[1]: *** [_module_/home/rudolf/Desktop/linux/b44-1.00g] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2


what I would like you to doe is  to please open up the terminal and enter the following command:

**iwlist scan**

an see what wireless networks you see.
 
If you don't get any - try moving closer. If still nothing then it's a driver. If however you do get the AP that  you where looking for:

1) leftclick the network icon top right of the screen, click manual config.

2) double click on your wireless connection

3)click the dropdown and select  your AP you want to connect to. set the connection to use DHCP and not roaming.

4) click ok, make sure the connection is ticked, and wait for Ubuntu to apply the settings, click okay again to exit the app and wait another 30 sec's for good messure. see if it has worked?

**NO?**

5) do steps 1-3

6) set the connection to use MANUAL config and not DHCP 

7) enter the following info:

address: [COLOR="Red"]71.81.60.241[/COLOR]
netmask: [COLOR="Red"]255.255.255.0[/COLOR]
gateway: [COLOR="Red"]71.81.60.1[/COLOR]

8 ) click okay, click okay. wait 30secs.  open up the terminal and type in ifconfig.
Somewhere in the list you MUST find somtheing with the address that you have given it.

9) Open up the broweser and see if you can surf the web?

Still not working?

**Trouble shooting:**

1) is the wireless turned on?
 in a previous post, the out put of sudo /etc/init.d/networking restart only showed one connection?
if not - redo all steps

2) if it is turned on
open up  your browser and type in 71.81.60.1. this should present you with a login in screen to your router.   if this works then ethernet works but internet doesn't.

3) enter the following command in the terminal with variations on the theme broadcom and see what it outputs.
i) lsmod |grep broad
ii) lsmod |grep BCM4401 
iii) lsmod |grep bcm

post back with all results please! thats why I want your wired connection to work first so that when we need to trouble shoot on the Ubuntu Wireless side you can copy and paste directly into your web browser.

Best of luck,

Rudolf

---

### Post by RudolfMDLT on 2007-05-27
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

the above looks very promising! :)

---

### Post by dsonyay on 2007-06-02
ok, sorry to be so long in replying but I was working offshore and couldn't use the laptop.
I figured out the problem with connecting to the internet using my cable modem.  Before I plug the the ethernet cable into the Dell laptop, I have to reboot the modem (power it off then on again).  Apparantly when it's connected to my PC, and I unplug it from there into my laptop, the modem is trying to see my PC, but can't.  So when I power it off/on, everything works fine.

Bad news is that I had to load XP pro as my OS becuase I was running out of time before going back to work again and I wanted a working laptop to communicate with the family.

Next chance I get I'll likely retry Ubuntu.

What a bummer- wish I could have figured that out before giving up and going back to XP.  I was having the same problems with XP seeing my cable modem, until we figured that out.  Charter tech support actually works ;)

David

---

