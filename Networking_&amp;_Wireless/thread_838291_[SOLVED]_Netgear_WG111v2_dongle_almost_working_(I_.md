---
title: "[SOLVED] Netgear WG111v2 dongle almost working (I think), but still need help...."
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by Mr_FixIT on 2008-06-23
Hello,
I have just gone through the process of getting my WG111v2 Netgear wireless dongle connected to my old Dell Inspiron 7000 laptop.  I have followed many various tutorials on these forums.  Most recently I followed along on Kevdog's sticky on how to get the wireless connection connected without the Network Manager GUI.  I have my Netgear router set up with no protection so that I can incrementally get through.  Eventually I will add the encryption.  Following the tutorial for an "open" system, I get to the part where it says:
**A successful connection in all cases will results in this:**
and I get the following response (I just gathered the last few interesting lines)
.
.
.
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received
No working leases in persistent database - sleeping
user@user - laptop: ~$

Something appears to be "sleeping".  How do I wake it up? Is the router sleeping or the laptop/dongle sleeping?:confused:

I have tried another laptop with XP and it connects and recognizes the router.

TIA

---

### Post by prshah on 2008-06-23
> **Mr_FixIT said:**
> 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received
No working leases in persistent database - sleeping
user@user - laptop: ~$



This means that your wireless has been unable to discover a DHCP server to assign it an IP address, because of which it's (the dhclient program) going to sleep.

If your router is serving DHCP addresses fine to WinXP (ie, Windows XP does not use a static IP) then probably you've not connected to the router with the proper password, in case of an encrypted/secured connection (WEP, WAP).

If you would like to setup the IP addresses and related parameters manually, the output of ```
ipconfig /all
``` from Windows XP will guide us in giving you the exact parameters.

---

### Post by Mr_FixIT on 2008-06-24
Sorry, I only get to play with this set-up in the morning before work. 
Update:  I have 2 Dell laptops, and old one (Laptop "A": Dell Inspiron 7000 w/ Ubuntu 8 Linux) and a newer one (Laptop "B": Dell Dimension w/ XP). From "A" I am trying to connect to a Netgear Router with a Netgear WG111v2 wireless dongle.  The Router is setup "open", no password at all required.  Laptop "B" connects without problem at all.  The  output of
"ipconfig /all" for Laptop "B" is: 

Ethernet adapter Wireless Network Connection:

Connection-specific DNS Suffix :
Description : Dell Wireless 1370 WLAN Mini-PCI Card
Physical Address : 00-14-A5-56-C7-60
Dhcp Enableded : Yes
Autoconfiguration Enabled : Yes
IP Address : 192.168.2.2
Subnet Mask : 255.255.255.0
Default Gateway : 192.168.2.1
DHCP Server : 192.168.2.1
DNS Server : 192.168.2.1
Lease Obtained : Tuesday, June 24, 2008 4:03:08 AM
Lease Wxpires : Wednesday, June 25, 2008 4:03:08 AM

C:\Documents and Settings\user>

Hopefully this will give some insight as to how to connect Laptop "A" with Linux.

THanks

---

### Post by prshah on 2008-06-24
> **Mr_FixIT said:**
>   The  output of
"ipconfig /all" for Laptop "B" is: 

Ethernet adapter Wireless Network Connection:

Dhcp Enableded : Yes
Autoconfiguration Enabled : Yes
IP Address : 192.168.2.2
Subnet Mask : 255.255.255.0
Default Gateway : 192.168.2.1
DHCP Server : 192.168.2.1
DNS Server : 192.168.2.1



Yes, this means that DHCP is working fine on your network. So Ubuntu _should_ also work in the same manner. 

First, try this: Look for network manager in the top right hand corner of your screen; it will be something like 2 computer screens, 1 slightly behind the other. Click that icon, and see if you can see your wireless network. If you can't click on "Connect to another wireless network" and give your network SSID in the box that follows.

If for some reason you can't do the above, then you have to go the terminal (Applications-Accessories-Terminal) method```
sudo iwconfig wlan0 essid "someid"
sudo dhclient wlan0

```

Replace wlan0 and "someid" with the actual values for interface and SSID (wireless network "name")

If both of these don't work, post any outputs from the above commands, and also post output of ```
iwconfig
```

---

### Post by Mr_FixIT on 2008-06-25
Good morning,
Well this is what has happened:  Tried the "network manager" icon.    When I tag on it, I see the wireless network "user" which is the correct one, the signal bar is at the ~70% point, but the radio-button is open.  So I tag on it and the 2 little computers change to the stacked-bar-wireless icon, but with no colors in it.  And nothing appears to be happening.  When I hover the pointer over the wireless icon, it shows, "user"...0%.

So, from here I opened a terminal, and input the commands you suggested plus a few more, take a look....Thank you very much for your help!

user@user-laptop:~$ sudo iwconfig wlan0 essid "user"

user@user-laptop:~$ sudo dhclient wlan0

Internet Systems Consortium DHCP Client V3.0.6

Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)


Listening on LPF/wlan0/00:0f:b5:b6:c2:b1

Sending on LPF/wlan0/00:0f:b5:b6:c2:b1

Sending on Socket/fallback

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3

No DHCPOFFERS received.

No working leases in persistent database - sleeping.

user@user-laptop:~$

user@user-laptop:~$ ndiswrapper -l

net111v2 : driver installed

device (0846:6A00) present (alternate driver: rtl8187)

user@user-laptop:~$ sudo lshw -C network

*-network

description: Wireless interface

physical id: 1

logical name: wlan0

serial: 00:0f:b5:b6:c2:b1

capabilities: ethernet physical wireless

configuration: broadcast=yes driver=ndiswrapper+net111v2 driverversion=1.52+NETGEAR Inc.,03/24/2005,5.1 link=no multicast=yes wireless=IEEE 802.11g

user@user-laptop:~$ sudo ifconfig

lo Link encap:Local Loopback

inet addr:127.0.0.1 Mask:255.0.0.0

inet6 addr: ::1/128 Scope:Host

UP LOOPBACK RUNNING MTU:16436 Metric:1

RX packets:686 errors:0 dropped:0 overruns:0 frame:0

TX packets:686 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:0

RX bytes:34452 (33.6 KB) TX bytes:34452 (33.6 KB)


wlan0 Link encap:Ethernet HWaddr 00:0f:b5:b6:c2:b1

inet6 addr: fe80::20f:b5ff:feb6:c2b1/64 Scope:Link

UP BROADCAST MULTICAST MTU:1500 Metric:1

RX packets:0 errors:0 dropped:0 overruns:0 frame:0

TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:1000

RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)


wlan0:avahi Link encap:Ethernet HWaddr 00:0f:b5:b6:c2:b1

inet addr:169.254.10.25 Bcast:169.254.255.255 Mask:255.255.0.0

UP BROADCAST MULTICAST MTU:1500 Metric:1


user@user-laptop:~$ sudo iwconfig

lo no wireless extensions.


wlan0 IEEE 802.11g ESSID:off/any

Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated

Bit Rate:1 Mb/s Tx-Power:20 dBm Sensitivity=0/3

RTS thr:off Fragment thr:off

Encryption key:off

Power Management:off

Link Quality:0 Signal level:0 Noise level:0

Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0

Tx excessive retries:0 Invalid misc:0 Missed beacon:0

user@user-laptop:~$

---

### Post by prshah on 2008-06-25
> **Mr_FixIT said:**
> inet6 addr: fe80::20f:b5ff:feb6:c2b1/64 Scope:Link



Looks like it's taking an ipv6 address. If you are not using ipv6, you can blacklist it to prevent loading. ```
sudo gedit /etc/modprobe.d/blacklist
```, then, at the end of the file, add a single line ```
blacklist ipv6
```, save, close, reboot. Now try the network manager thing again with the signal bars, and if that still doesn't work, try the terminal commands (essid) again. 

If it _still_ doesn't work, post back with output.

---

### Post by Mr_FixIT on 2008-06-26
Hello, today's saga continues...
So, I did the "blacklist ipv6" and rebooted.  Tagged the Network Icon.  As before it showed the "user" wireless network available, ~60-70 signal power showing, but with the radio button cleared.  I tagged the radio-button.  This time 2 little swirly balls showed spinning for 20-30 seconds and then disappeared with the 2-computer-screen network icon reappearing but with a little triangular ! showing.  I tagged the network icon again, and it looked just as before, with the radio-button cleared.  I then went to the terminal and ran the commands you suggested, no luck.  So, here is the outcome of latest commands:

user@user-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Listening on LPF/wlan0/00:0f:b5:b6:c2:b1
Sending on   LPF/wlan0/00:0f:b5:b6:c2:b1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
user@user-laptop:~$
user@user-laptop:~$ sudo lshw -C network
  *-network              
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:b5:b6:c2:b1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net111v2 driverversion=1.52+NETGEAR Inc.,03/24/2005,5.1 link=no multicast=yes wireless=IEEE 802.11g
user@user-laptop:~$ sudo ifconfig
lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7900 (7.7 KB)  TX bytes:7900 (7.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0f:b5:b6:c2:b1 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:0f:b5:b6:c2:b1 
          inet addr:169.254.10.25  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

user@user-laptop:~$ sudo iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"user" 
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4C:7E:00:6E  
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3 
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

user@user-laptop:~$

---

### Post by chili555 on 2008-06-26
How about letting us see:```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by Mr_FixIT on 2008-06-26
Will do, Unfortunately the afflicted computer is at home.  I am responding from my work computer.  Will try tomorrow AM.  

Something to note from today's update:
[user@user-laptop:~$ sudo iwconfig
lo no wireless extensions.

wlan0 IEEE 802.11g ESSID:"user"
Mode:Managed Frequency:2.462 GHz Access Point: 00:90:4C:7E:00:6E
Bit Rate=54 Mb/s Tx-Power:20 dBm Sensitivity=0/3
RTS thrff Fragment thrff
Encryption keyff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0]

It appears to "see" the router now, has the proper essid and and MAC ID.  Feels like I'm getting closer and closer.

Till tomorrow, cheers!

---

### Post by Mr_FixIT on 2008-06-27
...here ya go...

user@user-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for user:
wlan0     Scan completed :
          Cell 01 - Address: 00:90:4C:7E:00:6E
                    ESSID:"user"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

user@user-laptop:~$

---

### Post by Mr_FixIT on 2008-06-27
bump

---

### Post by chili555 on 2008-06-27
It should work with:```
sudo iwconfig wlan0 essid user
sudo dhclient wlan0
```Let us know.

---

### Post by prshah on 2008-06-27
> **chili555 said:**
> It should work with:```
sudo iwconfig wlan0 essid user
sudo dhclient [color=red]wlano[/color]
```Let us know.

That's ```
sudo dhclient [color=red]wlan0[/color]
``` (wlan-zero) And it's tried and.. failed.

---

### Post by chili555 on 2008-06-27
You are quite right, I made a typo! I have edited my post to fix it.

Speaking of which, I thought I was addressing Mr_FixIT.

prshah, I guess I wasn't aware you were having problems connecting.

---

### Post by prshah on 2008-06-27
> **chili555 said:**
> You are quite right, I made a typo! I have edited my post to fix it.

Speaking of which, I thought I was addressing Mr_FixIT.

prshah, I guess I wasn't aware you were having problems connecting.

:lolflag:I meant that those commands were already tried by fixit and failed.

---

### Post by prshah on 2008-06-27
> **prshah said:**
> 
then you have to go the terminal (Applications-Accessories-Terminal) method```
sudo iwconfig wlan0 essid "someid"
sudo dhclient wlan0

```
Replace wlan0 and "someid" with the actual values for interface and SSID (wireless network "name")



> **Mr_FixIT said:**
> Good morning,

user@user-laptop:~$ sudo iwconfig wlan0 essid "user"
user@user-laptop:~$ sudo dhclient wlan0

No DHCPOFFERS received.



OK if all else fails, try this:
```
sudo iwconfig wlan0 essid user
sudo dhclient wlan0

```

Note: No quotes for "user".

If that doesn't work either, try:
```
sudo iwconfig wlan0 essid user
sudo /etc/init.d/networking restart

```

---

### Post by Mr_FixIT on 2008-06-30
Good Morning, sorry it took a while to get back, had a little vacation...
...anyway, here is the result, still no luck....
user@user-laptop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:90:4C:7E:00:6E
                    ESSID:"user"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

user@user-laptop:~$ 
user@user-laptop:~$ sudo iwconfig wlan0 essid user
user@user-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                [ OK ] 
user@user-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0f:b5:b6:c2:b1
Sending on   LPF/wlan0/00:0f:b5:b6:c2:b1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
user@user-laptop:~$ 
user@user-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9200 (8.9 KB)  TX bytes:9200 (8.9 KB)


wlan0     Link encap:Ethernet  HWaddr 00:0f:b5:b6:c2:b1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:0f:b5:b6:c2:b1  
          inet addr:169.254.10.25  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

user@user-laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"user"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4C:7E:00:6E   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

user@user-laptop:~$

---

### Post by prshah on 2008-06-30
> **Mr_FixIT said:**
> 
user@user-laptop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:90:4C:7E:00:6E
                    ESSID:"user"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
[color=red]                    Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm[/color]

wlan0     IEEE 802.11g  ESSID:"user"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4C:7E:00:6E   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
[color=red]          Link Quality:0  Signal level:0  Noise level:0[/color]
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

user@user-laptop:~$

As highlighted, there is an inconsistency here.As per the scan, it has connected to the access point 00:90:4C:7E:00:6E but though connected, it is showing link quality and signal level as 0.

Are you by any chance using the Windows 98 driver for this dongle? There is a known issue with that driver that seems to be affecting you. If you are using Windows XP drivers with ndiswrapper I don't know what's wrong.

---

### Post by Mr_FixIT on 2008-06-30
I think (notice operative word > think) I am using the XP driver.  When I installed ndiswrapper it said to use the latest.  But I am not so sure any more.  How do I check? And/or reinstall?

Separately, the MAC id listed is curious to me.  I looked up the MAC id of the router with ESSID = user, it is distinctly different (will supply when I get home later).  I do know when I connected with my XP-laptop, it finds a neighbor's open "Linksys" router.  Using my XP-laptop I am able to connect etc. to "Linksys".  I think I will try finding out what the MAC id of that device is.  Chance these are getting "crossed up" some how?!
Thank you for your continued diligence toward helping me,
Till tomorrow,
Cheers!

---

### Post by Mr_FixIT on 2008-07-01
Well, some new sleuthing....

The MAC-id is shown as:
00:14:6C:4F:C9:21
when looking at it from "the internet side".  

The MAC-id is shown as:
00:90:4C:7E:00:6E
when looking at it from "the laptop side".

I confirmed the later by looking at the wireless network manager from my XP-laptop.  

The former is realized when I login to the router.

This make any sense?  The Xp-laptop continues to connect without problem.

Regardless, w.r.t. the discussion of drivers.  I was able to confirm that I have the XP version installed.  I did this by looking at the property values of the file size of the .sys file that came from the WG111v2 netgear CD.  (108160bytes)  When I look at the properties of the same file stored on the Linux-laptop it is exactly the same size (108160bytes).

Interesting though, your suggestion regarding driver version led me to more research.  To the contrary of your suggestion (no disrespect intended) I find many submittals of problems using the XP-driver and many suggestions of success using the 98 version.

So, I think I am going to try that.  Is it as simple as dumping the .sys and .inf files that exist on the Linux-Laptop, saving the 98-versions and rebooting?  Or is there more to it?

Thanks
Mr_FixIT

---

### Post by prshah on 2008-07-02
> **Mr_FixIT said:**
> 
The MAC-id is shown as:
00:14:6C:4F:C9:21
when looking at it from "the internet side".  

The MAC-id is shown as:
00:90:4C:7E:00:6E
when looking at it from "the laptop side".

That's normal; it's because the Internet and the internal network work off two different interfaces; that's why the Internet "modem" is actually called a router.

> **Mr_FixIT said:**
> 
Regardless, w.r.t. the discussion of drivers.  
To the contrary of your suggestion (no disrespect intended) I find many submittals of problems using the XP-driver and many suggestions of 
success using the 98 version.

None taken (disrespect, that is). What I meant is that in the _specific_ case of wg111v2 windows 98 driver, there is a known problem, acknowledged by NetGear in their knowledge base as well. However, since you are using the XP driver, the point is moot.

> **Mr_FixIT said:**
> 
So, I think I am going to try that.  Is it as simple as dumping the .sys and .inf files that exist on the Linux-Laptop, saving the 98-versions and rebooting?  Or is there more to it?

More or less as you mentioned; however, first _deregister_ your exiting ndiswrapper driver, _then_ install the Windows 98 driver. It's worth a try, inspite of what I've said before.


Thanks
Mr_FixIT[/QUOTE]

---

### Post by Mr_FixIT on 2008-07-02
SOLVED!!!I installed the Win98 driver and I can connect!! WhHoo!
I followed these instructions:
[http://ubuntuforums.org/showthread.php?t=590942#6](http://ubuntuforums.org/showthread.php?t=590942#6)
Downloaded the WG111v2 driver from the suggested site.
Under step-4 of instructions, it says to go to System>Administration>Windows Wireless Drivers, which I did.  It brings up a window that showed the installed driver and gives an option to "remove" or "uninstall", which I did.  I then restarted with the WG111v2 connected (I had unplugged and connected wired network to get the new drivers into a folder I created).  Going back to System>Administration>Windows Wireless Drivers I tagged on install driver and simply followed instructions.  I then tagged on the network icon at the top.  It showed my router (user) and the neighbor's.  I tagged on my router, 2 swirly littles balls showed up, and, and.....it connected!  Shows the stacked wireless icon with 3 of 4 bars filed in blue.  I tried Firefox, and I'm in!!

So, for open, no security connections, I can connect.  Later, I will figure out how to enable security.  Since this was nearly a throw-away laptop and is completely remote from any of my home systems, this will be fine for now.  I did see the reference to the known bug in Win98 drivers for wireless security and will deal with that later.

prshah, thank you for hanging with me, very much appreciate your help!

Till, the next problem/adventure, best regards, Mr_FixIT 
:)

---

