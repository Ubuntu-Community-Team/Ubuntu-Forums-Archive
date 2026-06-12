---
title: "Gutsy, Hardy on Aspire 1640: No DHCPOFFERS"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by Nicolas Raoul on 2008-02-05
Hello all,

WLAN refuses to work on my Acer Aspire 1640 laptop.
More exactly, it finds zero WLAN networks.

When I run "dhclient eth0", I receive "No DHCPOFFERS received" after a minute, even after configuring an ESSID and protocol that should work.

When run kismet, it runs fine but zero WLAN networks are shown, I tried in many places where I know for sure some should be available.

"iwconfig eth0" shows me a scary output (but I am not familiar with this tool so I don't know):
radio off   ESSID:""
Mode:managed  Channel:0  Access Point: Not-Associated
Bit rate:0 kb/s  Tx-Power=off Sensibility=8/0
Retry limit: 7  RTS thr:off   Fragment thr:off
Encryption key:off
... everything 0

"lspci" shows that my WLAN harware is:
Intel Corporation PRO/Wireless 2200BG Network Connection (rev05)
"lshw" shows that module ipw2200 is taking care of it on eth0.

I always use network-admin.
I am using Ubuntu Gutsy. I have the same problem with Hardy alpha4.
It used to work fine in ealier versions, I remember using WLAN with Dapper.

Any idea ? Thanks !
Nicolas Raoul.

---

### Post by chili555 on 2008-02-05
Perhaps this will help: [http://ubuntuforums.org/archive/index.php/t-557121.html](http://ubuntuforums.org/archive/index.php/t-557121.html)

---

### Post by Nicolas Raoul on 2008-02-06
Thanks so much man !
Can't believe I was stuck while the solution was to press a button !

So here is what I did:
- Press on both large buttons that are on the front side of the Aspire 1640, just under the touchpad.
- Start the network manager, and all of the Wifi network are there, finally ! :-)

A confusing thing is that the button produces no light, can't see whether it is on or off (have to use "iwconfig eth0" to see this).

Thanks again,
Nicolas.

---

