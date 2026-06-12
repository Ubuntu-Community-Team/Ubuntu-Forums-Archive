---
title: "wifi networks visible but can't connect"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by duffrecords on 2007-08-14
I have a Netgear MA401RA Eval-RevA which, after some tweaking, seems to be working.  I can see the available networks using > iwlist eth1 scanningso that must mean the card and hostap driver are working.  However, when I try to connect to my network using > sudo iwconfig eth1 essid linksysnothing happens.  No error messages, no nothing.  I ping Google and it fails.  I've tried using network-manager and wifi-radar (with only one installed at a time, because I read they interfere with each other).  When I try to connect using these frontends, either they claim to have connected when they really haven't, they fail and revert back to my wired connection, or Gnome totally freezes and I have to do a hard reboot.  Any suggestions?  Here are my details:

Dell Inspiron 8200
Ubuntu 7.04 (kernel version 2.6.20-16-generic)
hostapd 1:0.5.5-3.1
network-manager 0.6.4-6ubuntu7
wifi-radar 1.9.7-0ubuntu4

sudo pccardctl ident
> Socket 0:
  no product info available
Socket 1:
  product info: "NETGEAR MA401RA Wireless PC", "Card", "ISL37300P", "Eval-RevA"
  manfid: 0x000b, 0x7300
  function: 6 (network)


lshw -C network
>   *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:e0:e5:0f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.103 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: ioport:ec80-ecff iomemory:f8fffc00-f8fffc7f irq:11
  *-network
       description: Card
       product: ISL37300P
       vendor: NETGEAR MA401RA Wireless PC
       physical id: 0
       version: Eval-RevA
       slot: Socket 1
       resources: irq:4
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:09:5b:25:2a:39
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=hostap driverversion=0.4.4-kernel firmware=1.3.6 multicast=yes wireless=IEEE 802.11b

iwconfig
> 
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:04:0C:57   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth1      IEEE 802.11b  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:04:0C:57   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-57 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:44  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:78   Missed beacon:0

ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:08:74:E0:E5:0F  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fee0:e50f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1606 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1503204 (1.4 MiB)  TX bytes:203067 (198.3 KiB)
          Interrupt:11 Base address:0x8c00 

eth1      Link encap:Ethernet  HWaddr 00:09:5B:25:2A:39  
          inet6 addr: fe80::209:5bff:fe25:2a39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14272 (13.9 KiB)  TX bytes:576 (576.0 b)
          Interrupt:4 Base address:0xe100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-09-5B-25-2A-39-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15992 (15.6 KiB)  TX bytes:576 (576.0 b)
          Interrupt:4 Base address:0xe100 

iwlist eth0 scanning
> wifi0     Scan completed :
          Cell 01 - Address: 00:12:17:04:0C:57
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level=-51 dBm  Noise level=-90 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10

---

### Post by grantwfuller on 2007-08-14
I have a similar problem but with a D-Link adapter and router. I have recently installed Ubuntu from the 6.10 CD and would really like to use this OS as opposed to Windows. I am using a Compac Presario desktop that came with Vista, which crashed and I don't want to revive it. I installed wine and ndiswrapper in order to get the driver to work in Ubuntu. The scan shows my network as well as a couple of my neighbours, but signal quality on all is 0/100. The iwconfig command produces this:
myrna@myrna-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

myrna@myrna-desktop:~$ 
I feel like we are so close to success, I hate to give up now.

---

### Post by bmartin on 2007-08-14
Are you using the built-in network manager or wifi-radar to connect? I think that since they both try to control your WiFi devices, they may conflict.

If neither of them is working, try a different wireless connection manager. [wicd]("http://wicd.sourceforge.net/download.php") has been getting good reviews and people have said that it helped them connect where other WCMs had failed. As a bonus, wicd claims to have builn-in WPA support.

---

### Post by kevdog on 2007-08-14
Lets see if we can connect from command line first since I dont know what is wrong with network manager, wifi radar.

Type the following at let me know what happens (if you get file doesn't exist, just keep going, some of the steps are overkill)

Make sure WEP/WPA/Mac Filterfing are turned off.  I want at this point no encryption on the router

```
sudo ifconfig eth1 down
sudo killall dhclient dhclient3
sudo rm /var/run/dhclient.pid
sudo ifconfig eth1 up
sudo iwconfig eth1 essid linksys mode managed
sudo dhclient eth1
```


Why are you getting a wlan0 interface??

---

### Post by grantwfuller on 2007-08-14
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid grant
wireless-key 1234567890

Above is the content of my interfaces file, the command line attempt to connect results in "no such device. The manager I am using is "System>Administration>Network". I did not realize there were other options. (the wireless key above is not real but it is right in the actual file)

---

### Post by grantwfuller on 2007-08-14
I have disabled the router security and am going back to try the problem computer.

---

### Post by grantwfuller on 2007-08-14
myrna@myrna-desktop:~$ sudo ifconfig eth1 down
Password:
eth1: ERROR while getting interface flags: No such device
myrna@myrna-desktop:~$ sudo ifconfig wlan0 down
myrna@myrna-desktop:~$ 

It answered the first command with an error so I tried my own and it won't even answer.

---

### Post by duffrecords on 2007-08-14
Thanks, kevdog, it worked for me.
> ian@Inspiron:~$ sudo ifconfig eth1 down
Password:
ian@Inspiron:~$ sudo killall dhclient dhclient3
dhclient3: no process killed
ian@Inspiron:~$ sudo rm /var/run/dhclient.pid
rm: cannot remove `/var/run/dhclient.pid': No such file or directory
ian@Inspiron:~$ sudo ifconfig eth1 up
ian@Inspiron:~$ sudo iwconfig eth1 essid linksys mode managed
ian@Inspiron:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:09:5b:25:2a:39
Sending on   LPF/eth1/00:09:5b:25:2a:39
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.104 -- renewal in 37188 seconds.
Now if I can just get my mouse pointer to stop drifting to the top right corner I'll be able to enjoy my new wireless card.

---

### Post by duffrecords on 2007-08-15
grantwfuller, your wireless adapter may have a different logical name than "eth1."  To get a list of all wireless devices your system recognizes, type the following:
```
iwconfig
```
You should see a logical name with details about your adapter.  Use that name.  If they all say "no wireless extensions." then it's not configured or it might be disabled.

---

### Post by kevdog on 2007-08-15
Im glad you are happy that this process worked, however unless you want it to be, it isnt the end of the line.  The next step is automation.  Ive confirmed that your network card works, and can connect.  You can run this script if you would like to do it manually, or download a package such as wicd which will do it automatically for you and provide you with a GUI (if you want it).

---

### Post by grantwfuller on 2007-08-15
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

The above is what I get from iwconfig. When I scan for networks, mine comes up. This must mean that the card is receiving transmission? I blacklisted the drivers that were recommended in another  thread. Still no connection. I don't want to give up but I can't think of anything to do.

---

### Post by kevdog on 2007-08-15
grantwfuller

Start a new thread so not to confuse your problem and the one here

Give the following:

lspci -nn
lshw -C network
iwlist scan
ifconfig

Thanks

---

### Post by mgrignoli on 2007-10-02
I see my wifi network configuration without error messages, but I don't see the signal, so I don't get to connect. I read this post and I think that my problem is seem. Wiith the command lshw -> logical name = wifi0 and iwconfig -> wifi is recognizes for ath0. What to do? The different logical name, is really my problem??

---

