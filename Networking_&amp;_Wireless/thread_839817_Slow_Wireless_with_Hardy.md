---
title: "Slow Wireless with Hardy"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by iperich on 2008-06-24
Hi, I have this problem with a Broadcom wireless card:

$ lspci | grep LAN
02:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Is very slow with Hardy, with Gutsy i've never had a problem...

Look at this:

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"nerds"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:15:E9:01:B5:48   
          **[COLOR="Red"]Bit Rate=1 Mb/s[/COLOR]**   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=75/100  Signal level=-56 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

The Bit Rate never change in this laptop, even with Signal level=-5dBm, with the laptop side by side with de wifi router. I have another 3 machines in the wireless network and there is no problem with them, one with Ubuntu Hardy on a IBM Thinkpad, a Mac and a Xubuntu in a EeePC, the Bit Rate is between 11 and 54Mb/s in those...

Some workaround for this?

Thanks in advice

---

### Post by iperich on 2008-06-24
I' ve tried doing 

#sudo iwconfig wlan0 rate auto

or 

#sudo iwconfig wlan0 rate 11M

etc...

but it doesn't change the bit rate, i did 

#sudo ifdown wlan0
ifdown: interface wlan0 not configured

Hmmm... so I checked my /etc/network/interfaces file:

auto lo
iface lo inet loopback

and that's it...

In the EeePC the file is exactly the same, but it shows bitrate=54M

There is another way to configure the bit rate???

---

### Post by undertakingyou on 2008-06-24
I was having issues in gutsy with the broadcom stuff.  I went to using NDisWrapper and the windows drivers and it cleared it up.  Have you tried that?

---

