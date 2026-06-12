---
title: "Unable to configure wireless network connection"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by Lourie2 on 2008-05-03
I am unable to connect to the internet with my Belkin USB Wireless Adapter in Hardy 8.04, yet the same adapter worked fine in Gutsy 7.10.  When I open Wireless Network Drivers via System, Administration, I can see that the windows driver is installed and hardware is present.  I then open the Network settings dialogue box by selecting Configure network.  All connections are grey (perhaps because I haven't entered a password?) but I can see there is a tick next to Wireless connection.  So this way, I am unable to configure the network.

I then have to click on the network icon in the panel and select Manual configuration. (Wired network is grey)  The Network settings dialogue box again opens, all connections are still grey, until after I enter my password.  I can then select the Wireless connection, select Properties and then a bar in another Network Settings box opens and moves to and fro, with a message: Change interface configuration.  That process ends, AND I STILL CANNOT CONNECT TO THE INTERNET!!!

I can also see that my adapter is installed:

```
*-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:1c:df:33:be:0b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+blkwgu driverversion=1.52+Belkin Corporation.,06/01/2 multicast=yes wireless=IEEE 802.11g
```

I am sure about the following:
1. It is the correct driver (It worked previously)
2. The network exists, it sees it, it works, because my Windows laptop connects to it. (I do connect by cable via the router)
3. I enter the SSID and WEP correctly, and have done so over and over.

Please help.

---

### Post by ubume2 on 2008-05-03
Same thing here. I had Ubuntu 6.06 Dapper. The computer crashed & I installed 8.04. I have a Belkin wireless device, a 7050 usb. I think the driver is BLKGWU.inf.

I just got connected. However, I connected using an rt2500usb driver.  Through the help of another on this board I got it going.

Looks like your connection is wlan0.  Mine is eth1.

Do a lshw -C network in the terminal. And then an ifconfig and report back.

---

### Post by Lourie2 on 2008-05-03
Yes, the driver is BLKGWU.inf
```
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 02
       serial: 00:11:25:67:08:b7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.65 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:1c:df:33:be:0b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+blkwgu driverversion=1.52+Belkin Corporation.,06/01/2 multicast=yes wireless=IEEE 802.11g
```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:25:67:08:b7  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe67:8b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53675 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24223860 (23.1 MB)  TX bytes:15832934 (15.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:656 errors:0 dropped:0 overruns:0 frame:0
          TX packets:656 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35794 (34.9 KB)  TX bytes:35794 (34.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:df:33:be:0b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1c:df:33:be:0b  
          inet addr:169.254.5.163  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
```

---

### Post by ubume2 on 2008-05-03
Now I have two computers in the house. One is wired to the dsl modem, and the other is wireless.  This is what I did to connect the wireless computer.  If your connection is not like this, I don t know if it will work.

If you are using WEP this might work. WPA you might have to get further help.

You want to manually configure the wireless. If this method works you shouldnt have to use System>>Network. The wireless would be gray and have a dash -. Mine says not connected.

At the terminal command line enter

sudo ifconfig wlan0 down
sudo dhclient -r wlan0 
sudo ifconfig eth0 up
sudo iwconfig eth0 essid "name of network"    #put in quotes 
#sudo iwconfig eth0 encryption on
sudo iwconfig eth1 key [put your WEP passphrasehere] ASCII KEY  # that is if you use WEP don't but in brackets
sudo dhclient eth0

see if that works. If it does you can create a script. let me know. if you have any problems report back the errors using lshw -C network and ifconfig.

I also notice you have an lo that shows up. If that causes problems, will have to do something else.

---

### Post by Lourie2 on 2008-05-03
Thanks so far. This is what I got.  Problem, I think, is, I enter the code and nothing happens, it goes to the prompt without any extra lines.
```
name@name-IBM:~$ sudo ifconfig wlan0 down
[sudo] password for name: 
name@name-IBM:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1c:df:33:be:0b
Sending on   LPF/wlan0/00:1c:df:33:be:0b
Sending on   Socket/fallback
name@name-IBM:~$ sudo ifconfig wlan0 up
name@name-IBM:~$ sudo iwconfig wlan0 essid "XXXXXXXXXXX"
name@name-IBM:~$ #sudo iwconfig wlan0 encryption on
name@name-IBM:~$ sudo iwconfig wlan0 key 9999999999
name@name-IBM:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1c:df:33:be:0b
Sending on   LPF/wlan0/00:1c:df:33:be:0b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
name@name-IBM:~$
```

```
name@name-IBM:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 02
       serial: 00:11:25:67:08:b7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.65 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:1c:df:33:be:0b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+blkwgu driverversion=1.52+Belkin Corporation.,06/01/2 multicast=yes wireless=IEEE 802.11g
name@name-IBM:~$
```

```
name@name-IBM:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:25:67:08:b7  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe67:8b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82895 (80.9 KB)  TX bytes:30237 (29.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26300 (25.6 KB)  TX bytes:26300 (25.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:df:33:be:0b  
          inet6 addr: fe80::21c:dfff:fe33:be0b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1c:df:33:be:0b  
          inet addr:169.254.5.163  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

name@name-IBM:~$
```

---

### Post by ubume2 on 2008-05-03
I wonder what you have: a Wireless G Router or other on the page: 

[http://catalog.belkin.com/IWCatSectionView.process?Section_Id=200340](http://catalog.belkin.com/IWCatSectionView.process?Section_Id=200340)

I have a Wireless G USB Network Adapter
[http://catalog.belkin.com/IWCatSectionView.process?Section_Id=200340](http://catalog.belkin.com/IWCatSectionView.process?Section_Id=200340)

It might make the setup different. Makes me wonder because nothing happened when you did an ifconfig wlan0 down. 

Did you try ifconfig eth0 up after you did ifconfig wlan0 down?

---

### Post by Lourie2 on 2008-05-03
I have the following: [http://www.belkin.com/uk/support/product/?lid=enu&pid=F5D7050uk&scid=283](http://www.belkin.com/uk/support/product/?lid=enu&pid=F5D7050uk&scid=283) I think it's the same as yours.

Yes, at first I did try ifconfig eth0 up after I did ifconfig wlan0 down. (I took shortcut by copying your code)!  I got a message that I could not do that and repeated the whole procedure you suggested with wlan0.

---

### Post by ubume2 on 2008-05-03
Yes, they look the same.  
Have you gotten it to work?

Looks like both eth0 and wlan:avahi are picking up the inet address.

Since your laptop is apparently wired to the modem router, I would think
that your other computer should work using eth0.[unless there is a driver conflict]

Enter sudo ifconfig wlan0 down
      sudo ifconfig eth0 up
      ifconfig   ##If eth0 shows up but wlan0 doesnt, then try my routine   again       

Best of luck. When you get a command routine that works you can create a script that automates the whole thing.

For me the next big project is to get my Lexmark printer to work on Ubuntu!

---

