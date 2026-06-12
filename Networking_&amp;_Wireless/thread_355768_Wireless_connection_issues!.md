---
title: "Wireless connection issues!"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by oldmanpete on 2007-02-07
Hi all

I'm having some serious issues with wireless connectivity in edgy. Setting up a brand new laptop.
Acer Travelmate2490 for dual booting. All okay! 

From windows i can actively scan networks and connect to them.

From edgy I cannot. I have installed network-manager and network-manager-gnome and cant even launch the bloody thing. Running network-manager from alt-f2 doesn't work. When i go into add remove programs and install form there is says its available in the Applications > Internet options but doesn't actually show. 

At this point i tried I tried wifi-radar which did actually pick up networks but would not connect. This is what the system currently loks like.

Vendor: Atheros Communications, Inc.
Device: AR5005G 802.11abg NIC

> iwconfig readout

laptop:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"TheOldMan"  Nickname:"TheOldMan"
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

/etc/network/interfaces

> auto lo
iface lo inet loopback


#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

#auto eth0

iface ath0 inet dhcp
wireless-essid TheOldMan
wireless-key s: *************

auto ath0

/etc/iftab

> [QUOTE]# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:16:d4:68:19:ae arp 1
ath0 mac 00:19:7d:0b:68:7b arp 1

[/QUOTE]

If anyone can shed any light on this i would be most greatful!

---

### Post by oldmanpete on 2007-02-07
further information

aptop:~$ iwlist ath0 scan
ath0      Scan completed :
         Cell 01 - Address: 00:14:6C:EE:A7:CA
                   ESSID:"SKY25064"
                   Mode:Master
                   Frequency:2.462 GHz (Channel 11)
                   Quality=1/94  Signal level=-94 dBm  Noise level=-95 dBm
                   Encryption key:off
                   Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                             9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                             48 Mb/s; 54 Mb/s
                   Extra:bcn_int=100
                   Extra:wme_ie=dd180050f2020101040003a4000027a4000042435e0062322f00
                   Extra:ath_ie=dd0900037f01010024ff7f

it appears to have defaulted to an unsecured network it has found?

yikes!

---

### Post by gradedcheese on 2007-02-07
do you find the correct network if you can?

sudo iwlist ath0 scanning

If not, then I would guess that the network you want isn't seen and some other one could be picked.

---

### Post by oldmanpete on 2007-02-07
as above 

ESSID:"SKY25064" is the ID its giving me and th ats for an unsecured network on my street. How do i specify that i want it to pick mine up. It must be transmitting because its seen from a laptop running windows elsewhere in the building!

---

### Post by gradedcheese on 2007-02-07
sudo iwconfig ath0 essid write_the_id_here

---

### Post by oldmanpete on 2007-02-07
Right so i have told it to scan for oldmanpete and then when you check to see what its scanning for it still shows 'skyxxxx' :( 

beka@beka-laptop:~$ sudo iwconfig ath0 essid oldmanpete
beka@beka-laptop:~$ sudo iwlist ath0 scanning
ath0      Scan completed :
          Cell 01 - Address: 00:14:6C:EE:A7:CA
                    ESSID:"SKY25064"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=4/94  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101040003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f01010024ff7f

this is starting to fry my brain

---

### Post by maxwang on 2007-02-07
i am having a similar issue. i have a dell latitude d610 and a clean install of edgy. i ran through all the installation procedures and everything went fine. however network manager does not detect my wireless card but when i do a iwlist eth1 scan, it detects the access point i want to connect to. when i try to configure it from the gui, nothing happens.

i even did sudo iwconfig eth1 essid max and that doesnt seem to do anything.

---

### Post by oldmanpete on 2007-02-07
Even more information...

when i do sudo ifconfig it actually shows 4 devices

beka@beka-laptop:~$ sudo ifconfig
ath0      Link encap:Ethernet  HWaddr 00:19:7D:0B:68:7B  
          inet6 addr: fe80::219:7dff:fe0b:687b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:16:D4:68:19:AE  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe68:19ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11867 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8772796 (8.3 MiB)  TX bytes:1756336 (1.6 MiB)
          Interrupt:66 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:500 (500.0 b)  TX bytes:500 (500.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7D-0B-68-7B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:752 errors:0 dropped:0 overruns:0 frame:138257
          TX packets:9768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:78630 (76.7 KiB)  TX bytes:492809 (481.2 KiB)
          Interrupt:58 Memory:e0360000-e0370000 

why would my wfi be registering under ath0 if there is a wifi0??

I've gone past the point of puzzled to down right flumoxed. I'm relatively new to Linux/ubuntu and this is causing me some real grief!

---

### Post by gradedcheese on 2007-02-07
It's the way the driver was written: ath0 is your real WiFi device, wifi0 is a special management interface.

---

### Post by oldmanpete on 2007-02-08
Right some progress has been made..

I finally got that confused with all the changes I had made I could not remember how much and what I'd done. As it was a brand spanker of an install I just flattened and reinstalled ubuntu. From there i did a full update/upgrade (all repos in synaptic enabled) and rebooted. After this I installed network-manager and network manager-gnome.

On reboot the network manager applet would actually work and I have successfully been able to scan for a networks. Having found and connected to my network all initially seemed okay. signal strength of 60% and fluxuating! As soon as I try to connect to the Internet it wont find a connection. Tried to ping my router from terminal and get the message 'Network is unreachable'. 

The connection stability is still fluxuationg at this point indicating that it is seeing the wireless network.

I feel i'm not far off a solution now but I need a bit of help over the final hurdle!

---

### Post by oldmanpete on 2007-02-08
Was not picking up the wireless network because i'd specified in network settings which network i wanted to conect to. Network-manager dictates that you dont do this.

#'ed out everything in /etc/network/interfaces with the exception of auto lo and it all seems to be working *touch wood*!

Hurrah!

---

### Post by timlewis242 on 2007-02-08
Of course you want to make sure your router is not encrypted, at least until you get a successful connection. That would eliminate one variable and potential problem. The drivers for the built in wi-fi are strange and if you're using wep or wpa, it may look like it should connect, it might even ask you for the key but you're better off running naked at least for the time it takes to get the connection made, then you can worry about encryption.

The other issue is that sometimes, the drivers and cards do not like to update their IP address, as this is a problem I have from time to time. I have discovered that if I use static IP addresses on my network, even the windblows machines I have connected to it, I can then resolve any connection issues my manually changing the IP address in the connection manager for my AP.

Also you can try to force it to renew the interface. 
'dhclient wlan0' works on mine and I guess the long term solution would be to put this in a start up script. The strange thing is that mine doesn't always need to use it to connect. Sometimes it all works and sometimes I have to change the IP address or use the above command to force the interface to reset itself.

Unfortunately for me, I cannot seem to use the windows driver for my card (with NDIS Wrapper) but you might try that as well and see if that resolves some of your problems. You'll also come much closer to using encryption if you use the windows driver as it looks like the best you can do with the driver Ubuntu installs is WEP.

There is a front end for the NDIS wrapper that makes using it easier. Just download it from the ADD/REMOVE repositories. Do a search for NDIS and it will display. It will show up as "Windows Wireless Drivers" in the Administration menu. Then you only need to get a copy of the windows driver for your card and install it using that GUI. 

I hope all of this helps.  For what it's worth, you could always try an external wireless card and see if it works. Just make sure you keep the receipt. LOL.

---

