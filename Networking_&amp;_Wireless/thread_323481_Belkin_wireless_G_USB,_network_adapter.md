---
title: "Belkin wireless G USB, network adapter"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by pedro.delgallego on 2006-12-22
Hi, 

I've some problems with my USB wireless device.  I cannot connect to internet via wireless :

I've to computers, one laptop (its working correctly under ubuntu), and a desktop with Belkin usb wireless. the last one not work at all. 

What can i do to connect with this computer?
Why when i conect the USB devices i have two interfaces wlan0 and wmaster0 ?
Must i put the same ip to wmaster0 and wlan0? 

Thanks in advance.. 

 

************************************* technical  data
With my computer clean i do : 
> #ifconfig 

         [INDENT]  eth0      Link encap:Ethernet  HWaddr 00:05:1C:05:68:B8  
          inet addr:192.168.0.40  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::205:1cff:fe05:68b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3799 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:29 txqueuelen:1000 
          RX bytes:3498211 (3.3 MiB)  TX bytes:600815 (586.7 KiB)
          Interrupt:201 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4424 (4.3 KiB)  TX bytes:4424 (4.3 KiB)[/INDENT] 

Then i conected the device to my computer : 

> :~$ ifconfig
[INDENT]eth0      Link encap:Ethernet  HWaddr 00:05:1C:05:68:B8  
          inet addr:192.168.0.40  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::205:1cff:fe05:68b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3935 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3337 errors:0 dropped:0 overruns:0 carrier:0
          collisions:29 txqueuelen:1000 
          RX bytes:3622375 (3.4 MiB)  TX bytes:621516 (606.9 KiB)
          Interrupt:201 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4424 (4.3 KiB)  TX bytes:4424 (4.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:17:3F:13:66:91  
          inet6 addr: fe80::217:3fff:fe13:6691/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:1208 (1.1 KiB)
          Base address:0x2000 

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-13-66-91-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.168.0.30  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x2000 [/INDENT]


I config and setup the interface wlan with my static ip and my DNS and ifdown the eth0

> ifconfig 
[INDENT]lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17302 (16.8 KiB)  TX bytes:17302 (16.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:17:3F:13:66:91  
          inet addr:192.164.0.30  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fe13:6691/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:5910 (5.7 KiB)
          Base address:0x2000 

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-13-66-91-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.168.0.30  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x2000 
[/INDENT]

then i try to   ping to my router : 

> 
ping 192.168.0.100
[INDENT]
PING 192.168.0.100 (192.168.0.100) 56(84) bytes of data.
From 192.168.0.30 icmp_seq=2 Destination Host Unreachable
From 192.168.0.30 icmp_seq=3 Destination Host Unreachable
From 192.168.0.30 icmp_seq=4 Destination Host Unreachable
[/INDENT]

I try to ifup the interface : 

> :~$ sudo ifup wlan0
[INDENT]SIOCADDRT: Network is unreachable
Failed to bring up wlan0.[/INDENT]
 
~$ sudo ifdown wlan0
[INDENT]ifdown: interface wlan0 not configured[/INDENT]
~$ sudo ifup wlan0[INDENT]
SIOCADDRT: Network is unreachable
Failed to bring up wlan0.[/INDENT]


I look int the etc/network/interfaces file :
> 
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet static
address 192.164.0.30
netmask 255.255.255.0
gateway 192.168.0.100
wireless-essid WLAN
auto wlan0

iface wmaster0 inet static
address 192.168.0.30
netmask 255.255.255.0
gateway 192.168.0.100
wireless-essid WLAN
wireless-key s:

auto wmaster0


ty

---

### Post by [L2G] Slapshot on 2006-12-22
Hi Pedro 
I have a Belkin wireless usb adaptor working with wep encryption at the moment. First what is the chipset of the device, type lsusb in a command window then let us know here. There are different versions all around the world. Mine is using the ralink rt73 driver that came with the windows install disc loaded with ndiswrapper. 

Also you have to remember most of the newer drivers from Ralink are plug and play. I have to remove my usb stick, start the p.c, login to the desktop then insert the stick wait 7 or 8 seconds and then use wireless assistant to scan and then connect to the wireless network.

Cheers
Slapper

---

### Post by pedro.delgallego on 2006-12-22
Hi, thats the output. 
I suposse is this one :  rt73 (Belkin F5D7050) by [google]("http://www.google.es/search?q=050d%3A705a+Belkin+Components+&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a") 

> ~$ lsusb
[INDENT]
Bus 003 Device 005: ID 050d:705a Belkin Components 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 062a:0000 Creative Labs 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000[/INDENT]  

in my cd, the driver directoriy : > 
:/media/cdrom0/drivers/1.0.0.0/win2kxp$ ls
[INDENT]rt73.cat  rt73.inf  rt73.sys[/INDENT]

more commands outputs : 
> 
 iwconfig[INDENT]
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr: off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"WLAN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr: off   Fragment thr=2346 B   
[/INDENT]

sudo iwlist wlan0 scan [INDENT]
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:21:D7:C9:A1
                    ESSID:"P153471890003"
                    Mode:Master
                    Frequency:2.412 GHz
                    Encryption key:on
                    Extra:tsf=000000007b774105
          Cell 02 - Address: 00:80:5A:29:05:D8
                    ESSID:"WLAN"
                    Mode:Master
                    Frequency:2.437 GHz
                    Encryption key:off
                    Extra:tsf=0000000d32e1365e[/INDENT]

sudo iwconfig wlan0 WLAN[INDENT]
Error : unrecognised wireless request "WLAN"[/INDENT]

sudo iwconfig wlan0 P153471890003[INDENT]
Error : unrecognised wireless request "P153471890003"[/INDENT]

 tcpdump
[INDENT]tcpdump: no suitable device found[/INDENT]



thanks again,

---

### Post by [L2G] Slapshot on 2006-12-22
Hi Pedro
You are in luck this is the exact same chipset as mine so if you follow this howto exactly it will work. Also your usb device is plug and play driver so you will have to take it out reboot and login then wait and use wireless assistant to scan and connect. here's the howto link.

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?action=show")

Tip I didn't compile the drivers I used the drivers from the cd and installed them using ndiswrapper

I actually used this mostly and then used the above guide to set up the network config

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29")

Hope this works for you and don't forget to boot without it plugged in mate.
Cheers
Slapper

---

### Post by lkaufma1 on 2006-12-22
Windows user here that was convinced to load Ubuntu and try it out. Well I did and like it alot, however I need to install this Belkin USB Wireless G Version 3000 from scratch. I literally have no idea on how to use Ubuntu whatsoever. I am savvy at building Windows machines, but this is all new to me. I have a readout from lsusb here:

Bus 001 Device 003: ID 050d:705a Belkin Components
Bus 001 Device 002: ID 066b:2211 Linksys, Inc. WUSB11 802.11b Adapter
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

and iwconfig here...
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11-DS ESSID:"linksys" Nickname:"okuwlan"
Mode:Managed Frequency:2.457 GHz Access Point: Not-Associated
Bit Rate:11 Mb/s Tx-Power=15 dBm
Retry limit:8 RTS thr=1536 B Fragment thr=1536 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.


I've scoured and read for over 5 hours and still have no clue what is wrong and where to go from here. Any help for a newb would be appreciated! 

Thanks in advance!

---

### Post by pedro.delgallego on 2006-12-22
The ouptu when i try to follow the instructions : 
> 
pedro@la-vaca-verde:/media/cdrom0/drivers/1.0.0.0/win2kxp$ ls
[INDENT]rt73.cat  rt73.inf  rt73.sys[/INDENT]
pedro@la-vaca-verde:/media/cdrom0/drivers/1.0.0.0/win2kxp$ sudo ndiswrapper -i rt73.inf
[INDENT]Installing rt73 [/INDENT]
pedro@la-vaca-verde:/media/cdrom0/drivers/1.0.0.0/win2kxp$ sudo ndiswrapper -l
[INDENT]Installed drivers:
rt73            driver installed, hardware present 
[/INDENT]
pedro@la-vaca-verde:/media/cdrom0/drivers/1.0.0.0/win2kxp$ sudo modprobe ndiswrapper
pedro@la-vaca-verde:/media/cdrom0/drivers/1.0.0.0/win2kxp$ sudo ndiswrapper -m
[INDENT]modprobe config already contains alias directive[/INDENT]
pedro@la-vaca-verde:/media/cdrom0/drivers/1.0.0.0/win2kxp$ gksudo gedit /etc/modules
[B]pedro@la-vaca-verde:/media/cdrom0/drivers/1.0.0.0/win2kxp$ sudo iwconfig wlan0 essid "WLAN"  mode Managed
[INDENT]Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.[/INDENT][/B]
pedro@la-vaca-verde:/media/cdrom0/drivers/1.0.0.0/win2kxp$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr: off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"WLAN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr: off   Fragment thr=2346 B   



I dont how to solve the broke instruction. 

Thanks,

---

### Post by [L2G] Slapshot on 2006-12-22
Hi Pedro
Yes the command failed 
 SET failed on device wlan0 ; Device or resource busy.
because the device or resource is busy. I took ages to solve this, unplug the device as its in use and try the command again or alternatively reboot without it and try the command. I think this is why it failed. I'ts a while ago now since I did it, I appologise for my poor memory

Slapper

---

### Post by pedro.delgallego on 2006-12-22
Now is not busy 

but is not working. Now i can see the MAC address. 
> 
pedro@la-vaca-verde:~$ iwconfig
 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"WLAN"  [INDENT]
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:80:5A:29: 05: D8   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr:2 347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-42 dBm  Noise level:-256 dBm
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag:0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon:0 [/INDENT]

pedro@la-vaca-verde:~$ ping 192.168.0.100
connect: Network is unreachable


Its look good, but i make a ping to my router. 


But when i scan for netwoks i can see my and my neighbors nets. 
> 
sudo iwlist wlan0 scan[INDENT]
wlan0     Scan completed :
          Cell 01 - Address: 00:80:5A:29: 05: D8[INDENT]
                    ESSID:"WLAN"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-42 dBm  Noise level:-256 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0[/INDENT]
          Cell 02 - Address: 00: 0F:21: D7: C9:A1[INDENT]
                    ESSID:"P153471890003"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-74 dBm  Noise level:-256 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0[/INDENT]
          Cell 03 - Address: 00:01:38:58:2A: D8[INDENT]
                    ESSID:"angel"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level: -80 dBm  Noise level:-256 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK[/INDENT]
 [/INDENT] 

And this  is the config in my /etc/network/interfaces  file: 
> 
# rt73 wireless network device using static IP address 
iface wlan0 inet static
pre-up ifconfig wlan0 up
wireless-essid WLAN
address 192.164.0.30
netmask 255.255.255.0
gateway 192.168.0.100
# wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX       # This line for hexidecimal keys
wireless-key s:			                # This line for ASCII (string) keys
# network XXX.XXX.XXX.XXX
# broadcast XXX.XXX.XXX.XXX
auto wlan0 

But the ping is not working. I dont know.  Is a configuation problem ? a driver problem ?
the lsusb looks good : 
> 
pedro@la-vaca-verde:~$ lsusb 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 062a:0000 Creative Labs 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 050d:705a Belkin Components 
Bus 001 Device 001: ID 0000:0000  


thx

---

### Post by [L2G] Slapshot on 2006-12-23
Hi Pedro
Sorry for the delay but I have to work.

here is my network interfaces file

iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
wireless-essid belkin54g
wireless-key xxxxxxxxxxxxxxxxxxxxx

I also just boot the p.c then login then use wireless assistant to scan and connect to my network. You may need to download and install it.

I use wlassistant search in synaptic .

we'll get there
Slapper

---

### Post by pedro.delgallego on 2006-12-23
Ok im going to try this tonigth . 

Im must work too ](*,) 

thanx. Tomorrow i say to you the result

---

### Post by Sigudian on 2006-12-24
I have the same wirless card i got for x-mas, and i also had problems setting it up, i followed the guide linked in post #4 and compiled my own drivers(as guided in the touturial)
I just wanted to say thank you, because now i can use the car my brother gave to me for x-mas and not use that 20m TP-cable that goes up the stares and around the house(under the oven).

**Now it works, thank you [L2G] Slapshot!!!!**

(in case your wondering, in norway we open presents at the 24th in the evening after dinner and desert, so no im not a spoiled brat who opens presents the day befor, its acustom)

---

### Post by [L2G] Slapshot on 2006-12-26
Excellent Sigudian

Glad it's working for you. Just to let you know I got my present on the 20th of December, a 4 GIG flash memory stick off my Wife. I got it early to use on a job I had to do before Christmas.

Happy Christmas and New Year to all TaPioneer Kubuntu / Ubuntu / Kubuntu / Xubuntu / Edubuntu and any Flavour I've missed users, Devs and Programmers.

Slapper

---

### Post by melenor on 2007-01-18
i am a complete newbie to Ubuntu having just recently installed it, after hearing so much about Linux, but the biggest problem i have is that i can't access the internet, the problem is the Belkin  Wireless G USB Network Adapter. i was originally going to post a new topic in complete beginners but when i searched i found this. i am using it works fine in windows but doesn't work in Ubuntu and i need some basics to help me, i heard that each one uses different chipsets and how do i find the chipset and when i type stuff in should i use windows or Ubuntu to do it?

Thanks for helping me

---

### Post by [L2G] Slapshot on 2007-01-21
Go to the command line and type lsusb ( LSUSB in lower case ) This will give you the device id which inturn will help us find if it's supported and what the driver it needs.

Jacko

---

