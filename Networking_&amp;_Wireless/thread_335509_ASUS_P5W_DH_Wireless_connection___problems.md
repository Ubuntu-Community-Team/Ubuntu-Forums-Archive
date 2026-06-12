---
title: "ASUS P5W DH Wireless connection   problems"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by devoncatt on 2007-01-10
Hi I have tried several ways but my wireless sees the wireless Linksys router but will not connect. I have tried network , I have tried wifi radar network manager, with nothing installed . Using the suggested drivers, etc. I cannot get this to work. The system thinks this is a USB type of wireless device not a PCI. The only thing I haven't done yet is NDIS Driver ( something I had no luck with on a previous motherboard and a Belkin card)
I have tried with open router, WEP and WPA still nothing connects except once under a ubuntu variant I got the ARP address of the router.

DHCP times out when it tries to connect. I have similar problems is I hard code an IP address as well. Wired connection is fine

Any help would be appreciated it is very very frustrating!

Dcatt
Edgy EFt
chelle@tazx2:~$ dmesg | grep rtl
[17179595.188000] rtl_ieee80211_crypt: registered algorithm 'NULL'
[17179595.188000] rtl_ieee80211_crypt: registered algorithm 'TKIP'
[17179595.188000] rtl_ieee80211_crypt: registered algorithm 'WEP'
[17179595.188000] rtl_ieee80211_crypt: registered algorithm 'CCMP'
[17179595.460000] rtl8187: Initializing module
[17179595.460000] rtl8187: Wireless extensions version 20
[17179595.460000] rtl8187: Initializing proc filesystem
[17179595.460000] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[17179595.572000] rtl8187: Card MAC address is 00:15:af:07:9c:11
[17179595.748000] rtl8187: Card reports RF frontend Realtek 8225
[17179595.748000] rtl8187: WW:This driver has EXPERIMENTAL support for this chipset.
[17179595.748000] rtl8187: WW:use it with care and at your own risk and
[17179595.748000] rtl8187: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO [email]andreamrl@tiscali.it[/email]
[17179595.792000] rtl8187: This seems a new V2 radio
[17179595.792000] rtl8187: PAPE from CONFIG2: 0
[17179595.792000] rtl8187: Driver probe completed
[17179595.792000] usbcore: registered new driver rtl8187
[17179595.896000] rtl8187: Setting SW wep key
[17179596.576000] rtl8187: Card successfully reset
chelle@tazx2:~$ sudo iwlist wlan0 scanning

wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:12:1F:E1
                    ESSID:"dcatt"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:7
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:15  Signal level:0  Noise level:113
                    Extra: Last beacon: 12ms ago

chelle@tazx2:~$ lsusb
Bus 007 Device 005: ID 046d:0a04 Logitech, Inc.
Bus 007 Device 006: ID 0bda:8187 Realtek Semiconductor Corp.
Bus 007 Device 004: ID 05e3:0606 Genesys Logic, Inc.
Bus 007 Device 001: ID 0000:0000
Bus 008 Device 002: ID 2040:9950 Hauppauge
Bus 008 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 003: ID 046d:c30a Logitech, Inc.
Bus 002 Device 004: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000

lle@tazx2:~$ lspci
00:00.0 Host bridge: Intel Corporation 975X Express Memory Controller Hub (rev c0)
00:01.0 PCI bridge: Intel Corporation 975X Express PCI Express Root Port (rev c0)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:00.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:00.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
05:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71c6
05:00.1 Display controller: ATI Technologies Inc Unknown device 71e6
chelle@tazx2:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g link..  ESSID:"dcatt"
          Mode:Managed  Channel=7  Access Point: Not-Associated
          Bit Rate=11 Mb/s
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by devoncatt on 2007-01-10
modprobe results

$ modprobe -c |grep 8187
alias pcmcia:m*c*f*fn*pfn01paF7CB0B07pb66881874pc*pd* serial_cs
alias usb:v0BDAp8187d*dc*dsc*dp*ic*isc*ip* r8187
alias usb:v0846p6100d*dc*dsc*dp*ic*isc*ip* r8187
alias usb:v0846p6A00d*dc*dsc*dp*ic*isc*ip* r8187
alias pcmcia:m*c*f*fn*pfn00paF7CB0B07pb66881874pc*pd* pcnet_cs
chelle@tazx2:~$ modprobe -c |grep rtl
alias usb:v0BDAp8150d*dc*dsc*dp*ic*isc*ip* rtl8150
alias usb:v0411p0012d*dc*dsc*dp*ic*isc*ip* rtl8150
alias usb:v3980p0003d*dc*dsc*dp*ic*isc*ip* rtl8150
alias usb:v07B8p401Ad*dc*dsc*dp*ic*isc*ip* rtl8150
alias symbol:rtl_ieee80211_wx_get_encode ieee80211_rtl
alias symbol:rtl_ieee80211_wx_set_encode ieee80211_rtl
alias symbol:rtl_ieee80211_wx_get_name ieee80211_rtl
alias symbol:rtl_ieee80211_wx_get_rate ieee80211_rtl
alias symbol:rtl_ieee80211_wx_set_rate ieee80211_rtl
alias symbol:rtl_ieee80211_register_crypto_ops ieee80211_rtl
alias symbol:rtl_ieee80211_softmac_start_protocol ieee80211_rtl
alias symbol:rtl_ieee80211_wx_get_power ieee80211_rtl
alias symbol:rtl_ieee80211_wx_set_power ieee80211_rtl
alias symbol:rtl_ieee80211_wx_set_freq ieee80211_rtl
alias symbol:rtl_ieee80211_wx_get_freq ieee80211_rtl
alias symbol:rtl_ieee80211_wx_set_essid ieee80211_rtl
alias symbol:rtl_ieee80211_wx_get_essid ieee80211_rtl
alias symbol:rtl_ieee80211_wx_set_rawtx ieee80211_rtl
alias symbol:rtl_free_ieee80211 ieee80211_rtl
alias symbol:rtl_ieee80211_wx_get_wap ieee80211_rtl
alias symbol:rtl_ieee80211_wx_set_wap ieee80211_rtl
alias symbol:rtl_ieee80211_wx_get_mode ieee80211_rtl
alias symbol:rtl_ieee80211_wx_set_mode ieee80211_rtl
alias symbol:rtl_ieee80211_ps_tx_ack ieee80211_rtl
alias symbol:rtl_ieee80211_is_shortslot ieee80211_rtl
alias symbol:rtl_ieee80211_rx ieee80211_rtl
alias symbol:rtl_ieee80211_crypt_deinit_entries ieee80211_rtl
alias symbol:rtl_ieee80211_txb_free ieee80211_rtl
alias symbol:rtl_ieee80211_get_beacon ieee80211_rtl
alias symbol:rtl_ieee80211_crypt_deinit_handler ieee80211_rtl
alias symbol:rtl_ieee80211_reset_queue ieee80211_rtl
alias symbol:rtl_ieee80211_unregister_crypto_ops ieee80211_rtl
alias symbol:rtl_alloc_ieee80211 ieee80211_rtl
alias symbol:rtl_ieee80211_is_54g ieee80211_rtl
alias symbol:rtl_ieee80211_wlan_frequencies ieee80211_rtl
alias symbol:rtl_ieee80211_crypt_delayed_deinit ieee80211_rtl
alias symbol:rtl_ieee80211_stop_queue ieee80211_rtl
alias symbol:rtl_ieee80211_softmac_stop_protocol ieee80211_rtl
alias symbol:rtl_ieee80211_rx_mgt ieee80211_rtl
alias symbol:rtl_ieee80211_wx_set_scan ieee80211_rtl
alias symbol:rtl_ieee80211_wx_get_scan ieee80211_rtl
alias symbol:rtl_ieee80211_wpa_supplicant_ioctl ieee80211_rtl
alias symbol:rtl_ieee80211_wake_queue ieee80211_rtl
alias symbol:rtl_ieee80211_get_crypto_ops ieee80211_rtl

---

### Post by chili555 on 2007-01-10
What is the output when you do:

sudo dhclient wlan0

???

---

### Post by devoncatt on 2007-01-10
The results are:



Listening on LPF/wlan0/00:15:af:07:9c:11
Sending on   LPF/wlan0/00:15:af:07:9c:11
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by chili555 on 2007-01-10
I noticed your scanning result shows the key is on in your router:

> Cell 01 - Address: 00:13:10:12:1F:E1
ESSID:"dcatt"
Protocol:IEEE 802.11bg
Mode:Master
Channel:7
Encryption key on

Let us see sudo iwconfig wlan0 and let's see if the key is on and matches what you see on the router side. 

Also, is the router set for wireless security mode Auto or Shared Key? If Shared Key, you'll need to do sudo iwconfig key restricted. Then try sudo dhclient wlan0. 

We have our fingers crossed for you.

By the way, any snags installing Ubuntu on this mobo? I am considering the same item.

---

### Post by devoncatt on 2007-01-11
Results were it was set to shared key. I set the router to open, same results, 
I set the router to auto same results. 
I hard entered the key same results

Using Network Manager, wifi radar is installed. 
No configuration in /etc/network/interfaces except loopback.. 
Kwifimanager can't seem to see the networks and the strength seems low (0) 
What should I have as far as networking to make wifi work and what is too much.?

Yes I like the motherboard I have had really no problems with it and the core-duo. I purchased it from Mwave.com and they tested the combination of processor/motherboard and memory as a set before getting it. I have the latest stable BIOS  ( 1707)





sudo iwconfig wlan0 key restrcited
sudo iwconfig wlan0 key xxxxxxxxxxxxxxx
sudo iwconfig wlan0
wlan0     802.11b/g  ESSID:"DCATT"
          Mode:Auto  Channel=5  Access Point: Not-Associated
          Bit Rate=11 Mb/s   Sensitivity=4/6
          Retry:on   Fragment thr:off
          Encryption key:F5B9-A624-0D   Security mode:restricted
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


iwpriv
lo        no private ioctls.

eth0      no private ioctls.

eth1      no private ioctls.

wlan0     Available private ioctls :
          badcrc           (8BE0) : set   1 int   & get   0
          activescan       (8BE1) : set   1 int   & get   0
          rawtx            (8BE2) : set   1 int   & get   0

sit0      no private ioctls.





sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6145
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.


sudo iwconfig wlan0 key restrcited

sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6145
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:15:af:07:9c:11
Sending on   LPF/wlan0/00:15:af:07:9c:11
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by chili555 on 2007-01-11
> No configuration in /etc/network/interfaces except loopback.. 

This is freaky!

Let's try to add it manually and see what we get. Gedit /etc/network/interfaces to add:

auto wlan0
iface wlan0 inet dhcp
wireless-essid yourshere
wireless-key xxxxxxxxxxxxxxx restricted

Save and quit gedit.

Make sure your router is set to Shared Key if you use "restricted." 

Then do sudo /etc/init.d/networking restart and let's see what happens.

Thanks for the mobo info; I'm reaching for my Visa card now!

---

### Post by naht on 2007-01-14
Hi!

I had exactly the same problem. Forget about the r8187 driver, it simply doesn't work. I got mine working with a newer version (1.33) of ndiswrapper (i think you have to compile it myself, but I am not fully sure).
The funniest thing is, the most recent realtek drivers for win98 did'nt work for me. After a few days(weeks) i tried older drivers from the cd that were shipped with the board, and they work like a charm with ndiswrapper. No problems at all. I think this solution can also be applied to the P5B board, it has afaik the same chipset.
I wish you luck. :)

geetings, naht

---

