---
title: "Installing sis163u Chipset using ndiswrapper on Feisty"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by octaedro7 on 2007-05-16
Hi there.
This is another newbie with the same old problem: Getting it's wireless USB dongle to work on (K)Ubuntu feisty.  So far I've read a lot of pages and posts and achieved a lot of progress but not the main goal that is to connect to the internet (through a router).
This chipset comes in many brands such as Advantek, Encore, Thompson, and many more.
I've downloaded and installed ndiswrapper and it's GUI.
I have Win XP drivers for my device.

This is where I'm now (very close I think):

$ ndiswrapper -l
```

sis163u : driver installed
        device (0457:0163) present

```

$ iwlist wlan0 scan
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11FH  ESSID:"WLAN_EC"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:13:49:9E:E8:6C
          Bit Rate=54 Mb/s   Tx-Power:17 dBm   Sensitivity=0/3
          RTS thr=2312 B   Fragment thr=2312 B
          Power Management:off
          Link Quality:57/100  Signal level:-59 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

$ iwlist wlan0 scan
```

wlan0     Scan completed :
          Cell 01 - Address: 00:13:49:9E:E8:6C
                    ESSID:"WLAN_EC"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 22 Mb/s
                              18 Mb/s; 12 Mb/s; 11 Mb/s; 9 Mb/s; 6 Mb/s
                              5.5 Mb/s; 2 Mb/s; 1 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:01:38:70:B4:BD
                    ESSID:"WLAN_A8"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s; 6 Mb/s; 5.5 Mb/s
                              2 Mb/s; 1 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

My /etc/networks/interfaces file:
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid WLAN_EC
wireless-key s:XXXXXXXXXXXXX
wireless-channel 9
wireless-mode managed

```

My /etc/modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper
```


Have everything as I'm supossed to but even though my device  appears enabled on the control module and properly configured it does not connect.
[IMG]http://img509.imageshack.us/img509/3157/screenshotconfigurekdeclv6.png[/IMG]

Only once two wireless signals appeared on KNetwork manager (on tray) but when trying to connect to the router it hung on 28%.

Well that's it.  If anyone knows what I' m missing or needs further info just ask.

Big thanks in advance.

---

### Post by octaedro7 on 2007-05-17
Managed to get it work.
Don't know the explanation but did what I read somewhere.
Boot up without the USB dongle plugged in.
After login, plug the wireless adapter and voila!
From that point you don't need to unplug your dongle anymore!

Ugly solution but after all the reading and essay-error I don't give a damn:)

Hope it's useful to SB

---

### Post by DARKGuy on 2007-11-05
Hey, could you please share where did you got those drivers? I have the same card at work (an Encore one) and ndiswrapper says "invalid driver!" using Gutsy :(

---

### Post by welshlion on 2007-11-05
When installing the USB dongle using ndiswrapper you need 2 files sis163u.inf and SIS163u.sys which you will find makes up the windows installer for TP-LINK's TL-WN320G and can be downloaded from their site [http://www.tp-link.com/support/download.asp?a=1&m=TL%2DWN320G](http://www.tp-link.com/support/download.asp?a=1&m=TL%2DWN320G)
The guide below will advise you on how to extract the files and also tell you how to do the install.
[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide)

---

### Post by DARKGuy on 2007-11-07
> **welshlion said:**
> When installing the USB dongle using ndiswrapper you need 2 files sis163u.inf and SIS163u.sys which you will find makes up the windows installer for TP-LINK's TL-WN320G and can be downloaded from their site [http://www.tp-link.com/support/download.asp?a=1&m=TL%2DWN320G](http://www.tp-link.com/support/download.asp?a=1&m=TL%2DWN320G)
The guide below will advise you on how to extract the files and also tell you how to do the install.
[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide)

Hey, thanks!

I've tried those drivers, it doesn't say Invalid Driver now, but when I try "modprobe ndiswrapper" it doesn't work, dmesg says the driver is 32-bit and not 64-bit :(

Do you know where can I find a working 64-bit one?

---

