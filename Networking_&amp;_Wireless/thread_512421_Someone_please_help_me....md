---
title: "Someone please help me..."
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by User X on 2007-07-29
I am a super noob and I am need of some wirelesss help.  I have an Asus A8V-E Deluxe motherboard with an onboard Marvel 88w8335 Libertas chip providing wifi.  I am using a Linksys WRT54G wireless router.  I am using WEP encryption currently.  I am using Ndiswrapper, and the windows XP driver for my chip and "ndiswrapper -l" reports:

"mrv8ka51 : driver installed
              device (11AB:1FA7) present"

an iwconfig yeilds:

" wlan0     IEEE 802.11b  ESSID:"Home to the Gods"  Nickname:"Home to the Gods"
                Mode:Managed  Frequency:2.437 Ghz  Access Point: 00:18:39:56:63:F4
                Bit Rate=36 Mb/s  Sensitivity=-200 dBm
                RTS thr=2346 B  Fragment the=2346 B
                Power Management:off
                Link Quality:45/100  Signal level:-67 bBm  Noise level:-96 dBm
                Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
                Tx excessive retries:0  Invalid misc:0  Missed beacon:0"

Network manager saw my wireless networks ssid, and reported being connected however I was not able to access the internet, or ping my router.  I tried Wicd and got "could not obtain IP address".  I tried Wifi Radar and got an IP address once, and only once, and I was still not able to connect to the internet, or ping my router.  The light on the back of the wireless card is on.  Wireless is this computers only connection to the internet.  I have tried all of the afformentioned configurations with and without wep encryption.  I have also tried all configurations using DHCP, and static IP addresses.  My wireless router has all MAC Address filtering disabled.  Some one please help!

Edit: that smiey face is not supposed to be there...  It should read a ":", then "off"

---

### Post by User X on 2007-07-29
I have tried as described here:

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_(ndiswrapper)?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_(ndiswrapper)?highlight=%28WifiDocs%2FDevice%29)

and I get the driver installed, but not "device XXXX present"?

I am using ndiswrapper-1.47

---

### Post by User X on 2007-07-30
Wow... no one has used this chip with any sucess???

---

### Post by ACMarina on 2007-07-30
Have you tried to release and renew your dhcp to get a solid IP address??

My wireless question is now on page 11, asked about this time yesterday..

---

### Post by jw5801 on 2007-07-31
Hey User X! Me again :p
Can you change your ESSID to something without spaces in it? Something in the back of my mind seems to think that Linux has issues with spaces in ESSIDs. I seem to recall reading something about it somewhere... Worth a shot I figure!

---

