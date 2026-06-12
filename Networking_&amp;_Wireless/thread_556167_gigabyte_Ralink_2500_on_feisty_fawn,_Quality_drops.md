---
title: "gigabyte Ralink 2500 on feisty fawn, Quality drops to &quot;0&quot;, weird problem"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by oranguman on 2007-09-21
hey, longtime listener first time caller, love the show.

the subject here is networking on my desktop, a Dell Dimension/Celeron..

fresh install of Feisty Fawn, with an odd networking problem: 

if i'm not mistaken, it should have support for the Ralink 2500 card (a Gigabye GN-WPKG) right out of the box, but whenever I attempt to connect to my wireless network I can watch the Quality of ra0 drop from 95 to 75 to 60 to 0 as the network-assistant icon animates. 

over the course of these few seconds, **iwlist** looks like this: 

ra0        Scan Completed :
             Cell 01 - Address: 00:xx:xx:xx
                           mode managed
                           essid "linksys"
                           encryption key: off
                           channel 6
                     **     *Quality: 84/100  Signal level:-102dBm Noise level:-224dBm **

three seconds later:

ra0        Scan Completed:
              "   "
              Quality: 65/100       Signal Level:-102     Noise level:-224dBm 

...and so on, until the quality hits "0" and the icon switches to 'no connection'. I can see my SSID in the drop down menu from network-assistant, too. 


while this is going on, **ifconfig** is showing: ra0 like this:

ra0       Link encap:Ethernet  HWaddr 00:14:85:B6:5D:EE  
          inet6 addr: fe80::214:85ff:feb6:5dee/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81060 errors:3 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44743 (43.6 KiB)  TX bytes:3731663 (3.5 MiB)
          Interrupt:20 Base address:0x4000 

three seconds later..

x@steve:~$ sudo **ifconfig**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

ra0       Link encap:Ethernet  HWaddr 00:14:85:B6:5D:EE  
          inet6 addr: fe80::214:85ff:feb6:5dee/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81064 errors:3 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44919 (43.8 KiB)  TX bytes:3731887 (3.5 MiB)
          Interrupt:20 Base address:0x4000 


does anyone have any idea what is going on here? I could really use some help or direction?!?!

D



P.S. 
here is my **/etc/network/interfaces**: 

auto lo
iface lo inet loopback 

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


#iface ra0 inet dhcp
#wireless-essid linkfish

#auto ra0

---

### Post by oranguman on 2007-09-21
yup, it definitely should work; it's listed on [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsGigabyteTechnology](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsGigabyteTechnology)

it's the top one. I'm going to try commenting out the wired connections that don't show up on **iwconfig** and rebooting

I'll let you know how it goes and i'm sorry to be impatient, but ubuntu's functionality BLOWS UP once you get to the ol' internet; i'm sure you know.. that's when it gets cool!

thanks

---

### Post by kevdog on 2007-09-21
Not telling you what to do, but you might want to upgrade the old 2500 built-in driver to the newer rt2500 serial monkey driver if you keep having problems.  Do a search in the forums for rt2500, rt73, serial monkey -- Im sure you will run across something :)

---

### Post by oranguman on 2007-09-21
> **kevdog said:**
> Not telling you what to do, but you might want to upgrade the old 2500 built-in driver to the newer rt2500 serial monkey driver if you keep having problems.  Do a search in the forums for rt2500, rt73, serial monkey -- Im sure you will run across something :)


thanks, i'll try that.. i'm still having problems, but something interesting has happened:

I tried to plug in an old Linksys WUSB, to see what kind of autodetection this device has in the current kernel, and looked around, and I attached an ethernet cable to the back of the computer to see what would happen too. (The ethernet port on this computer corresponds to a hardware card that has since been removed. It doesn't work.) Then I played with the Networking control dialog for a while. 

The punchline is, when I removed the Linksys WUSB (I think it requires ndiswrapper.. I never got it to work on Edgy EFT)... well, my wireless AP suddenly became visible to the network manager! it's strong too. how bizarre.

I wish I could say that I was on that connection right now, but now I CAN'T RESOLVE ANY PAGES!! 

>sudo dhclient ra0 gives 

Listening on LPF/ra0/{mac address}
Sending on (same)
Sending on socket/fallback
DHCPDISCOVER on Ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on Ra0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on Ra0 to 255.255.255.255 port 67 interval 5
no DHCPOFFERS recieved
no working leases... 

what could be wrong now?? I'm worried that the connection will disappear when I reboot but then, I did comment out ra0 in /etc/interfaces/networking so i'll once again undo that and try.. 

weird, huh? wish me luck

---

### Post by oranguman on 2007-09-21
well, I have one acronym for anyone that reads this thread, it's WICD.. this was a simple and elegant solution to the problem, which was that the dhcp requests were never getting to the router. i'd recommend this easy-install program to anyone with a ralink chipset

PEACE

---

