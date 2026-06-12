---
title: "Wi-Fi on a Packard Bell Easynote A5 with Gutsy 7.10 ?"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by jwt123 on 2008-01-19
Hi , a somewhat frustrated newbie here trying to get wireless working on a Packard Bell laptop and I should say first that I apologise
for the long-winded nature of this post but I have spent quite alot of time trying to resolve this myself, also this laptop came into my
possesion from my folks after the hdd failed. I replaced the drive and added some additioanl memory but this is a experiment for me in Linux
and so far apart from the difficulties I am having with wireless I quite like it. 

I have found a windows driver that allegedly works with ndiswrapper, however when I install driver with ndisgtk
the Wi-Fi led instantly goes out but if I run ndiswrapper -l I get the following
jeff@jeff-laptop:~$ ndiswrapper -l
neti2220 : driver installed
        device (17FE:2220) present

If I then restart the laptop the wi-fi led remains on and ndiswrapper -l returns the same as above which would imply the driver is ok yes?
When I run lshw at this point I get the following:
 *-network:1 UNCLAIMED
                description: Ethernet controller
                product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
                vendor: Linksys, A Division of Cisco Systems
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64 maxlatency=32 mingnt=32


So at this point I try and load ndiswrapper by typing the following commands

sudo depmod -a
sudo modprobe ndiswrapper

When I run the modprobe command the wireless led goes out again! however if I run lshw again I get the following
           *-network:1
                description: Wireless interface
                product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
                vendor: Linksys, A Division of Cisco Systems
                physical id: 4
                bus info: pci@0000:02:04.0
                logical name: wlan0
                version: 00
                serial: 00:11:e2:02:51:a3
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+neti2220 driverversion=1.45+INPROCOMM,02/24/2005,3.07.0 latency=64 maxlatency=32 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

Which to me as a newbie suggests the driver is ok.So at this point if I run iwconfig or ifconfig I get the following

jeff@jeff-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:0 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0/100  Signal level:56/154  Noise level:160/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jeff@jeff-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:74:D3:0A  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe74:d30a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7793 (7.6 KB)  TX bytes:7347 (7.1 KB)
          Interrupt:5 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:11:E2:02:51:A3  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:e0207000-e0207800 

I currently have my router set up with no security, and have re-installed windows on the laptop earlier [no dual-boot for me:-)]
and successfully connected so I know the hardware works ok.

So basically I am wondering if anyone has one of these laptops and has got wi-fi working or if anyone can give me some pointers on
where to go next. I found some intersting stuff in this card/laptop:

[http://pwrdesc.free.fr/](http://pwrdesc.free.fr/) This guy got Mandriva 2005 working fine almost out of the box (obviously knows alot more about Linux than me!) 
so I thought I'd give Mandriva 2008 a go but had very similar problems with the led going off and not seeing any wireless n/w's etc. ( Plus 
I didn't like the look of it as much as ubuntu)

In the ubuntu forums I found the following post that describes someone who eventually got the Inprocomm IPN 2220 working on a different 
model laptop.

[http://ubuntuforums.org/showthread.php?t=586414&highlight=Inprocomm](http://ubuntuforums.org/showthread.php?t=586414&highlight=Inprocomm)

but I have still been unsuccessful in connecting to my wireless network. The fact the LED goes out leads me to believe that the wi-fi card
is being disabled when I load ndiswrapper which then led me down the road of looking at section 3.2.6 in the following article about the
S/W or H/W Function key combinations especially as there is a sw download on the Packard Bell website for Easykeys or something like that for Windows.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#driver](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#driver)

Which in turn led me too the following link

[http://sourceforge.net/project/showfiles.php?group_id=108766](http://sourceforge.net/project/showfiles.php?group_id=108766)

so I downloaded the file (aware of the fact that it refers to a Easynote E5 not an A5!) and run the command suggested

% dd if=/dev/mem bs=1 skip=983040 count=65535 2>/dev/null | strings | egrep "NEW-PC|Insyde Software MobilePRO BIOS"

but get nothing back so I am assuming that loading the pbe5 module won't help me.

So if anyone has gor the same model laptop and has managed to get wireless working or fancies a challenge please get in touch.
I should add that I now have the wired n/w plugged in so that I can post the results off my efforts but had exactly the same problems
when the wired n/w was not connected.

---

