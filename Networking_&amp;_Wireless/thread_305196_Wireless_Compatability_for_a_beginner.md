---
title: "Wireless Compatability for a beginner"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by lori.ann on 2006-11-22
I am installing Ubuntu and trying to figure out how to connect to wireless internet. I've browsed through several posts but beyond knowing to type in iwconfig, I have no idea what to do.

At that command, the only thing that doesn't say "no wireless extensions" is eth1 which reads:

IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
Mode:Managed  Access Point: Invalid
RTS thr: off   Fragment thr:off
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0  Missed beacon:0

Can someone help me understand this?

Thanks! I'm trying to fully switch to ubuntu and right now this is the only thing holding me back.

Lori Ann

---

### Post by livestockPimp on 2006-11-22
well first you have to configure your essid, are you using wpa or wep or no security on your wireless?

for a basic setup:

iwconfig eth1 essid *insert your essid*
iwconfig eth1 key *Enter your wep key*
iwconfig eth1 mode managed

try that, it generally works for a basic wep based wifi connection to your router.

---

### Post by lori.ann on 2006-11-22
Thanks! How can I find that out? I usually am using public wireless which has a passcode, but right now I'm at my parent's house and I'm on my dad's computer but they also have a wireless router I'm hoping to connect to.

---

### Post by livestockPimp on 2006-11-22
well as far as the public one goes, you will need to find out if its wep or wpa, if its wep the commands i sent you should do just fine.
as far as your local router at your dads, if that is wep then it will aslo work, you can use 
iwlist eth1 scan
to find out what avaliable networks are around you. if it has a wpa then you need to use a ndiswrapper, i have never set that up so i cant help you with that... let me know if you have any problems and i will try and help...

---

### Post by lori.ann on 2006-11-25
I looked on my mom's laptop here at home and she's connected to Bevworld with no security. Here are the results of the commands:

loriann@Sami:~$ iwlist eth1 scan
eth1   No scan results
loriann@Sami:~$ iwconfig eth1 Bevworld
Error :unrecognised wireless request "Bevworld"
loriann@Sami:~$ iwconfig eth1 modemanaged
Error for wireless request "Set Mode" (8B06) :
  SET failed on device eth1 : Operation not permitted.

Any ideas?

---

### Post by spd106 on 2006-11-25
Sorry to be the bearer of bad news, but at the moment your wireless card won't work.

You're going to have to install either ndiswrapper or the bcm43xx driver. I would recommend ndiswrapper at the moment. I won't go into the details here since there is a wealth of posts about this already.

Follow this guide first [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper), then come back here with any problems.

Once that's done I also recommend that you install network-manager to manage the wireless connection, though this means you will have to set-up encryption on your home network (not such a bad thing!).

---

