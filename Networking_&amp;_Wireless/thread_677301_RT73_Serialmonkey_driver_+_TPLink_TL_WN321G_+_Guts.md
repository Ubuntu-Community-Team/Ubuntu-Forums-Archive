---
title: "RT73 Serialmonkey driver + TPLink TL WN321G + Gutsy = Insanity"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by RostokMcSpoons on 2008-01-24
Arggggggggggggghhhhhhhhhhhhhhhhhhhhhhhhhhhh!

Please can someone help this here Linux noob get through the (supposedly) simple, everyday task of getting a PC, albeit Linux, connected to the Net over WiFi.

Cos this is driving me absolutely nuts :(


The crazy things is I've now had it working twice.  But inspite of following the instructions in the HOWTO: RT73 thread, the settings don't seem to 'stick' through a reboot.  And when it comes back, I have to jump through hoops for the connection to work again.  Where hoops equals removing, rebuilding and reinstalling the drivers, then cycling the connection up and down a gazillion times.
I've got no idea why it's worked when it has.  

I only know the problem is that 'sudo dchlient wlan0' only rarely (ie. twice) has worked.  

I can't get the damn connection to work at all now, so I'm typing this on my windows pc, but my linux pc is next to me.  My Speedtouch 585v6 router ("SpeedTouchB7EBFF" you'll see later) is working fine wirelessly with my Wii, which is downstairs.

Here's the last mess of stuff I've typed which I thought might kick the net connection back to life:

```

ross@Ross-LinuxPC:/usr/src/rt73-cvs-2008010512$ sudo ifconfig wlan0 down

ross@Ross-LinuxPC:/usr/src/rt73-cvs-2008010512$ 
ross@Ross-LinuxPC:/usr/src/rt73-cvs-2008010512$ sudo make clean
make: *** No rule to make target `clean'. Stop.
ross@Ross-LinuxPC:/usr/src/rt73-cvs-2008010512$ dir
CHANGELOG  CVS  FAQ  LICENSE  Module  README  THANKS
ross@Ross-LinuxPC:/usr/src/rt73-cvs-2008010512$ cd Module
ross@Ross-LinuxPC:/usr/src/rt73-cvs-2008010512/Module$ 
ross@Ross-LinuxPC:/usr/src/rt73-cvs-2008010512/Module$ sudo make clean
ross@Ross-LinuxPC:/usr/src/rt73-cvs-2008010512/Module$ sudo make debug
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /usr/src/rt73-cvs-2008010512/Module/rtmp_main.o
  CC [M]  /usr/src/rt73-cvs-2008010512/Module/mlme.o
  CC [M]  /usr/src/rt73-cvs-2008010512/Module/connect.o
  CC [M]  /usr/src/rt73-cvs-2008010512/Module/rtusb_bulk.o
  CC [M]  /usr/src/rt73-cvs-2008010512/Module/rtusb_io.o
  CC [M]  /usr/src/rt73-cvs-2008010512/Module/sync.o
  CC [M]  /usr/src/rt73-cvs-2008010512/Module/assoc.o
  CC [M]  /usr/src/rt73-cvs-2008010512/Module/auth.o
  CC [M]  /usr/src/rt73-cvs-2008010512/Module/auth_rsp.o
  CC [M]  /usr/src/rt73-cvs-2008010512/Module/rtusb_data.o
  CC [M]  /usr/src/rt73-cvs-2008010512/Module/rtmp_init.o
  CC [M]  /usr/src/rt73-cvs-2008010512/Module/sanity.o
  CC [M]  /usr/src/rt73-cvs-2008010512/Module/rtmp_wep.o
  CC [M]  /usr/src/rt73-cvs-2008010512/Module/rtmp_info.o
  CC [M]  /usr/src/rt73-cvs-2008010512/Module/rtmp_tkip.o
  CC [M]  /usr/src/rt73-cvs-2008010512/Module/wpa.o
  CC [M]  /usr/src/rt73-cvs-2008010512/Module/md5.o
  CC [M]  /usr/src/rt73-cvs-2008010512/Module/rt2x00debug.o
  LD [M]  /usr/src/rt73-cvs-2008010512/Module/rt73.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/src/rt73-cvs-2008010512/Module/rt73.mod.o
  LD [M]  /usr/src/rt73-cvs-2008010512/Module/rt73.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
!!! WARNING: Module file much too big (>1MB)
!!! Check your kernel settings or use 'strip'
*** Module rt73.ko built successfully
ross@Ross-LinuxPC:/usr/src/rt73-cvs-2008010512/Module$ sudo strip -S rt73.ko
ross@Ross-LinuxPC:/usr/src/rt73-cvs-2008010512/Module$ sudo rmmod rt73
ross@Ross-LinuxPC:/usr/src/rt73-cvs-2008010512/Module$ sudo insmod rt73.ko debug=31
ross@Ross-LinuxPC:/usr/src/rt73-cvs-2008010512/Module$ lsmod | grep usbcore
usbcore               138632  7 rt73,usb_storage,usbhid,libusual,ehci_hcd,ohci_hcd
ross@Ross-LinuxPC:/usr/src/rt73-cvs-2008010512/Module$ sudo ifconfig wlan0 up
ross@Ross-LinuxPC:/usr/src/rt73-cvs-2008010512/Module$ sudo iwconfig wlan0 essid RossLinuxPC
ross@Ross-LinuxPC:/usr/src/rt73-cvs-2008010512/Module$ sudo iwconfig wlan0 key EC3ED595C4
ross@Ross-LinuxPC:/usr/src/rt73-cvs-2008010512/Module$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:11:F5:A5:DB:5A
                    ESSID:"SpeedTouchB7EBFF"
                    Mode:Managed
                    Channel:1
                    Encryption key:on
                    Bit Rates:0 kb/s
          Cell 02 - Address: 00:17:3F:7C:55:CF
                    ESSID:"Belkin_G_Plus_MIMO_ADSL"
                    Mode:Managed
                    Channel:10
                    Encryption key:on
                    Bit Rates:0 kb/s

ross@Ross-LinuxPC:/usr/src/rt73-cvs-2008010512/Module$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 7619
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:19:e0:65:95:f6
Sending on   LPF/wlan0/00:19:e0:65:95:f6
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
Trying recorded lease 192.168.1.70
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.

--- 192.168.1.254 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```

Here's the gubbins I've got in the Networks\interfaces file:

```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid RossLinuxPC
pre-up iwconfig wlan0 key EC3ED595C4

```



On a side note... frankly I'm wondering what anyone sees in Linux, it's so damned obtuse, seemingly for no reason other than to keep Teh N00bs away :?

---

### Post by wieman01 on 2008-01-25
I can offer you my own guide and full support:

[http://ubuntuforums.org/showthread.php?t=563547]("http://ubuntuforums.org/showthread.php?t=563547")

Post there if you need help. I have given up on other drivers, therefore I cannot tell you more.

---

### Post by deltaprime on 2008-01-25
nice page
good drivers used them on other computers =)

DELTA-_-delta

---

### Post by RostokMcSpoons on 2008-01-25
Thanks, I'd forgotten about ndiswrapper tbh, as other people said it wasn't required.  But any port in a storm!  I'll try that tonight :)

---

### Post by jeffus_il on 2008-01-25
Mine just plugged in and worked, just gave it the Access Point, a Wep password and dhcp, one of the easiest installs I've had.

---

### Post by RostokMcSpoons on 2008-01-25
Okey dokey... well it's been 'interesting'
I can now get my wifi to work more consistently.  It's not there yet though.

1) I reinstalled Gutsy, to clear out any mistakes or nastiness I may have introduced with my noobily fat fingers.
2) I reinstalled a very recent copy of the Serialmonkey driver
3) I realised the ESSID in my iwconfig wlan0 has to match that of my router.... well, I think it does, doesn't it?

Now the first time I changed all that, it worked.  So I changed the interfaces file, and hoped it would work after a reboot (the aim of all this is so my daughter can use this pc, so it's got work straight away, no faffing!)

It didn't.  And it got it's knickers in a twist and showed my lots of text about usb devices not working (the wifi).  A subsequent reboot got a clean start, But still no automatically working wifi :(

However, it's interesting to see my wifi works, in spite of having all the other rt modules still in place:

```

ross@RossLinuxPC:/etc/network$ lsmod | grep usbcore
usbcore               138632  9 rt2500usb,rt73usb,rt2x00usb,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd

```

...and Network Manager is still there (even though I purged it... presumably that only applies to the current session?)

Here's my current interfaces file:
```

auto lo
iface lo inet loopback

auto wlan0

iface wlan0 inet dhcp

	pre-up ifconfig wlan0 up

	pre-up iwconfig wlan0 essid "SpeedTouchB7EBFF"

	pre-up iwconfig wlan0 key EC3ED595C4

```

Whaddya reckon?


edit: Hmmm... left the pc for a bit, only to return to find the network connection had died.  Nothing seemed to bring it back so I pulled the usb dongle out and put it back - still no joy so rebooted.
As usual, the net connection failed.  And in spite of my cajolings only re-making the rt73 module seemed to bring it back to life.   I think ndiswrapper is what I'm going to try now.

---

