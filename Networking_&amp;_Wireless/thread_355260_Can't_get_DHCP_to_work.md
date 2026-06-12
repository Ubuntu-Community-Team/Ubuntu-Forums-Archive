---
title: "Can't get DHCP to work"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by JoeMul on 2007-02-07
Hello...

I'm  admittedly a 'newbie' on Ubuntu and I really like Ubuntu thus far except for a frustrating problem I'm having with wireless and DHCP...yes I know this is a fairly recurrent theme and I've followed nearly every suggestions offered but to no avail and I'm hoping that someone in the forum might spot something.   I'm using a Dell Latitude C840 which used to run XP and I've tried a variety of network cards mostly Netgear products, an Airlink and finally a  ZyDas USB dongle which comes with a 9 Db external antenna...  I  initally begin on Ubuntu 6.06 and encountered the problem with this release and had hope that 6.10 would resolve the problem but I got the same problem with DHCP

The first screen capture shows the device in question (which incidentally comes with Linux drivers) and it's showing up as eth1 ..When I run Ifconfig (the second screen capture) I don't see any packets being received or transmitted but yet when I run Iwlist eth1 scan I can see many access points... I'm particularly interested in connecting to the Access point with the essid of "GoogleWiFi which is open system without any encryption or password ...

In the third screen capture I'm showing what I believe to be excellent signal quality and levels  yet when I try to extract an ipaddress from the router using Dhclient (Screen capture 3) I'm never able to receive a ip... The router (access point) works fine as I have other Windows computers which are  able to get ipaddress without problems....   Actually I'm unable to get an Ip from any Router or access point that wireless assistant shows (screen capture 4) yet I'm able to use the DHclient to obtain an Ip address on a wired network....

So I 'm pretty much discounting hardware, access points, and or signal level or quality, so I'm  hoping that someone on the forum might have some pointers or have seen something like this before....I've tried pretty much everything that I can think of but I'm open to any suggestions  and I'm interested to hear if anyone has had issues with WPA on an open system.....

Many thanks in advances for any suggestions.

---

### Post by gradedcheese on 2007-02-07
lets try some things from the shell:

sudo ifconfig eth1 down
sudo ifconfig eth1 up
sudo iwconfig eth1 essid GoogleWiFi
sudo dhclient eth1

Does that help?  By the way, I would copy/paste the output of shell commands like ifconfig and iwlist instead of taking screenshots :)  In case you didn't know, in Linux you can just select some text with your mouse, which automatically copies it.  To paste, you middle-click (or if you only have two buttons, try pressing them both at the same time).

---

### Post by JoeMul on 2007-02-08
Sorry about the screen captures ..... Anyhow reinstalled the  OS  yet again ... I have the wired connection using DHCP but  alas still no wireless ... The installation seems to have recognized all my hardware including my USB dongle wireless adapter ....
*********************************************************************************************************
**Ran the scripts as shown below:**

joe@dufus:~$ sudo ifconfig eth1 down
joe@dufus:~$ sudo ifconfig eth1 up
joe@dufus:~$ sudo iwconfig eth1 essid GoogleWiFi
joe@dufus:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 4915
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:02:72:57:43:61
Sending on   LPF/eth1/00:02:72:57:43:61
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
***************************************************************************************************
IWconfig returns

joe@dufus:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      802.11g zd1211  ESSID:"GoogleWiFi"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Encryption key:off
          Link Quality=86/100  Signal level=93/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
**********************************************************************************************************

Ifconfig returns

joe@dufus:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:02:72:57:43:61  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
********************************************************************************************************

Yet when  I scan manually I receive the following:

iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:0D:97:04:85:A6
                    ESSID:"GoogleWiFi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:3
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=100/100  
                    Extra: Last beacon: 68ms ago
          Cell 02 - Address: 00:E0:98:52:24:F2
                    ESSID:"default"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:3
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=100/100  
                    Extra: Last beacon: 56ms ago
          Cell 03 - Address: 00:0C:41:A2:EF:1B
                    ESSID:"mtvwp"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:4
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=100/100  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 76ms ago
          Cell 04 - Address: 00:0D:97:04:0C:F2
                    ESSID:"GoogleWiFi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:3
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=100/100  
                    Extra: Last beacon: 184ms ago
***********************************************************************************************
My interfaces file (etc/network/interfaces) looks like this:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid GoogleWiFi

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Not sure if I need the extra stuff but I commented out most of the lines in earlier attempts and it didn't do me any good.

**********************************************************************************************************************
my /etc/iftab looks like this:

eth0 mac 00:08:74:07:3a:f8 arp 1
eth1 mac 00:02:72:57:43:61 arp 1

******************************************************************************************************
So I'm not sure where else to go ..The Access point is unsecured and I have plenty of signal strength  so what am I missing here... DHCP works on the wired connection as this is how I'm posting to the forum...The wireless card USB dongle appears to work as I'm seeing other Access points than GoogleWiFi although I can't connect to any of the unsecured ones but my Windoze machines have no problems... I have tried several different types of pci wireless card in this machine  and always get the same frustrating problem despite the fact it worked fine with Windoze.

So i appreciate the response and eagerly await the next response  


******************************************************************************************************

---

### Post by gradedcheese on 2007-02-08
I haven't seen this happen before:

```

Mode:Managed Frequency:2.422 GHz Access Point: Invalid 

```

So it looks like your WiFi card is supported, it took the SSID you entered, and supposedly associated, or maybe failed at that point.   Out of curiosity, is there another access point that you can associate with (from "sudo iwlist eth1 scanning") just to test things out?  Also, if you have a wired connection already, you might want to bring that one down while you mess with the wireless, but it's not a big deal since they're probably on different networks/subnets.

Also I am not sure why your interfaces file has 'ath0' and 'wlan0' in it, those are generally found when you have an Atheros chipset card.  But then iwconfig doesn't list them and only shows you eth1.  Did you remove the extra interfaces before or after running iwconfig?  Also, can you post the results of the "lspci" command?  I'm curious if maybe you do have an Atheros chipset.

---

### Post by trippinnik on 2007-02-08
What version of the driver are you using?  Is it the one built into the Kernel? What kernel version are you using?  I have a wireless dongle based on the same hardware.  With kernel before 2.6.20 I had to build and install from the communiity maintained zydas driver (probably a newer version that shipped with your dongle).  There's a good howto here: [http://www.ubuntuforums.org/showthread.php?t=288753&highlight=zd1211](http://www.ubuntuforums.org/showthread.php?t=288753&highlight=zd1211) about that driver.

can you post what lsusb reports? also what does dmesg say when you plug in the dongle?

---

### Post by JoeMul on 2007-02-08
Hi Gradedcheese,

Thanks for the quick response and I had also  thought at one time that I had a hidden wireless card fl but here's the output from **LSPCI **

*****************************************************************************************************************00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go] (rev a3)
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
******************************************************************************************************

I have both commented out  and deleted the Wlan0 and Atho  entries in the interfaces file on previous occasions but it didn't help ... I also disabled the wired connection and even rebooted but I've never been able to receive a IPaddress from DHCP....

Now want to hear the funny part...The wired connection I'm using is actually connected to the same Access point "GoogleWiFi" using a Rukus wireless modem....I'm just taking the output from the Ruckus over a Cat 5 cable to the Ethernet connection and it works...  So now you can probably understand why I'm so perplexed...

---

### Post by JoeMul on 2007-02-08
Actually on this go around I've used the driver thats supplied with the kernel but I did try both the Windows driver and the linux driver that came supplied with the Dongle...And I had the same result...I also had the same result with the Netgear PCI and Airlink card that I've tried.. I used both NDISwrapper and MADWIFI  but I'm always running into the same problem where I can see the Access points but never get an Ipaddress from the DHCP... 

Nonetheless I've enclosed the output from **LSUSB** which shows the ZYDAS 

***********************************************************************************************************Bus 002 Device 002: ID 0ace:1215 ZyDAS 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

***********************************************************************************************************

---

### Post by DanlG on 2007-02-08
Is it possible that your wireless server does not have DHCP running on it?  

Sometimes the wireless modem has a few wired ports.  Can you get a DHCP connection through them?  Could be something else obvious like a MAC filter running.

---

### Post by JoeMul on 2007-02-08
I somehow doubt that filtering is employed it as this is Google's WIFI which  I'm attempting to connect to and  covers the city in which I live... As I mentioned previously I have no problem with Windows and other people apparently have managed to have Ubuntu connect as well.. In fact this laptop used to be a Windows machine and it worked fine before I installed Ubuntu...See the plot thickens..

---

### Post by joriad on 2007-02-08
I had a problem also with DHCP on edgy not assigning an ip address, my lan even indicated i was sending and receiving packets. I tried everything from static ip addresses to  reinstalling my OS, to installing a different lan card. However the problem was that I simply needed to shutdown my computer and unplug my modem from the power source, then doing a full restart of the modem then (only after the modem was up and running) powering up my computer. I do not know if this would work with your wireless router but you could give it a try.

---

### Post by joriad on 2007-02-08
Also if it does have the capability of wired connection as another had stated, it would probably make sense to try restarting the router and computer both ways.

---

### Post by shofetim on 2007-02-08
Hello,

I have had the same problem, but slightly different hardware, here is what I have and what worked for me:

Internet is via a cable modem, which is connected to a Netgear WGR914 wireless router, I have two windows computers that share this connection, and installed Ubuntu Edgy 6.10 on a Compaq P6105NR laptop. Ubuntu installed fine and recognized the wireless card, but could not connect, so I followed the directions for using the firmware cutter. Then restarted. Network manager then saw my card, and the network, and would repeatedly attempt to connect, but with no effect. From reading on the forum I remembered that the Netgear instructions mentioned restarting when you added a computer, so I turned everything off (all computers on my LAN, the cable modem, and the router) then powered on the cable modem, then router, than the computers. Now the router can see the notebooks card, and the card can see the router, but still no connect. So I changed the routers settings to permanently assign an IP to the laptop, and used ipconfig /releas, ipconfig /renew on the windows machines to free the IP the router assigned to the laptop. Everything is now working.

---

### Post by spot221 on 2007-02-10
I am having the same problem.  I have a smc card with  a zd1211b chipset.  Apprently these chipsets are having a difficult time connecting.  One of the solutions I have seen is to use an older version of the firmware.  I have not had the time to try this yet.  But the firmware can be down loaded from here
[http://sourceforge.net/project/showfiles.php?group_id=129083](http://sourceforge.net/project/showfiles.php?group_id=129083)
If you come up with a solution please post back

---

### Post by trippinnik on 2007-02-11
recently i had to start typing dhclient at the command line to connect.  you should try that. the  other option is to use the zd1211rw driver.  you can get it working by using the 2.6.20 kernel. if your amibitious you could do that: [http://www.ubuntuforums.org/showthread.php?t=354212&highlight=zd1211](http://www.ubuntuforums.org/showthread.php?t=354212&highlight=zd1211)

---

