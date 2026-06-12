---
title: "I can't get wireless on my HP to function"
date: 2015-11-24
forum: Networking &amp; Wireless
---

### Post by xlink- on 2015-11-24
Hey all,

I'm new to Ubuntu and would love to get some help if possible. I have recently installed Ubuntu on my system next to Windows 10 and I'm having problems getting the wifi to work.
It picks up the signal from my modem; only when I'm close though and it allows me to enter my Password for my modem but refuses to connect.

I have searched and tried a few troubleshooting tips that I've found around the forums but none seem to fix my problem. I've followed the tips at "[Before posting in Network & Wireless]("http://ubuntuforums.org/showthread.php?t=370108")" but with no luck. I have ran and got information from wireless-info and I will also include a link with my machine information.


Hardware and etc. [http://pastebin.com/dTv6e13Z](http://pastebin.com/dTv6e13Z)

---

### Post by Bucky Ball on 2015-11-24
Welcome. Might sound silly, but have you unplugged the ethernet cable and rebooted with just wireless? If the cable is in it may be blocking the wireless (which seems to be working and finding your AP but is 'soft blocked').

(And hi from Adelaide! :))

---

### Post by xlink- on 2015-11-24
I just tried a reset without the cable connected and it managed to connect for a short while, once I got about 5 meters from the modem it drops off. The signal strength seems to be very poor now.

(Hello from Melbourne :D)

---

### Post by Bucky Ball on 2015-11-24
Click on the network icon and select Edit and edit your wireless connection.

Under the 'General' tab you should have the first two ticked: Automatically connect to this ... and All users may connect. The last, about VPN, should be unticked.

Under 'Wifi' make sure you have your AP/network name in there, mode is 'infrastructure' and leave the rest.

Under 'Security' make sure you have the correct details to match your network.

Under 'IPv4' settings make sure that is set to 'Auto' if you are getting an IP from the router. Importantly, make sure 'Require IPv4 addressing' at the bottom is UNticked.

Under 'IPv6', set to 'ignore'. Important. :)

Save/close and reboot. Any better? At least you are getting some connection so that is a start. Check all settings against your router's to make sure you have them matching. :)

(PS: When you move 5m away, are you still in clear line of sight to the router?)

---

### Post by xlink- on 2015-11-25
I done all of that and the issue still remains :(

5m; it's behind a wall, although the wireless card never had any issues connecting this far when Windows was installed. So I don't presume the wall should cause any issues.

---

### Post by Hadaka on 2015-11-25
Hi , please copy and paste..
This sets your country code which is currently not defined.
```
sudo iw reg set AU
sudo sed -i 's/^REG.*=$/&AU/' /etc/default/crda
```
next,please access your router settings are remove the TKIP setting
replace with wpa2 aes, the current TKIP setting may be causing your
cutoffs and weak connection,it does'nt usually affect windows but it does ubuntu.
thanks

---

### Post by xlink- on 2015-11-25
I gave all that a go too and no luck as of yet, I would also like to add that the connection less than a meter away is pretty awful as well

---

### Post by Bucky Ball on 2015-11-25
Have you done a reboot after running Hadaka's instructions?

---

### Post by xlink- on 2015-11-25
I sure have, to no prevail as of yet.

---

