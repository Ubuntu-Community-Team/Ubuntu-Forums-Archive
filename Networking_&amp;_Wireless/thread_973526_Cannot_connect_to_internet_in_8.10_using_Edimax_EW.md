---
title: "Cannot connect to internet in 8.10 using Edimax EW-7318-USg"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by peter4432 on 2008-11-06
I am a newbie to using Ubuntu and as such have been having problems using my wireless usb card since I install Ubuntu 8.04. I hoped upgrading to 8.10 might help me, as using 8.04, I was not even able to get the my wireless card, an Edimax EW-7318USg usb, to be recognized by Ubuntu, even by following the various instruction sets posted on this forum.

Having upgraded to 8.10, this issue is no longer a problem, as the improved wireless support now recognizes my card and is using the appropriate drivers, so I can configure the card. However, I still cannot connect to my wireless network.

When I click on the network icon on the top right now, it presents me with the SSID list including my home network, and when i click it is pops up with a prompt to enter the wpa/wpa2 key. However, when I enter the key, all that happens is that the icon changes to the two lights of the requesting connection icon, with both balls being green and after a while just goes back to the network icon with the message 'Disconnected'.

Also, if I change the settings of the connection to my home network using the r-click edit connections... option, and set up the connection to be static using the manual option in IPv4 settings tab, i.e. set the require IP, subnet and gateway key, the connection tab icon changes to the connected icon, and I can see and iwconfig and connection information seem to indicate I have a connection to my network. In fact, even my router, a Netgear WPN824v2 seems to think there is a connection, as in the attached devices option tab on its config screen, it displays the same IP address and mac info for my computer as when it is connected in Windows. However, despite all these indications of a good connection, I still cannot access the internet for any function from browsing to updating Ubuntu.

Further more, when I am apparently connected to my network in the manner above, if I try to ping the default gateway, I get the following:
From 192.168.1.x (set ip address) icmp_seq=x Destination Host Unreachable
Over and over until I hit Crtl+C.

Can someone please help me to figure out whats going on and let me connect to my network and the internet.

To help here are the result of ifconfig and iwconfig when I try to use wireless with auto dhcp:

ifconfig:
wlan0
Link encap:Ethernet HWaddr 00:1f:1f:14:4d:a8
inet6 addr: fe80::21f:1fff:fe14:4da8/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:62 errors:0 dropped:0 overruns:0 frame:0
TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:8261 (8.2 KB) TX bytes:22739 (22.7 KB)

iwconfig:
wlan0
IEEE 802.11bg ESSID:""
Mode:Managed Frequency:2.437 GHz Access Point: Not-Associated
Bit Rate:54 Mb/s Tx-Power=16 dBm
Retry min limit:7 RTS thrff Fragment thr=2352 B
Power Managementff
Link Quality=41/100 Signal level:-70 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ANd with manual IPv4 settings:
ifconfig:
wlan0
Link encap:Ethernet HWaddr 00:1f:1f:14:4d:a8
inet addr:192.168.1.7 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::21f:1fff:fe14:4da8/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:64 errors:0 dropped:0 overruns:0 frame:0
TX packets:197 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:8567 (8.5 KB) TX bytes:26173 (26.1 KB)

iwconfig:
wlan0
IEEE 802.11bg ESSID:"Taylor Family Network"
Mode:Managed Frequency:2.437 GHz Access Point:00:1B:2F:5A:E9:E2
Bit Rate:54 Mb/s Tx-Power=16 dBm
Retry min limit:7 RTS thrff Fragment thr=2352 B
Power Managementff
Link Quality=67/100 Signal level:-58 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

### Post by KF4WBS on 2008-11-16
I installed ubuntu 8.10   i had a lot of trouble configureing the manule ip but i got the firefox running     then my screen resolution change so large that i could not see the buttons to continue  so i reinstalled the operating system ...... Same problem twice now the screen is stable however i have jumped up and down trying to get the internet working again   i can ping my router    i thought it might be an hardware issue............. I am typing this message using knopix lite   it configured first try ........... No screen issues ...........     I think ubuntu 8.1 needs some work......... The eariler vers  were much more user friendly   i am sorry that the 7 vres is no longer supported   i cant update ..    

Part of the config issues are     number typed into the config box just go from 192.168.x.x   to 0.0.0.0  the ok button greys out then after trying 10-12 times ops it goes in the box  but the browser cannot still find the dns server   it is installed in the bos  i didnt forget to put it in  .............     The program just doesnt run

---

