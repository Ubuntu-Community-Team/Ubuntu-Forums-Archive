---
title: "SMC2635W wireless help!"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by spamzilla on 2006-10-22
Hey

Since I have some free time coming up, I have decided to try to get Ubuntu working on my laptop. The first problem I have is trying to access the internet. I have a SMC2635W (v2 blue card) and a couple of drivers (rt2400 and rt2x00) tar.gz packages on my desktop that will work.

Now, I have enabled the wireless access Ra0 in the networking options (edited in my router essid [SWAMR-54108] and set the configuration settings to DHCP) and this got my cards light to show up. Sadly I cannot connect to the internet :( As an **Ubuntu noob**, can someone point me in the direction to get my internet working.

This would be much appreciated

Thanks :)

---

### Post by spamzilla on 2006-10-22
I figured this may help in fixing this problem. I typed in iwconfig in the terminal:

lo no wirless extensions

sit0 no wirless extensions

eth0 no wirless extensions

rao RT2400PCI ESSID: "SWAMR-54108"
    Mode:Managed  Channel=1 1  Access Point:hex here
    Bite Rate: 11 Mb/s
    RTS thr: off   Fragment thr: off
    Encry key: off
    link qual: 80 sig level: 48 Noise lev: 0
    rX invalid nwid: 0   invalid crypt: 0 invalid misc: 0

---

### Post by spamzilla on 2006-10-23
Anyone got any ideas on how I can get my internet working?

---

### Post by spamzilla on 2006-10-23
Ok I can now connect to the internet and surf the web. However I cannot connect Gaim to the web, or download packages via Terminal. How can I sort this out?

Cheers :)

---

### Post by javierfh on 2006-10-23
> **spamzilla said:**
> Ok I can now connect to the internet and surf the web. However I cannot connect Gaim to the web, or download packages via Terminal. How can I sort this out?

Cheers :)

Hi,

i cant help you but i was wondering if you could help me :) 
I have similar card and couldnt make it to connect. I have SMC 2835w so any instructions or tips how to make it work?
Do you use dapper?

Javi

---

### Post by spamzilla on 2006-10-23
Hey, yeah I use Dapper.

All did was plug my card into the PCI slot, go to:

System > Admin > Networking > Activated ra0 wireless connection, then go into proporties, clicked enable this connection, entered in an essid, set connection config to DCHP and hit ok, and then ok again on the Network settings page. Finally I  did this:

> Try turning off ipv6 in Firefox as follows:

Enter about:config in the ff address field.

Enter ipv6 in the new Filter: field.

Now double click on the one & only line left in the display window of ff, to change it's boolean value to true.

I hope this helps :)

---

### Post by javierfh on 2006-10-23
im now at office but will try it as soon as i get home :)

Thanks a lot,

javi

---

### Post by javierfh on 2006-10-23
Hello,

i couldnt make it work.
When i do iwconfig i get similar info to what you get but all ceroed... :( so i assume no packages are going anywhere.

So probably something it is wrong, but first of all, so can you tell me or point me to some links where i can get these drivers that you mentioned?
It might be that my card it is not controled at all by the system.


I will keep trying..it works perfectly on windows side, i have dual boot laptop.

Javi

---

