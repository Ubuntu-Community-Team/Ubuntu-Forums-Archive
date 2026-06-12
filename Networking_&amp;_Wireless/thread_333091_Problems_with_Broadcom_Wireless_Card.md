---
title: "Problems with Broadcom Wireless Card"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by Baethan on 2007-01-06
I have a Broadcom 4318 desktop card (Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller). I didn't know what I had when I first installed Ubuntu (6.10), so there's been a lot of guessing up 'till now. I eventually figured it out and followed one of the excellent guides on making this thing work([http://ubuntuforums.org/showpost.php?p=1189681&postcount=105](http://ubuntuforums.org/showpost.php?p=1189681&postcount=105)). I also installed WiFi Radar, which shows all the nearby networks although it cannot connect. I think I'm close, but I still can't connect to the internet.
 
iwconfig says:
lo: no wireless extensions.
 
eth0: no wireless extensions.
 
eth1:IEEE 802.11g ESSID: off/any Nickname:Wireless@Home
Mode:Managed Frequency: 2.462 GHz Access Point:Not-Associated
Bit Rate=54 Mb/s Tx-Power:25 dBm
RTS thr=2347 B Fragment thr=2346 B
Encryption key:[key here, too lazy to type it out] Security mode:restricted
Power Management: off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
 
sit0: no wireless extensions.
 
I don't know where to go from here. I really need internet access on the computer in question, and it's a wireless-or-nothing sort of setup. Any help is greatly appreciated.
 
Just to head off any advice I've already taken, ndiswrapper is installed, the appropriate drivers have been blacklisted, and "ifdown eth1", "ifup eth1", and "dhclient" have all been entered successfully into the terminal.

---

### Post by aminoz on 2007-01-06
Where it says in your iwconfig listing for eth1, "Access Point:Not-Associated" means - I think - that  your wireless router is not giving you a connection for some reason.  Otherwise you should see a hex address here.

If you're using WPA-PSK encryption, then you also need to have something called "wpa_supplicant" installed and running.  It looks after the keys. 

There are also other things that could be going wrong than my suggestion, of course, I'm just putting this one forward because I was in the same situation as you, and that was my particular problem ---  and it took me absolutely ages before I found out about it despite reading all the howtos and threads etc;  afterwards I realised they were telling me this all the time.

(if you've already got wpa-supplicant, sorry for wasting your time)

---

### Post by Baethan on 2007-01-06
> **aminoz said:**
> Where it says in your iwconfig listing for eth1, "Access Point:Not-Associated" means - I think - that your wireless router is not giving you a connection for some reason. Otherwise you should see a hex address here.
 
If you're using WPA-PSK encryption, then you also need to have something called "wpa_supplicant" installed and running. It looks after the keys. 
 
There are also other things that could be going wrong than my suggestion, of course, I'm just putting this one forward because I was in the same situation as you, and that was my particular problem --- and it took me absolutely ages before I found out about it despite reading all the howtos and threads etc; afterwards I realised they were telling me this all the time.
 
(if you've already got wpa-supplicant, sorry for wasting your time)
 
Thank you for the reply! It's good to know other people have had this problem and survived. :D 
I looked into it, and I'm fairly certain the network has WEP rather than WPA. (I considered installing wpa-supplicant anyways, just in case, but I couldn't figure out how, so I gave up on that.)
Would wpa-supplicant do anything, even if I am most likely dealing with wep?

---

### Post by haiku99 on 2007-01-07
If you are using WEP sometimes it is simpler to just edit your /etc/network/interfaces file, you can input the ESSID and key manually, reboot, and hopefully wifi will work.  If not, another thing to try is entering (in a terminal) **sudo ifdown eth1** followed by **sudo ifup eth1**, that might do it too...
FWIW my file looks like this..

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto wlan0
iface wlan0 inet dhcp
wireless-essid abcdef
wireless-key 0123456789

---

### Post by Baethan on 2007-01-07
I've done the ifdown and ifup... I checked the file, and everything looks good. I'll post it in case there's another problem with it:
 
auto lo
iface lo inet loopback
 
iface eth0 inet dhcp
 
iface eth1 inet dhcp
wireless-essid Wireless@Home
wireless-key keyhere
 
auto eth2
iface eth2 inet dhcp
 
auto ath0
iface ath0 inet dhcp
 
auto wlan0
iface wlan0 inet dhcp
 
 
 
 
auto eth1
auto eth0

---

### Post by mbazs on 2008-01-08
Try this:

iface wlan0
auto wlan0

I've just done this and it worked

---

### Post by mbazs on 2008-01-08
Oh I missed the year 2007, sorry :D

---

