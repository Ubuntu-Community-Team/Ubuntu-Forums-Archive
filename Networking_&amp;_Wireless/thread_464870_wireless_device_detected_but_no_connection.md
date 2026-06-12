---
title: "wireless device detected but no connection"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by Diego De Rosa on 2007-06-05
Hello everyone,

I am trying to use a wireless USB adapter by Roper (RO80211GTI-USB) with NDISwrapper without success (so far). I followed the instructions at: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
Namely, I installed NDISwrapper (svc) and ndisgtk and installed the driver for the adapter (successfully, I guess). When I do

  sudo ndiswrapper -l

I get

  wlanutg : driver installed
        device (0CDE:0017) present

but the "Windows Wireless Driver" says "Hardware present: No"

Then I did

  sudo depmod -a
  sudo modprobe ndiswrapper
  tail /var/log/messages
  
(see "tail" for messages. at the end it says:
  Jun  2 12:30:08 ares-laptop kernel: [  592.816000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
)

At this point, If I do iwconfig I get

wlan0     IEEE 802.11g  ESSID:any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:5B:DA:3A:5A   
          Bit Rate=54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3  
          RTS thr=4096 B   Fragment thr=4096 B   
          Power Management:off
          Link Quality:100/100  Signal level:-19 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

which looks pretty good, but the wireless connection is not working. BTW my router is open (temporarly), that is I set no encription.

Also, I tried 
  sudo ifdown wlan0
  ifdown: interface wlan0 not configured


I also tried (with the ethernet cable unplugged) 
  sudo killall dhclient
  sudo ifconfig eth0 down
but i got 
  dhclient: no process killed

and 
  $ sudo dhclient wlan0
  Internet Systems Consortium DHCP Client V3.0.4
  Copyright 2004-2006 Internet Systems Consortium.
  All rights reserved.
  For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
  
  Listening on LPF/wlan0/00:60:b3:08:21:ee
  Sending on   LPF/wlan0/00:60:b3:08:21:ee
  Sending on   Socket/fallback
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
  No DHCPOFFERS received.
  No working leases in persistent database - sleeping.


I tried the router without encription, and with all combinations of WEP encription (ascii, HEX, 64 and 128 bit). BTW, the Network Manager applet doesn't let me select "No encription", neither WPA. 

As you may have noticed, I am new to Linux. I have Ubuntu 7.04 installed on a Compaq Presario 2500 laptop (Intel Pentium 4).
kernel is 2.6.20-16-generic
the installed ndiswrapper version is 1.43
the output of lsusb command (the chipset?) is
0cde:0017 Z-Com

Thanks in advance for amy help - Diego

# # # # # # # T A I L # # # # # # #

tail /var/log/messages
Jun  2 12:21:17 ares-laptop gconfd (ares-5052): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun  2 12:21:27 ares-laptop gconfd (ares-5052): Resolved address "xml:readwrite:/home/ares/.gconf" to a writable configuration source at position 0
Jun  2 12:27:15 ares-laptop syslogd 1.4.1#20ubuntu4: restart.
Jun  2 12:30:07 ares-laptop kernel: [  591.540000] ndiswrapper version 1.45 loaded (smp=yes)
Jun  2 12:30:07 ares-laptop kernel: [  591.812000] usb 3-4: reset high speed USB device using ehci_hcd and address 2
Jun  2 12:30:08 ares-laptop kernel: [  591.988000] ndiswrapper: driver wlanutg (Roper,06/01/2005,7.2.2.42) loaded
Jun  2 12:30:08 ares-laptop kernel: [  592.500000] wlan0: ethernet device 00:60:b3:08:21:ee using NDIS driver: wlanutg, version: 0x702022a, NDIS version: 0x501, vendor: 'TNETW1450', 0CDE:0017.F.conf
Jun  2 12:30:08 ares-laptop kernel: [  592.500000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Jun  2 12:30:08 ares-laptop kernel: [  592.500000] usbcore: registered new interface driver ndiswrapper
Jun  2 12:30:08 ares-laptop kernel: [  592.816000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

 # # # # # # # # # # # # # #  # # #

---

