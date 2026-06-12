---
title: "Wireless: can't connect via DHCP"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by skadoo on 2007-08-16
Hi.

I'm having problems with a new wireless card -- the Ambicom WL1100C-CF compact flash card.

Everything seems to be fine with the driver:

> # lshw

  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:10:7a:71:9f:bf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=hostap driverversion=0.4.4-kernel firmware=1.8.0 multicast=yes wireless=IEEE 802.11b

> # lsmod | grep hostap

hostap_cs              62996  3 
hostap                114820  1 hostap_cs
ieee80211_crypt         7040  1 hostap
pcmcia                 39596  2 orinoco_cs,hostap_cs
pcmcia_core            41624  5 orinoco_cs,hostap_cs,pcmcia,yenta_socket,rsrc_nonstatic


> # iwconfig

lo        no wireless extensions.

eth1      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"test"  Nickname:""
          Mode:Managed  Frequency:2.467 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
wlan0     IEEE 802.11b  ESSID:"test"  Nickname:""
          Mode:Managed  Frequency:2.467 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-73 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:402   Missed beacon:0


And iwlist wlan0 scanning returns plenty of hosts.

In my /etc/network/interfaces file, i have:

> auto wlan0
iface wlan0 inet dhcp

But when i try to connect to the network:

> wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wlan0/00:10:7a:71:9f:bf
Sending on   LPF/wlan0/00:10:7a:71:9f:bf
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wlan0/00:10:7a:71:9f:bf
Sending on   LPF/wlan0/00:10:7a:71:9f:bf
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
   ...done.

This is a minimal command line system, so unfortunately I can't use Network Manager, or any other GUI tools.

Any help or suggestions would be welcome!

---

### Post by kevdog on 2007-08-16
Can you post iwlist scan and tell us what AP you are trying to connect to??

The AP listed in iwconfig for wlan0 shows a signal quality of zero!!

---

### Post by skadoo on 2007-08-16
Thanks for the quick reply.

> # iwlist scan:

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wifi0     Scan completed :
          Cell 01 - Address: 00:0B:86:80:F7:40
                    ESSID:"Kiewit Wireless"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Signal level=-53 dBm  Noise level=-78 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
          Cell 02 - Address: D6:4E:CA:C1:36:5F
                    ESSID:"Wireless Network"
                    Mode:Ad-Hoc
                    Frequency:2.412 GHz (Channel 1)
                    Signal level=-77 dBm  Noise level=-78 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
                    Extra:atim=20563
          Cell 03 - Address: 00:0B:86:82:D6:70
                    ESSID:"Kiewit Wireless"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Signal level=-63 dBm  Noise level=-74 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
          Cell 04 - Address: 00:0B:86:C4:54:E0
                    ESSID:"Kiewit Wireless"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Signal level=-69 dBm  Noise level=-73 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
          Cell 05 - Address: 00:0B:86:C4:56:C0
                    ESSID:"Kiewit Wireless"
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Signal level=-69 dBm  Noise level=-75 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
          Cell 06 - Address: 00:0B:86:C4:5D:E0
                    ESSID:"Kiewit Wireless"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Signal level=-74 dBm  Noise level=-79 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
          Cell 07 - Address: 00:0B:86:C4:52:20
                    ESSID:"Kiewit Wireless"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Signal level=-77 dBm  Noise level=-79 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10

wlan0     Scan completed :
          Cell 01 - Address: 00:0B:86:80:F7:40
                    ESSID:"Kiewit Wireless"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Signal level=-54 dBm  Noise level=-77 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
          Cell 02 - Address: D6:4E:CA:C1:36:5F
                    ESSID:"Wireless Network"
                    Mode:Ad-Hoc
                    Frequency:2.412 GHz (Channel 1)
                    Signal level=-76 dBm  Noise level=-78 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
                    Extra:atim=20563
          Cell 03 - Address: 00:0B:86:82:D6:70
                    ESSID:"Kiewit Wireless"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Signal level=-59 dBm  Noise level=-75 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
          Cell 04 - Address: 00:0B:86:C4:54:E0
                    ESSID:"Kiewit Wireless"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Signal level=-71 dBm  Noise level=-75 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
          Cell 05 - Address: 00:0B:86:C4:56:C0
                    ESSID:"Kiewit Wireless"
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Signal level=-73 dBm  Noise level=-75 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
          Cell 06 - Address: 00:0B:86:C4:5D:E0
                    ESSID:"Kiewit Wireless"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Signal level=-76 dBm  Noise level=-78 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10

I'm not sure what AP I'm trying to connect to. (What's an AP...!?) I'm basically just replicating a setup I had for my previous wireless card, which worked fine (until I needed the PCMCIA slot for something else...)

---

### Post by kevdog on 2007-08-16
AP = access point

Try the following (dont worry if you get some errors until the end -- its kind of redundant and overkill)
```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo killall dhclient dhclient3
sudo rm /var/run/dhclient.pid
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "Name of ESSID in Quotes" mode Managed
sudo dhclient wlan0

```

If you are trying to connect to "Kiewit Wireless"- there could be a potential problem since the essid name has a space.

---

### Post by skadoo on 2007-08-16
That did it, thanks!

I added these lines to the wlan0 entry in /etc/network interfaces:

> wireless-mode managed
wireless-essid "Kiewit Wireless"

But there was no DHCP connection after a reboot. Is there something else I should do to bring the network up at startup?

Thanks again for your help with this.

---

### Post by kevdog on 2007-08-16
Im not sure what you mean??

That did it!! <-- What worked??? 

Please post your /etc/network/interfaces file.

---

### Post by skadoo on 2007-08-16
> Im not sure what you mean??

That did it!! <-- What worked??? 

I followed your instructions line by line, and I got a network connection.

> Please post your /etc/network/interfaces file.

```
# The loopback network interface
auto lo
iface lo inet loopback

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
        wireless-mode managed
        wireless-essid "Kiewit Wireless"

auto eth0
iface eth0 inet static
       address 192.168.1.40
       netmask 255.255.255.0
       broadcast 192.168.1.255
       gateway 192.168.1.1
```

---

### Post by kevdog on 2007-08-16
Two reasons it may not run at boot

#1. Cant run wired and wireless at the same time.  You would have to boot with ethernet cable not hooked in.

#2. In some cases (I dont know why) you need to restart the networking bus after boot:
sudo /etc/init.d/networking restart

Dont know why exactly but let me know what you find out!

---

### Post by skadoo on 2007-08-16
Well, the behavior is a little weird. I unplugged ethernet and commented out the eth1 entry in /etc/network/interfaces, but no matter how many times I reboot or restart the network, I can't get a wireless connection.

If, however, I utter the following in a shell:

# iwconfig wlan0 essid "Kiewit Wireless" mode managed
# dhclient wlan0

it connects every time.

I thought that adding essid and mode entries to /etc/network/interfaces would do the same thing, but apparently not.

This machine is going to run embedded, without a keyboard or monitor, so connecting to the network at startup is important. I guess I could put the iwconfig and dhclient commands in a login script, but that seems pretty hacky...

---

### Post by kevdog on 2007-08-16
Ive got to say that it is very strange.  

I assume you have network-manager-gnome installed???
Are you getting any errors when you check dmesg|more that might help.


If you do have network manager installed (which means its not working appropriately), you could always opt out for wicd.  Wicd is another networking program that should start at startup and provide a connection.  I understand how wicd works down below a little better than network manager, but its another alternative that you could try.  If you opt for this version I would elect to install the 1.3.3 version that you have to download from sourceforge over the 1.3.1 version that is contained in the repositories.

Can you try switching the wireless-mode and wireless-essid lines around to see if that makes any difference??

---

### Post by skadoo on 2007-08-18
Hi again.

Apologies for the hiatus...

This is an embedded command-line system running from a tiny flash drive, so I only have a minimal X and fluxbox installed (no network-manager-gnome or wicd...).

I've actually changed a few things around, and have gone back to my old wireless card for DHCP, and I'm planning on using the flash card only in ad-hoc mode. But (surprise, surprise...) I'm still having problems making a connection.

But it's a different problem, so I might start a new thread.

Thanks for all your help with this.

---

