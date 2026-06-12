---
title: "wlan0 can't acquire ip address"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by cloudedice on 2007-10-22
I'm not really sure what is wrong because after the upgrade I was able to connect to the network just fine.  I was having issues with my nvidia driver not working properly, so after using envy to get it set up and rebooting, graphics worked fine, but wireless stopped working.

wpa_supplicant will associate the wlan0 device to the correct AP, but dhclient doesn't get a DHCPOFFER from the router. 

lshw -C network
```
  *-network:0
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 13
       serial: 00:XX:XX:XX:XX:XX
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.9 firmware=N/A latency=64 link=no maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair
  *-network:1
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: wmaster0
       version: 01
       serial: 00:xx:xx:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=prism54pci latency=64 maxlatency=28 mingnt=10 module=prism54pci multicast=yes wireless=IEEE 802.11g

```

iwlist
```
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:XX:XX:XX:XX
                    ESSID:"XXXXXXXXX"
                    Mode:Master
                    Frequency:2.412 GHz
                    Signal level=69/100  
                    Encryption key:on
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020000
                    Extra:tsf=00000001215051e3
          Cell 02 - Address: 00:1B:XX:XX:XX:XX
                    ESSID:"Wireless"
                    Mode:Master
                    Frequency:2.462 GHz
                    Signal level=49/100  
                    Encryption key:on
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020000
                    Extra:tsf=0000000893f89718
```

iwconfig; /etc/init.d/networking start; iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"XXXXXXXXXX"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


 * Configuring network interfaces...                                                                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:XX:XX:XX:XX:XX
Sending on   LPF/wlan0/00:XX:XX:XX:XX:XX
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                                                                       [ OK ]

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"XXXXXXXXXX"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0F:XX:XX:XX:XX   
          RTS thr:off   Fragment thr=2346 B   
          Link Signal level=35/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I would appreciate any and all help.

-ice

---

### Post by cloudedice on 2007-10-23
Strange things are happening...

When DHCP had initially failed, I tried to use a static IP address, which also failed.  I just tried again, but now static IP is working...

I'm confused, but I guess I'll try dhcp again tomorrow night.

-ice

---

