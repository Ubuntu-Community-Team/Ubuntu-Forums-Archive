---
title: "Help with WPA, ifconfig etc inside"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by distortedecho on 2007-10-27
I've got Ubuntu 7.10, and glad to see WPA within the options, something I couldn't get working in the previous version I was using (edubuntu).

However, I still can't get on to my wireless network, despite following the thorough HowTo on WPA on the forum.

Here are the details I can provide, if some one would be so kind as to analyze them and point out what's wrong??

*******************Terminal Stuff*************************
```
richard@richard-laptop:~$ su
Password: 
root@richard-laptop:/home/richard# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:02:D6:3C:3B  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fed6:3c3b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:20132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11597 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27059487 (25.8 MB)  TX bytes:927118 (905.3 KB)

eth1      Link encap:Ethernet  HWaddr 00:0C:30:E9:7A:4C  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:10 dropped:0 overruns:0 frame:10
          TX packets:1 errors:7 dropped:0 overruns:0 carrier:7
          collisions:114 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:12798 (12.4 KB)
          Interrupt:3 Base address:0x2100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-0C-30-E9-7A-4C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST MULTICAST  MTU:2312  Metric:1
          RX packets:0 errors:10 dropped:0 overruns:0 frame:10
          TX packets:1 errors:7 dropped:0 overruns:0 carrier:7
          collisions:114 txqueuelen:100 
          RX bytes:0 (0.0 b)  TX bytes:12798 (12.4 KB)
          Interrupt:3 Base address:0x2100 

root@richard-laptop:/home/richard# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:14:7F:B8:E4:86
                    ESSID:"BTHomeHub-CACE"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=72/100  Signal level=-59 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:17:3F:65:CC:BA
                    ESSID:"S3cur3 4s ****"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=100/100  Signal level=-41 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100

wifi0     No scan results

root@richard-laptop:/home/richard# ifconfig wifi0 up
root@richard-laptop:/home/richard# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

wifi0     Scan completed :
          Cell 01 - Address: 00:14:7F:B8:E4:86
                    ESSID:"BTHomeHub-CACE"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/100  Signal level=-63 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:17:3F:65:CC:BA
                    ESSID:"S3cur3 4s ****"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=100/100  Signal level=-40 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100

root@richard-laptop:/home/richard# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"S3cur3 4s ****"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:17:3F:65:CC:BA   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=100/100  Signal level=-28 dBm  Noise level=-103 dBm
          Rx invalid nwid:571  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:6652   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"S3cur3 4s ****"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:17:3F:65:CC:BA   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=100/100  Signal level=-28 dBm  Noise level=-103 dBm
          Rx invalid nwid:571  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:6652   Missed beacon:0

root@richard-laptop:/home/richard# sudo gedit /etc/network/interfaces

(gedit:9152): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```


*******************Interfaces Doc************************
> auto lo
iface lo inet loopback

auto wifi0
iface wifi0 inet dhcp
wpa-driver wext
wpa-ssid S3cur3 4s ****
wpa-proto WPA
wpa-ap-scan 2
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 54fb5a4e7fe4990e19efa228df78b23d734448e831563aa92d7efd6569dc8adb

auto eth1

I'm using a Cisco wireless card, Is **wext** the right driver?

My network is hidden, and I use a passphrase with TKIP encryption. Any help would be great.

---

### Post by kevdog on 2007-10-27
Broadcast your network -- do not hide the essid.

wpa-ssid S3cur3 4s ****

Do not use an essid that has spaces in its name.

---

### Post by distortedecho on 2007-10-27
I thought you could hide it so long as it was configured as hidden?

Can I fill the spaces with _ ?

---

### Post by kevdog on 2007-10-27
Try broadcasting it -- hidden sometimes doesnt work with linux -- I dont know why but ive seen this cause a problem -- its a linux thing.

You can fill the spaces with - or _, but just dont put any spaces in the essid name, and make sure the essid specified in the interfaces file matches exactly what is typed in the router setup.

---

### Post by distortedecho on 2007-11-10
OK, I've removed the spaces on router and wpasupplicant and I'm broadcasting my essid.

Here's what I get when I restart the network.

```
 * Reconfiguring network interfaces...                                                                                       RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wifi0.pid with pid 4415
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x1 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - There is already a pid file /var/run/dhclient.wifi0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Ignoring unknown interface eth1=eth1.

```

Can anyone explain?

---

### Post by kevdog on 2007-11-10
Can you repost the parameters you are using!!  You said a cisco card, but what driver/chipset are you running??

---

### Post by distortedecho on 2007-11-10
How do I show you this?

---

### Post by kevdog on 2007-11-10
Parameters --

They would either be like this:
auto lo
iface lo inet loopback

auto wifi0
iface wifi0 inet dhcp
wpa-driver wext
wpa-ssid S3cur3 4s ****
wpa-proto WPA
wpa-ap-scan 2
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 54fb5a4e7fe4990e19efa228df78b23d734448e831563aa92d 7efd6569dc8adb

or you would be using a wpa_supplicant.conf file.

The driver can be found with:
lshw -C network

---

### Post by distortedecho on 2007-11-10
It would be the first one - but without spaces in the SSID.

I'll run the Ishw -C network and post the results in the morning.

---

### Post by distortedecho on 2007-11-11
As promised.

```
  *-network               
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 0
       resources: irq:3
  *-network
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:08:02:d6:3c:3b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.2.3 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:0c:30:e9:7a:4c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS

```

---

### Post by kevdog on 2007-11-11
Look at what you just provided me.  (most users do not do this).

Your wireless interface is eth1 and not wifi0 or whatever you were naming it in the /etc/network/interfaces file.  

Are you running a usb wireless dongle or wireless pci card for your wireless card?  The output you gave seems to suggest a wireless dongle, however possibly not.  There is no wireless driver or driver statement associated with eth1 as their is with eth0.  Either confirm for me that you can connect to an unencrypted network (which means that everything is OK with your driver module setup), or confirm that you installed the drivers appropriately.

---

### Post by distortedecho on 2007-11-11
> **kevdog said:**
> Look at what you just provided me.  (most users do not do this).

Your wireless interface is eth1 and not wifi0 or whatever you were naming it in the /etc/network/interfaces file.  

Are you running a usb wireless dongle or wireless pci card for your wireless card?  The output you gave seems to suggest a wireless dongle, however possibly not.  There is no wireless driver or driver statement associated with eth1 as their is with eth0.  Either confirm for me that you can connect to an unencrypted network (which means that everything is OK with your driver module setup), or confirm that you installed the drivers appropriately.

OK - I've changed wifi0 for eth1 as you suggest. I still get the same results though.

I am using a Cisco Wireless Card - which is not a USB, it's PCI card/slot.

How do I install the drivers? In Windows I know that's the easy part, but I don't think there are Linux drivers for the card. Because it's Linux.

I appreciate your help so far - do you know how to get me connected wirelessly?
Thanks

---

### Post by distortedecho on 2007-11-19
Solved.

I changed the Cisco Aironet to a different spec/model - and it worked.
I guess the card I was using was to good for Linux, or there aren't drivers for it in Linux,

---

### Post by distortedecho on 2007-12-20
Hi again

Everytime I boot up my laptop, I have to "Maually configure" my wireless network.
This involves clicking on the network icon in the system tray and selecting manual configuration. Then selecting my profile and then going through the terminal to restart with this command:

/etc/init.d/networking restart

How can I set up ubuntu to start up with my wireless network all ready working?????

Please help.

Thanks

---

