---
title: "cryptic message form iwconfig"
date: 2005-07-20
forum: Networking &amp; Wireless
---

### Post by bcashman on 2005-07-20
I have been trying to get my DLink dwl-g630 card to work without any luck. I managed to get the laptop to at least see the device, and ndiswrapper- l gives be driver present, device present. The problem seems to be related to this cryptic message i get when i type iwconfig;


lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Sensitivity=-200 dBm
          RTS thr:2346 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I have no clue as to what it means as fare as extension, but the iwlist wlan0 scan gives me the same message then tells me no scan results so I cant find the wireless networks. Anyone have any ideas for a noobie?

---

### Post by PhilippWollermann on 2005-07-21
Mmh.. the error message shouldn't be a problem. Usually it works very well, even if your WLAN tools don't match the kernel WLAN interface. Could you please do a "lspci -n" and post the output, so we can find out, what chipset your card really is. :) D-Link seems to switch chipsets without changing the model number. If it is an TNET1130 or ACX1xx with Vendor ID = 104c and Model = 9066 you could also try using the open-source driver at [http://acx100.sourceforge.net/](http://acx100.sourceforge.net/).

Philipp

---

### Post by bcashman on 2005-07-21
lspci -n
0000:00:00.0 0600: 1002:cab3 (rev 05)
0000:00:01.0 0604: 1002:7010
0000:00:13.0 0c03: 1002:4347 (rev 01)
0000:00:13.1 0c03: 1002:4348 (rev 01)
0000:00:13.2 0c03: 1002:4345 (rev 01)
0000:00:14.0 0c05: 1002:4353 (rev 18)
0000:00:14.1 0101: 1002:4349
0000:00:14.3 0601: 1002:434c
0000:00:14.4 0604: 1002:4342
0000:00:14.5 0401: 1002:4341
0000:00:14.6 0703: 1002:434d (rev 01)
0000:01:05.0 0300: 1002:4437
0000:02:06.0 0607: 104c:ac50 (rev 02)
0000:02:07.0 0200: 10ec:8139 (rev 10)

---

### Post by PhilippWollermann on 2005-07-22
Hi,

mmh.. was your card plugged in, when you did the "lspci -n"? I can't find it in the list, although I see the PC-Card bridge. :-/

Philipp

---

### Post by bcashman on 2005-07-22
Card was plugged in, one of the 2 lights was on. Also, just as a side note when I tried to scan for wireless networks with iwlist the same error message came up about version 17 and 18.

---

