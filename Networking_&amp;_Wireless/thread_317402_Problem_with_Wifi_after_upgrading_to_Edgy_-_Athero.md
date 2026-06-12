---
title: "Problem with Wifi after upgrading to Edgy - Atheros AR5212"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by galador on 2006-12-12
I recently upgraded my Dapper installation - which was working perfectly - to Edgy, and after the upgrade I had a few problems with the mouse and video, though I got those fixed, and my Wireless card.  It is an Atheros AR5212 card on a Toshiba A75-S1253 laptop.

lspci:  

00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
______
iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:1829  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
_____

Restricted modules are installed for my kernel, and when I have the card active, it says that the network is at ~90% signal strength, but I can't access anything on the Internet.  I've done quite a bit of Googling, looking at the Wiki, and searching here, but so far I can't find anything that fixes my problem.

Any help will be appreciated!

---

### Post by galador on 2006-12-13
Also, I've tried a "clean" install of Edgy, and the networking still doesn't work.

---

### Post by jml on 2006-12-13
This may not be of help to you, but I had quite a bit of trouble getting my Atheros based card working in Edgy as well.  What worked for me was to install network-manager and network-manager-gnome.  I then disabled my wired NIC and configured my wireless card with network-mamager.  Other than a little delay in actually connecting to the wireless access point when I first log in, it seems to work well.

Joe

---

### Post by FrodoB on 2006-12-13
Can you get any output from iwlist:

 sudo iwlist ath0 scanning

---

### Post by galador on 2006-12-13
> **jml said:**
> This may not be of help to you, but I had quite a bit of trouble getting my Atheros based card working in Edgy as well.  What worked for me was to install network-manager and network-manager-gnome.  I then disabled my wired NIC and configured my wireless card with network-mamager.  Other than a little delay in actually connecting to the wireless access point when I first log in, it seems to work well.

Joe

I already have that installed, though I haven't really waited to see if it takes some time to connect, I'll try that.

> **FrodoB said:**
> Can you get any output from iwlist:

 sudo iwlist ath0 scanning

ath0      Scan completed :
          Cell 01 - Address: 00:01:F4:5B:72:82
                    ESSID:"UCAWIRELESS"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/94  Signal level=-83 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:01:F4:5B:73:F4
                    ESSID:"UCAWIRELESS"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=12/94  Signal level=-83 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
 ***     Cell 03 - Address: 00:C0:49:F0:F3:E2
                    ESSID:"Bryan"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/94  Signal level=-36 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101800003a4000027a4000042435e0062322f00
          Cell 04 - Address: 02:13:02:0A:D4:78
                    ESSID:"UCAWIRELESS"
                    Mode:Ad-Hoc
                    Frequency:2.462 GHz (Channel 11)
                    Quality=1/94  Signal level=-94 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100


The third one is the one I'm trying to connect to.

---

### Post by galador on 2006-12-13
I finally got it to work with network-manager.

Thanks for your help!

---

### Post by FrodoB on 2006-12-13
Excellent job!

---

### Post by dorkdork777 on 2007-01-19
OK, I've given each a quick look, but neither seems to supply a good, straightforward answer. And I've tried with Dapper and Edgy, each to no avail.

---

