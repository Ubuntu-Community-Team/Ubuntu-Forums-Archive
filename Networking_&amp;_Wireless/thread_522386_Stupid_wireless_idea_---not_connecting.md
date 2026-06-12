---
title: "Stupid wireless idea ---not connecting"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by yogo on 2007-08-10
I like many others have had a bundle of problems getting wireless to work. Followed many tutorials and nothing seems to help.

Would using Wine help to install the app that our wireless pci/usb etc cards use. Mine can c see the router and instantly, I can change channels on my router and the Ubuntu box will tell me what channel my router is on.

However I get no working leases in database sleeping error.

I have an EW 7128g pci card that is suppose to work out of the box but it sees the router fine but can not connect!


I am ready to pull out all my hair and this is only day two, I have read others working on this for weeks to a month.

This should not be that hard.

---

### Post by noob12 on 2007-08-10
Wine won't help.

In order to get more help, can you please post the output of these for starters
```

lspci -nn

sudo lshw -C network

iwconfig

iwlist scan

```

---

### Post by yogo on 2007-08-10
Noob12, 

Thanks for the reply, I learned a two new commands (the first two) here are the results, sorry it took awhile as I had to copy and paste to a memory card then transfer as I can not connect.

00:00.0 Host bridge [0600]: Intel Corporation 82810 GMCH [Graphics Memory Controller Hub] [8086:7120] (rev 03)
00:01.0 VGA compatible controller [0300]: Intel Corporation 82810 CGC [Chipset Graphics Controller] [8086:7121] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801AA PCI Bridge [8086:2418] (rev 02)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801AA ISA Bridge (LPC) [8086:2410] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801AA IDE [8086:2411] (rev 02)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801AA USB [8086:2412] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801AA SMBus [8086:2413] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801AA AC'97 Audio [8086:2415] (rev 02)
01:08.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
naty@naty-desktop:/etc$ sudo shw -C network
Password:
sudo: shw: command not found
naty@naty-desktop:/etc$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 8
       bus info: pci@01:08.0
       logical name: ra0
       version: 00
       serial: 00:0e:2e:8a:86:16
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS latency=64 link=yes multicast=yes wireless=RT61 Wireless
       resources: iomemory:f4100000-f4107fff irq:9
naty@naty-desktop:/etc$ iwconfig
lo        no wireless extensions.

ra0       RT61 Wireless  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=88/100  Signal level:-51 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

naty@naty-desktop:/etc$ 
naty@naty-desktop:/etc$ iwlist scan
lo        Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:16:01:27:7A:7B
                    ESSID:"001601277A7A"
                    Mode:Managed
                    Channel:1
                    Encryption key:on
                    Quality:0/100  Signal level:-40 dBm  Noise level:-256 dBm


I am not sure why those smilies are there, perhaps the board as i saw someone refer to the use of smilies earlier

---

### Post by yogo on 2007-08-10
What bugs me is the card is correctly identified but in network tools it says unknown ra0 device????

---

### Post by noob12 on 2007-08-10
If you have a hard line, you may find that easier than sneaker-net with the usb flash.  You may also need to download stuff.

OK.  Make a note of the fact that you have an Ralink RT61 PCI-based card.  We may find that you need to download and build more recent drivers for this card.

It seems to be scanning so we'll try to proceed with the shipped drivers.

Are you running Feisty?

Are you using NetworkManager?
```

aptitude show network-manager network-manager-gnome knetworkmanager | grep State

ps -ef | grep -e '(NetworkManager|nm-applet)' | grep -v grep

```

To avoid sneaker-net you can just tell me if the first command shows Installed for the first two items, and for the second command just tell me whether you get lines showing both NetworkManager and nm-applet.

Is "001601277A7A" the router you want to connect to?   Are you using WEP or WPA on it?
Do you control this router?  If so,  can you turn encryption off to test initially?

---

### Post by yogo on 2007-08-10
> **noob12 said:**
> If you have a hard line, you may find that easier than sneaker-net with the usb flash.  You may also need to download stuff.

OK.  Make a note of the fact that you have an Ralink RT61 PCI-based card.  We may find that you need to download and build more recent drivers for this card.

It seems to be scanning so we'll try to proceed with the shipped drivers.

Are you running Feisty?

Are you using NetworkManager? 


Is "001601277A7A" the router you want to connect to?   Are you using WEP or WPA on it?
Do you control this router?  If so,  can you turn encryption off to test initially?

Yes I am using Network manager and am running Feisty 7.04

it is my router and I have turned on and off encryption  and have left it off to simplify things.

---

### Post by yogo on 2007-08-10
PS I do not have knetworkmanager Do I need it and where? If so I will download it and add it. I am stepping out for a while but if you have any suggestions, I will do them all faithfully when I return.

Thanks I appreciate your help.

---

### Post by ugm6hr on 2007-08-10
This thread might help you:
[http://ubuntuforums.org/showthread.php?t=415693&page=3](http://ubuntuforums.org/showthread.php?t=415693&page=3)

Make sure you read the whole thread - since it depends on another tutorial to start with.

---

### Post by noob12 on 2007-08-10
No you don't need knetworkmanager.  That's for KDE/Kubuntu.

With the encryption off.  You should try the following:

Right-click on the NetworkManager (NM) icon -- this is the dual-computer icon in the notification area, typically upper right).  Select Enable wireless.  The check mark should be on.  Now left-click on the NM icon.  You should get a signal bar showing your wireless.  Left click on that.  You should connect.

If not, please describe in detail what happens.

---

### Post by yogo on 2007-08-10
> **noob12 said:**
> No you don't need knetworkmanager.  That's for KDE/Kubuntu.

With the encryption off.  You should try the following:

Right-click on the NetworkManager (NM) icon -- this is the dual-computer icon in the notification area, typically upper right).  Select Enable wireless.  The check mark should be on.  Now left-click on the NM icon.  You should get a signal bar showing your wireless.  Left click on that.  You should connect.

If not, please describe in detail what happens.



I can connect like that and have 5 bars and the signal strength is most times 100%, I have never see it fall below 96% but YET I can not connect to google or ping any website.

In fact two days ago, after installing the wireless card, I could connect like that but it's not connected.

I think I want to start from scratch, ditch all the old stuff even though it has just been done in the last two days and add everything new to the correct folder.Are there better drivers like from serial monkey, I have read their tutorial but it is not for the rt61, will it work?

I have installed so many things things and looked at so many tutorials that I am sure things are quirked out.

My idea is to use nautilus to copy the files from a usb stick and add them that way, I have so much trouble trying to do it from command line since I have no Internet. Does this sound right?

Thanks

---

### Post by yogo on 2007-08-10
Ok I found the rt61 cvs from serialmonkey, should I use that one and follow their tutorial for RT73..? not sure if that is the exact # as it does not correspond to me.

---

### Post by yogo on 2007-08-10
I think I am getting there BUT I have know idea where the rt61.ko driver file is as it has not been in any of the packages and it is not found in /lib/modules/2.6.20-15 generic/kernel/drivers/hotplug/ so I am at a loss for where it went to. I did add an inf file yesterday so it probably grabbed the rt61.fo....?

---

### Post by noob12 on 2007-08-10
Well, OK.  Before you go uninstalling and installing a bunch of stuff, you might want to figure out what's happening.  Maybe it's minor, or maybe you do need to get drastic.

Once you've got the signal bars and selected that wireless, and connected, you say you can't reach internet sites.  Can you show us the output of these?
```

ifconfig -a

ps -ef | grep dhclient

cat /etc/resolv.conf

host www.yahoo.com

ping www.yahoo.com

route -n

```

---

### Post by yogo on 2007-08-10
Here they are

No working leases in persistent database - sleeping.
naty@naty-desktop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

ra0       Link encap:Ethernet  HWaddr 00:0E:2E:8A:86:16  
          inet6 addr: fe80::20e:2eff:fe8a:8616/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15473 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:929092 (907.3 KiB)  TX bytes:612 (612.0 b)
          Interrupt:9 

ra0:avahi Link encap:Ethernet  HWaddr 00:0E:2E:8A:86:16  
          inet addr:169.254.4.143  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:9 

naty@naty-desktop:~$ ps -ef ! grep dhclient
ERROR: Garbage option.
********* simple selection *********  ********* selection by list *********
-A all processes                      -C by command name
-N negate selection                   -G by real group ID (supports names)
-a all w/ tty except session leaders  -U by real user ID (supports names)
-d all except session leaders         -g by session OR by effective group name
-e all processes                      -p by process ID
T  all processes on this terminal     -s processes in the sessions given
a  all w/ tty, including other users  -t by tty
g  OBSOLETE -- DO NOT USE             -u by effective user ID (supports names)
r  only running processes             U  processes for specified users
x  processes w/o controlling ttys     t  by tty
*********** output format **********  *********** long options ***********
-o,o user-defined  -f full            --Group --User --pid --cols --ppid
-j,j job control   s  signal          --group --user --sid --rows --info
-O,O preloaded -o  v  virtual memory  --cumulative --format --deselect
-l,l long          u  user-oriented   --sort --tty --forest --version
-F   extra full    X  registers       --heading --no-heading --context
                    ********* misc options *********
-V,V  show version      L  list format codes  f  ASCII art forest
-m,m,-L,-T,H  threads   S  children in sum    -y change -l format
-M,Z  security data     c  true command name  -c scheduling class
-w,w  wide output       n  numeric WCHAN,UID  -H process hierarchy
[B]naty@naty-desktop:~$ cat /etc/resolv.conf
search rgv.rr.com[/B]
naty@naty-desktop:~$ host [www.yahoo.com](www.yahoo.com)
;; connection timed out; no servers could be reached
naty@naty-desktop:~$ ping [www.yahoo.com](www.yahoo.com)
ping: unknown host [www.yahoo.com](www.yahoo.com)
naty@naty-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 ra0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 ra0
naty@naty-desktop:~$ 

And what I put in bold is my ISP, correctly identified.

---

### Post by yogo on 2007-08-10
I just restarted my router and I heard a beep from the other pc, I assume a critical beep but it was short, anyways my Ubuntu froze and I could not do anything so I restarted it. The only thing I did differently was I copied the rt61.ko to the /etc/wireless/RT61_STA folder as outlined in the tutorial....maybe h=just a coincident.

---

### Post by noob12 on 2007-08-10
The symbol after the ps command was a vertical bar (|) not an exclamation point (!).

Your situation is that you seem to have an association to the router but you don't have an IP address assigned.  We were trying to figure out why.

Try these again.  Cut and paste should work, if you retype, notice the symbol is a vertical bar, not an exclamation point.
```

ps -ef | grep dhclient

grep dhclient /var/log/syslog | tail -50

```

You seem to be engaged in a parallel effort of installing drivers.  It may be best to do one at a time.

---

### Post by yogo on 2007-08-10
Sorry about that here goes

naty@naty-desktop:~$ ps -ef | grep dhclient
naty      5804  5772  0 19:54 pts/0    00:00:00 grep dhclient
naty@naty-desktop:~$ grep client /var/log/syslog | tail -50
Aug 10 18:49:44 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
Aug 10 18:49:51 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
Aug 10 18:50:02 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
Aug 10 18:50:15 naty-desktop dhclient: No DHCPOFFERS received.
Aug 10 18:50:15 naty-desktop dhclient: No working leases in persistent database - sleeping.
Aug 10 18:54:31 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
Aug 10 18:54:39 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
Aug 10 18:54:54 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
Aug 10 18:55:02 naty-desktop dhclient: No DHCPOFFERS received.
Aug 10 18:55:02 naty-desktop dhclient: No working leases in persistent database - sleeping.
Aug 10 18:59:55 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
Aug 10 19:00:02 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18
Aug 10 19:00:20 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
Aug 10 19:00:26 naty-desktop dhclient: No DHCPOFFERS received.
Aug 10 19:00:26 naty-desktop dhclient: No working leases in persistent database - sleeping.
Aug 10 19:06:58 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
Aug 10 19:07:05 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
Aug 10 19:07:14 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
Aug 10 19:07:23 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
Aug 10 19:07:29 naty-desktop dhclient: No DHCPOFFERS received.
Aug 10 19:07:29 naty-desktop dhclient: No working leases in persistent database - sleeping.
Aug 10 19:10:55 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
Aug 10 19:10:59 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
Aug 10 19:11:07 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
Aug 10 19:11:21 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
Aug 10 19:11:26 naty-desktop dhclient: No DHCPOFFERS received.
Aug 10 19:11:26 naty-desktop dhclient: No working leases in persistent database - sleeping.
Aug 10 19:11:46 naty-desktop dhclient: receive_packet failed on ra0: Network is down
Aug 10 19:11:46 naty-desktop avahi-autoipd(ra0)[5147]: client: RTNETLINK answers: No such process
Aug 10 19:17:15 naty-desktop dhclient: receive_packet failed on ra0: Network is down
Aug 10 19:17:42 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
Aug 10 19:17:49 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
Aug 10 19:17:58 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
Aug 10 19:18:08 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
Aug 10 19:18:13 naty-desktop dhclient: No DHCPOFFERS received.
Aug 10 19:18:13 naty-desktop dhclient: No working leases in persistent database - sleeping.
Aug 10 19:21:35 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
Aug 10 19:21:41 naty-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
Aug 10 19:28:12 naty-desktop dhclient: There is already a pid file /var/run/dhclient.ra0.pid with pid 3740
Aug 10 19:28:12 naty-desktop dhclient: killed old client process, removed PID file
Aug 10 19:28:12 naty-desktop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Aug 10 19:28:12 naty-desktop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Aug 10 19:28:12 naty-desktop dhclient: All rights reserved.
Aug 10 19:28:12 naty-desktop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug 10 19:28:12 naty-desktop dhclient: 
Aug 10 19:28:12 naty-desktop dhclient: Listening on LPF/ra0/00:0e:2e:8a:86:16
Aug 10 19:28:12 naty-desktop dhclient: Sending on   LPF/ra0/00:0e:2e:8a:86:16
Aug 10 19:28:12 naty-desktop dhclient: Sending on   Socket/fallback
Aug 10 19:28:12 naty-desktop dhclient: DHCPRELEASE on ra0 to 192.168.11.1 port 67
Aug 10 19:28:22 naty-desktop avahi-autoipd(ra0)[5083]: client: RTNETLINK answers: No such process
naty@naty-desktop:~$

---

### Post by yogo on 2007-08-10
Just to make sure I am doing this right here is what I have in /etc/wireless/RT61_STA

rt2561.bin      rt2561s.bin    rt2661.bin    rt61sta.dat and I added rt61.ko and when that did not work I also add rt61pci.ko  The two .ko drivers are copied from lib/modules/kernel/ubuntu/wireless

This was from the tutorial on setting up this card linked on the first page of this thread.

Hope this is right

---

### Post by noob12 on 2007-08-10
It looks like you just recently put the interface down and the DHCP process for ra0 was stopped.  If you know the IP address of your router, you should try pinging it when your wireless is connected.  If not, you probably do need to work on the drivers.

I don't really know what you're doing or trying to do with the drivers; I can't help you there.  Maybe someone else on the forum can pitch in.  Good luck.

---

### Post by yogo on 2007-08-10
> **noob12 said:**
> It looks like you just recently put the interface down and the DHCP process for ra0 was stopped.  If you know the IP address of your router, you should try pinging it when your wireless is connected.  If not, you probably do need to work on the drivers.

I don't really know what you're doing or trying to do with the drivers; I can't help you there.  Maybe someone else on the forum can pitch in.  Good luck.
  

I am not sure exactly what happened, BUT I HAVE CONNECTED TO THE INTERNET really I am not shouting but am happy.  I tried to ping my router just 15 minutes ago and got network not recognized. Something magically clicked and I am back on.


Now I am crossing my fingers that I can shutdown and bring the pc back to my wife's room and she will have Internet.

As for now I am connected. Noob12, thanks for all the help and pointing me in the right directions. Also thanks to ugm6hr for the link as everything came together.

I just wish I knew what clicked!!

---

### Post by yogo on 2007-08-10
Well at least I know it will work, I am back to square one, Although my leases are showing up good when I sudo dhclient ra0 It shows that lease will be renewed in about 80,000 seconds.


If I only knew what got it to engage the first time!

I am now connected and when I check connection status, I get an error with no glade file, I have not done anything with a glade file and this goes away sometimes it will show me the status, other times it says the glade file is missing?

---

### Post by yogo on 2007-08-10
I am on the wireless and posting-----Where does the system pull the driver from? Is it in lib/modules/kerel/ubuntu/wireless or is it in the /etc/wireless/RT61STA directory that was created. In the first, there are a ton of drivers and maybe they are competing as it is difficult but I can connect and it does not drop connections as far as I can tell.

Thanks

---

### Post by yogo on 2007-08-10
I figured I would copy the commands Noob12, that you asked me to do earlier and show how it looks when connected, maybe you can see what is wrong and where to fix.

Hope this is not redundant.

naty@naty-desktop:~$ iwconfig
lo        no wireless extensions.

ra0       RT61 Wireless  ESSID:"001601277A7A"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:01:27:7A:7B   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=94/100  Signal level:-45 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

naty@naty-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:700 (700.0 b)  TX bytes:700 (700.0 b)

ra0       Link encap:Ethernet  HWaddr 00:0E:2E:8A:86:16  
          inet addr:192.168.11.3  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe8a:8616/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1986 errors:2 dropped:2 overruns:0 carrier:0
          collisions:17 txqueuelen:1000 
          RX bytes:3465262 (3.3 MiB)  TX bytes:277114 (270.6 KiB)
          Interrupt:9 

naty@naty-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82810 GMCH [Graphics Memory Controller Hub] [8086:7120] (rev 03)
00:01.0 VGA compatible controller [0300]: Intel Corporation 82810 CGC [Chipset Graphics Controller] [8086:7121] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801AA PCI Bridge [8086:2418] (rev 02)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801AA ISA Bridge (LPC) [8086:2410] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801AA IDE [8086:2411] (rev 02)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801AA USB [8086:2412] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801AA SMBus [8086:2413] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801AA AC'97 Audio [8086:2415] (rev 02)
01:08.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
naty@naty-desktop:~$ 
naty@naty-desktop:~$ sudo lshw -C network
Password:
  *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 8
       bus info: pci@01:08.0
       logical name: ra0
       version: 00
       serial: 00:0e:2e:8a:86:16
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS ip=192.168.11.3 latency=64 link=yes multicast=yes wireless=RT61 Wireless
       resources: iomemory:f4100000-f4107fff irq:9
naty@naty-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:16:01:27:7A:7B
                    ESSID:"001601277A7A"
                    Mode:Managed
                    Channel:1
                    Encryption key:off
                    Quality:82/100  Signal level:-36 dBm  Noise level:-256 dBm

naty@naty-desktop:~$

---

### Post by ugm6hr on 2007-08-11
Does this mean your problem is solved?  I'm a bit confused...
> configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS
This part of *lshw -C network* shows that you are using the correct driver.  And the *ifconfig* tells us its working (albeit with 2 errors - not significant, I think).

If it doesn't work at some point following a reboot (or whatever) - try this again (when not working):
```
lshw -C network
```
If it lists something different in the *driver=....* section, then there is obviously a driver conflict.  It would merely be a case of blacklisting the offending driver (add it to */etc/modprobe.d/blacklist*).

Let us know exactly what's going on.  I don't have a RT61 card - but it does definitely work with Linux, and is perhaps one of the best-supported chipsets; it is unfortunate that Feisty doesn't have the correct driver built-in.

Just so that you know - Wicd is currently being developed to work with RT61 cards: [http://wicd.sourceforge.net/phpbb/viewtopic.php?f=3&t=134&st=0&sk=t&sd=a&sid=a317014752194e48d61eedfa3568e39e&start=130](http://wicd.sourceforge.net/phpbb/viewtopic.php?f=3&t=134&st=0&sk=t&sd=a&sid=a317014752194e48d61eedfa3568e39e&start=130)

---

### Post by yogo on 2007-08-11
Yes I have got it working from about 70 feet away at around 64% four bars and that is good.

I am having a bit of trouble getting it going, are there other commands to get the driver up?
I have been using lshw -C network, and a few others the ifdown and ifup and auot commands are not found so do I need another package?

It is on and working Plus I just noticed there is a refresh button on the loopback interface lo found in network tools, will this refresh or bring it back up.

ugm6hr, Thanks for your help and that link you provided was great.

---

### Post by kevdog on 2007-08-11
Not to cut in here at the last minute, but did you ever compile and install the serial monkey rt61 drivers?? Its seems you haven't.  Although you are getting an spotty internet connection, I really would encourage you to go ahead and install the serial monkey drivers (if not done so).

Can you also post the following:
modinfo rt61

Thanks.

---

### Post by yogo on 2007-08-11
> **kevdog said:**
> Not to cut in here at the last minute, but did you ever compile and install the serial monkey rt61 drivers?? Its seems you haven't.  Although you are getting an spotty internet connection, I really would encourage you to go ahead and install the serial monkey drivers (if not done so).

Can you also post the following:
modinfo rt61

Thanks.


You are not butting in, I appreciate all the help I can get. I did download the serialmonkey but no I did not add it. What would I replace? the .bin and .dat and ko or do I use the INF file from NDISwrapper?

Thanks

Also, where is the driver being loaded from? I created a directory /etc/wireless/RT61STA but then there is also /lib/modules/kernel/ubuntu/wireless/xxxxxxx/rt61/

---

### Post by yogo on 2007-08-11
i think I got my answer from the modinfo....

filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt61/rt61.ko
license:        GPL
description:    Ralink RT61 802.11abg WLAN Driver 1.1.0 CVS CVS
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     180F8980D3385B365E8F654
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (int)
parm:           ifname:Network device name (default ra%d) (charp)

---

### Post by yogo on 2007-08-11
Is that the latest? see post directly above.

---

### Post by kevdog on 2007-08-11
I was wondering the same thing myself.  It looks like the latest build, when compared to mine.  You downloaded the sources, did you ever issue a:
sudo make install command

If you did Im sure then those drivers are the latest.

Assuming they are the latest, I believe the problem you are having is with not being used a dhcp lease??

Could you post two things and then I can actually be in a postion to help you:
lshw -C network
/etc/network/interfaces

Thanks

---

### Post by yogo on 2007-08-11
*-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 8
       bus info: pci@01:08.0
       logical name: ra0
       version: 00
       serial: 00:0e:2e:8a:86:16
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS ip=192.168.11.3 latency=64 multicast=yes wireless=RT61 Wireless
       resources: iomemory:f4100000-f4107fff irq:9




auto lo
iface lo inet loopback

#iface ra0 inet dhcp
#wireless-essid xxxx
#auto ra0


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

[I]iface ra0 inet static
wireless-essid 001601277A7A
address 192.168.11.1
netmask 255.255.255.0
gateway 192.168.11.3

auto ra0[/I]


What is in italic, is what I added new, no I did not do a make install as I had no internet so it was manually done by me. I left the original stuff included in the interfaces as I did not know if I should delete that.

I did use a static ip and it has been up all day, it has never dropped a connection, but sometimes is hard to connect, it seems to connect by hap and circumstance. It seems that running some commands help from terminal.

Any ideas are greatly appreciated.

Thanks Kevdog.

---

### Post by kevdog on 2007-08-12
Im basically referencing this thread: I know it has been posted before:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

Again if you have no internet access, you will need to find a computer with internet access (your own if it works) that you need to download one file and transfer via USB stick.  I know the instructions are for rt73, but just substitute 61 for 73.  Also use some common sense.  If they tell you to blacklist rt61 -- do not, blacklist rt73 instead since you want to use the rt61 driver.

I would highly recommend you doing this approach.  Yes its best if you have an internet connection, but it can be done with another computer and an install disk if possible.  Read the entire instructions (just the first post) about 3 times before doing anything, then proceed.  The whole process, although it seems intimidating should take you about 15 minutes.

Ill help you out as best as I can.  I dont have an ra chipset, but did as a drill compiled and installed the driver on my machine.  I just dont have a way to test if it works.  I know however for a fact with at least the ten people I have helped with this chipset, they all got it to work, although in one case WPA didnt work for one person.  Please note that WPA2 will not work for any ra based driver (new or old) at this point, so if this feature is a must for you, you need a new networking card.

---

