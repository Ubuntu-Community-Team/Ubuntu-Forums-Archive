---
title: "rt73 request for frodob"
date: 2007-01-02
forum: Networking &amp; Wireless
---

### Post by peterthewolf on 2007-01-02
I followed your how to for the belkin rt73 chip. I have a d-link dwl-g122 c1 which has the same chip. Having tried other how to and serialmonkeys rt73 module with no success on edgy I tried your method.
All went as per instructions but with no useable connection

This is my /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

# rt73 wireless network device using DHCP
iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid *********
# wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX       # This line for hexidecimal keys
wireless-key s:*********                 # This line for ASCII (string) keys
auto rausb0


And this is iwconfig output

peter@mediacentre:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

rausb0    RT73 WLAN  ESSID:""  
          Mode:Auto  Frequency=1 MHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


I would be grateful if you could advise

---

### Post by TheCaptain2000 on 2007-02-03
follow the instructions you find on  [http://wiki.ubuntu-it.org/RalinkRT73](http://wiki.ubuntu-it.org/RalinkRT73)
don't you mind it is in Italian, just follow the commands. your usb key will be recogniser as usbra0 if I am not mistaken
Ren:guitar: 

I have it working with wpa

---

### Post by peterthewolf on 2007-02-10
Thank you captain that worked straight away so ending many months of attempts and numerous forum posts.
I am doing this via the dwl-g122 c1.
One small fly in the ointment to boot the pc I have to unplug the dwl otherwise the boot freezes. Boot without dwl all OK then plug dwl in and all OK. Other usb bits do not stop booting.
Any ideas

---

### Post by peterthewolf on 2007-02-10
Forget the boot problem have found problem

---

