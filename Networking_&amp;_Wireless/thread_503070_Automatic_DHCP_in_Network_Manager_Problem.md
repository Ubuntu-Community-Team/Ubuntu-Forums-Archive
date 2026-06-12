---
title: "Automatic DHCP in Network Manager Problem"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by mckenzie on 2007-07-17
I have an intel ipw3945 wireless card that works perfectly from a driver standpoint. However, when connecting to a wireless network by clicking on the Network Manager icon (nm-applet) and selecting my wireless network which is detected, the icon changes to a spinning circle. But, it continues to spin and does not  give my wireless config a network address. However, if I manually open a terminal and run dhclient as root, it works.

If I used the wired port on my laptop, it gets a address via dhcp on boot.

I dont want it to get an address until I select the wireless network I want.Is there any way to "fix" the Network Manager to get an address via dhcp without this manual tweak or will I have to do this until the Gutsy final is released?
P.S- I am running Gutsy but this also failed in feisty

My wired is eth0 and my wireless is eth1, and I dont have a wlan0, ath2 or eth2 (which are listen in /interfaces)

_here is my /etc/network/interfaces:_

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

_Here is my ifconfig output:_
eth0      Link encap:Ethernet  HWaddr  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x4000 Memory:da000000-da020000 

eth1      Link encap:Ethernet  HWaddr
          inet addr:192.168.1.140  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2261 errors:6 dropped:40 overruns:0 frame:0
          TX packets:1580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1560752 (1.4 MB)  TX bytes:253055 (247.1 KB)
          Interrupt:16 Base address:0xe000 Memory:d8000000-d8000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1600 (1.5 KB)  TX bytes:1600 (1.5 KB)

_here is my iwconfig output:_
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:66:9Z:7B:ED   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=78/100  Signal level=-57 dBm  Noise level=-58 dBm
          Rx invalid nwid:0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries:0  Invalid misc:34   Missed beacon:0

---

### Post by kgr132 on 2007-07-17
Same here. Although in my /etc/network/interfaces I've commented out all of the network adapters except lo so that no physical networks are set to auto connect.


EDIT: If I click the network manager icon and choose "Connect to Other Wireless Network..."; 
then give it a fake SSID for a network that isn't there; 
then wait for it to time out and fail to connect (as it should, given the fake SSID); 
then click on the Network Manager icon and choose the network that I do actually want to connect to; 
it connects, obtains an IP via DCHP and works normally.

I don't understand   :(

---

### Post by slashdolt on 2007-07-17
I have just come across the same problem. I've been running Feisty for months on my inspiron 9400 with ipw3945 without any wireless issues, however something caused it to hang last week. At the time I was running WinXP inside Innotek Virtualbox, using the shared folder features. When I rebooted, network-manager refused to get me an IP, as previously described. I wonder if that screwed up some networking settings. A the moment, I run dhclient manually to work around this.

I've tried apt-get removing and reinstalling network-manager and the ipw3945 drivers but the problem is obviously not there. Must be one of those 'easily editable text file' settings somewhere ;).  I really don't want to be reinstalling the system if I don't have to.

P.S. I was also running Beryl w/ Emerald, but I've not had problems with them before. Also, I don't see how crashing would change network settings.

---

### Post by slashdolt on 2007-07-18
Good news - got it fixed. Problem was with dhcp3-cllient, as shown in /var/log/syslog:

> 
Jul 18 13:21:40 localhost NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth1 
Jul 18 13:21:40 localhost dhclient: Can't allocate interface etlease {   interface .
Jul 18 13:21:40 localhost dhcdbd: Unrequested down ?:3

Looking up the error turned up this page:
[http://www.webservertalk.com/message1747058.html]("http://www.webservertalk.com/message1747058.html")

Corrupted dhcp lease entries, perhaps? Could have been that crash as I suspected. Like the poster in that link, I deleted /var/lib/dhcp/* so I can't file a proper bug report :P this is worth investigating if you can have a look at those files. There are a number of related entries in the bugtracker, I think.

Cheers.

---

