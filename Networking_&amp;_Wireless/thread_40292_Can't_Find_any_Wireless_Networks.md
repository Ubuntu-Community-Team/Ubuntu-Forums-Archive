---
title: "Can't Find any Wireless Networks"
date: 2005-06-08
forum: Networking &amp; Wireless
---

### Post by mjsoccer1 on 2005-06-08
Okay, I got a sisco aironet 350 wireless adapter pcmcia card, and it works... Ubuntu recognizes it (in the Kwifi manager) however it cannot find any available networks... I know that the card works, I tried it on one of our Windows laptops, and it recognizes and connects to the network.  I know that I am not out of range, the wireless router is less than four feet away from the laptop.  When I click on "Scan for Networks," I get a an error saying *The scan is complete, but no networks have been found*. I have disabled WEP and MAC filtering... The router does not see the card.  Any ideas??? Please help! Both the status light and activity lights are blinking on the card..... Thanks!

---

### Post by kleeman on 2005-06-08
What do the following commands show:
iwconfig
ifconfig
sudo iwconfig wlan0 scan

(the latter assumes your nic is wlan0 check ifconfig)

Also are you using ndiswrapper or a native driver?

---

### Post by mjsoccer1 on 2005-06-08
Here is the iwconfig

[I]
lo      no wireless extensions

eth0  no wireless extensions

sit0    no wireless extensions

eth1   IEEE 802-11-DS  ESSID "tsunami"
Mode Managed Frequency: 2.44 GHz  Access Point:  FF:FF:FF:FF:FF:FF
Bit Rate: 11 Mb/s   Tx-Power=20dBm    Sensitivity=0/65535
Retry Limit: 16   RTS thr:off    Frament thr:off
Encryption key: off
Power Management: Off
Linke Quality=0/160   Signal level=-111 dBm Noise level = -111 dBm
Tx invalid nwid: 11191  Rx invalid crypt: 0  Rx invalid frag: 0

wifi0    IEEE 802-11-DS  ESSID "tsunami"
Mode Managed Frequency: 2.44 GHz  Access Point:  FF:FF:FF:FF:FF:FF
Bit Rate: 11 Mb/s   Tx-Power=20dBm    Sensitivity=0/65535
Retry Limit: 16   RTS thr:off    Frament thr:off
Encryption key: off
Power Management: Off
Linke Quality=0/160   Signal level=-111 dBm Noise level = -111 dBm
Tx invalid nwid: 11191  Rx invalid crypt: 0  Rx invalid frag: 0

[/I]

sudo iwconfig wifi0 scan returns an error, *unrecognized wireless request*

I am not using ndiswrapper, I simply plugged the card in, and tried connecting... I was told that the Aironet is supported out of box by Linux.
Any ideas? Thank you!

---

### Post by kleeman on 2005-06-08
Wierd it is showing two interfaces (eth1 and wifi0). Assuming you get 
an ip from your router using dhcp try:

sudo dhclient eth1

and report output

Also try

sudo iwlist eth1 scanning

to see what networks are around

---

### Post by mjsoccer1 on 2005-06-08
sudo dhclient returned
[I]
wifi0 unknown hardware address type 801
sit0: unknown hardware address type 776
wifi0 unknown hardware address type 801
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:09:e8:b4:e0:0d
Sending on LPF/eth1/00:09:e8:b4:e0:0d
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 prt 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 prt 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 prt 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 prt 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 prt 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 prt 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping
[/I]
sudo iwlist eth1 scanning returned
[I]
eth1            Scan Completed:
                   Cell 01- Address 00:0C:41:41:34:AE
                    ESSID "Benn"[/I] <one of my neighbors' network[I]
                    Mode Master
                    Frequency: 2.442GHz (channel 7)
                    Quality: 0/160 Signal level= -25 dBm Noise Level=-256 dBm
                    Encryption key: off
                    Bit Rate: 1 Mb/s
                    Bit Rate: 2 Mb/s
                    Bit Rate: 5.5 MB/s
                    Bit Rate 11 Mb/s
                 
               Cell 02- Address: 00:04:E2:7F:8D:15
                    ESSID: "SMC" [/I]**<My network**[I]
                    Mode: Master
                    Frequency: 2.442GHz (channel 7)
                    Quality: 0/160 Signal level= -57 dBm Noise Level=-256 dBm
                    Encryption key: off
                    Bit Rate: 1 Mb/s
                    Bit Rate: 2 Mb/s
                    Bit Rate: 5.5 MB/s
                    Bit Rate 11 Mb/s
[/I]
Any ideas???? Thanks!

---

### Post by kleeman on 2005-06-08
OK eth1 is your interface not wifi0. Your iwconfig seems to show you are listening for a network called tsunami which isn't showing up on iwlist. I wonder where tsunami came from???? Anyway try setting the essid to your network i.e. SMC as follows

sudo iwconfig eth0 essid SMC

check that it worked by doing iwconfig

then retry

sudo dhclient eth1

---

### Post by mjsoccer1 on 2005-06-08
Its working!!! I sstarted a new session in GNOME, and manualy configured the network interface eth1, and it seems to be working in both KDE and GNOME.... I will have to wait and see what happens when I reboot.  I will let you know what happens... thanks for all of your help.

---

### Post by kleeman on 2005-06-09
Excellent! BTW I always start my wireless network manually. As I understand it gui (and general wireless) support should be much better in Breezy. Here's hoping  :smile:  :smile:

---

