---
title: "Wireless capture with Wireshark using  Intel 4965 on 7.10"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by itomkins on 2007-10-23
I have a Dell D630 with the Intel 4965 wireless adapter.  Wireless works fine out of the box, however I am having some issues using Wireshark to do Wireless captures.

I can put the card into monitor mode as follows:

ifconfig wlan0 down
iwconfig wlan0 mode monitor

Then run Wireshark as root and capture against wlan0 OK, however I am seeing loads of malformed 802.11 packets, which I do not see using another laptop with the old 2200BG chipset.

I have attached an example capture.

I have looked around the forums here and on Wireshark plus Google it but not been able to find any pointers so any help would be much appreciated.

---

### Post by metalring on 2007-10-24
4965agn in monitor mode? Is these possible?

---

### Post by itomkins on 2007-10-25
Well there are no errors when putting the device into monitor mode, and running iwconfig afterwards clearly shows the device is in monitor mode, so I guess the answer is yes, however it isn't useable for me because of the issue I mentioned above.

---

### Post by indomiti on 2008-01-08
I have a "Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)" in my laptop, HP Compaq 8510w running Ubuntu 7.10

After putting my card into monitor mode like above my system freezes / hangs after 5-10 secs and i have to shut it down with the power button to restart it.

---

