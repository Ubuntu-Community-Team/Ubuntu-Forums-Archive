---
title: "Netgear wg311v2 problem"
date: 2005-05-24
forum: Networking &amp; Wireless
---

### Post by adrawer on 2005-05-24
Hi everyone.  Here's my situation

I used to have a belkin wireless card in my system but since ubuntu didn't like it and because it was a terrible card in XP, i decided to trash it and replace with netgear wg311v2.  Ubuntu recognizes that the hardware and driver are present, however, pinging google.com or opening firefox results in nothing.  

Here's what I did:

1) i installed the ndiswrapper for ubuntu
2) ndiswrapper -i ~/windows_driver/wg511.inf
3) ran ndiswrapper -l
Installed ndis drivers:
wg511 driver present, hardware present
4) ndiswrapper -m
5) modprobe ndiswrapper

reviewing my work:

I ran iwconfig
//----------------------------------------------------

lo        no wireless extensions.

wlan0     IEEE 802.11g/b+  ESSID:"wlan"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Encryption key:off
          Power Management:off
          Link Quality:38/100  Signal level:13/100  Noise level:0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions
-------------------------------------------------//

and then i ran ifconfig 
//------------------------------------------------
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2004452 (1.9 MiB)  TX bytes:2004452 (1.9 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:09:5B:BF:86:A3
          inet6 addr: fe80::209:5bff:febf:86a3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2772 (2.7 KiB)
          Interrupt:10 Base address:0xe000
---------------------------------------------//

when i ping google.com
//------------------------------------------
ping: unknown host google.com
-------------------------------------------//

when i ping -n 4.2.2.2
//-----------------------------------------
connect: Network is unreachable
------------------------------------------//

I know i have my device wlan0 setup to the right ssid name "wlan" and I'm not running my wireless router with any encryption of any kind.  My windowsXP (i have windows on the same box as Ubuntu) settings for the netgear card have 

network authentication :   open
data encryption:  disabled

-----------------------------------------------------------------
-----------------------------------------------------------------
-----------------------------------------------------------------
What settings do I still need to setup?  
Do i need to change the hosts in System -> Administation -> Networking ???

Thanks!
Andrew the linux noob

---

### Post by anders.ostling on 2005-05-24
Hi

I can not see any "dhclient" dhcp command in your log. Try to give the command "dhclient wlan0" explicity to see if the Ap hands out an IP adress. If you configure your network properly (System->Admin->Networking), then it should be invoked automatically in the future.

Anders

---

### Post by adrawer on 2005-05-24
dhclient wlan0

//--------------------------------------------------------------------
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:09:5b:bf:86:a3
Sending on   LPF/wlan0/00:09:5b:bf:86:a3
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
--------------------------------------------------------------------//

---

### Post by kleeman on 2005-05-24
What does sudo iwlist wlan0 show?

---

### Post by MBro on 2005-05-24
[QUOTE=kleeman]What does sudo iwlist wlan0 show?[/QUOTE]
 I'm setting up the exact same network card right now on my ubuntu box and am having the same problems.  I'm looking at the netgear manager I have on my windows 98 computer and it shows me connected to the router but not as an ap, just as an ad hoc network.  On my 98 box, we're connected to the router as ap, not ad hoc.  I feel that's what I need to change.

---

### Post by adrawer on 2005-05-24
[QUOTE=kleeman]What does sudo iwlist wlan0 show?[/QUOTE]


iwlist wlan0 doesn't give anything

iwlist wlan0 scan
//-----------------------------
wlan0 No scan results
----------------------------//

---

### Post by kleeman on 2005-05-25
Try restarting completely:
ifconfig wlan0 down
sudo rmmod ndiswrapper
Pull out the card and reinsert it
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan

The fact that your iwlist wlan0 scan shows nothing seems to indicate that ndiswrapper is not working properly especially sice iwconfig is showing info on your access point.

---

### Post by adrawer on 2005-05-25
[QUOTE=kleeman]Try restarting completely:
ifconfig wlan0 down
sudo rmmod ndiswrapper
Pull out the card and reinsert it
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan

The fact that your iwlist wlan0 scan shows nothing seems to indicate that ndiswrapper is not working properly especially sice iwconfig is showing info on your access point.[/QUOTE]

I don't really know what you mean by pull out the card and reinsert it.  It's a pci card, so i can't really remove it while the computer is on.  However, I did restart my computer after 

ifconfig wlan0 down
sudo rmmod ndiswrapper

and then finished the sequence of instructions after my system rebooted.  However, the scan result is the same = No scan reults



Should I modify my interfaces file in /etc/network ?  If I do, can someone tell me how to give myself permission to write to this file.  In properties of that file it says that I am not the owner although I am the only user in the OS (it's just a home computer).  Any suggestions would help!  Thanks

---

### Post by Beernut on 2005-05-26
[QUOTE=adrawer]If I do, can someone tell me how to give myself permission to write to this file.  In properties of that file it says that I am not the owner although I am the only user in the OS (it's just a home computer).  Any suggestions would help!  Thanks[/QUOTE]

Try sudo nano /etc/network/interfaces in a terminal window.

---

### Post by kleeman on 2005-05-26
Something quite odd going on. Check this FAQ

[http://ndiswrapper.sourceforge.net/phpwiki/index.php/FAQ](http://ndiswrapper.sourceforge.net/phpwiki/index.php/FAQ)

---

### Post by adrawer on 2005-05-27
Thanks I got it to work!  Yay!  I think it was because my essid was all uppercase though :-x my fault!

---

