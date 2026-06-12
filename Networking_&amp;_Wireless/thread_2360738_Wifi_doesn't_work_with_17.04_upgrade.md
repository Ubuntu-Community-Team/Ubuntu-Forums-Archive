---
title: "Wifi doesn't work with 17.04 upgrade"
date: 2017-05-07
forum: Networking &amp; Wireless
---

### Post by waltd on 2017-05-07
Hi all,  
    Xubuntu 16.10 was running well on my laptop.  When I upgraded to Xubuntu 17.04 the wifi didn't work.  My laptop has Realtek.  The wifi progress wheel just kept circling without stopping.  So I restored my disk back to 16.10.  Any suggestions on getting the wifi to work in 17.04?  Thanks.

---

### Post by &amp;KyT$0P# on 2017-05-08
Does this help? - [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1681513]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1681513")

---

### Post by waltd on 2017-05-09
I did what was suggested in the link you posted.  I added wifi.scan-rand-mac-address=no to the NetworkManager conf file.  But the problem still continues.  With Xubuntu 16.10 I have wifi connectivity, but with 17.04 I don't have it.  The wifi status bar just keep spinning.  I have a Realtec wifi card and a Netgear Nighthawk wifi router running DD-WRT firmware.

---

### Post by howefield on 2017-05-09
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by Dennis N on 2017-05-09
>  I added wifi.scan-rand-mac-address=no

My connectivity returned in 17.04 when I set the value to 0. 

```
wifi.scan-rand-mac-address=0
```

Try that.

---

### Post by waltd on 2017-05-09
I tried changing [COLOR=#000000][FONT=&quot]wifi.scan-rand-mac-address=no to [/FONT][/COLOR][COLOR=#000000][FONT=&quot]wifi.scan-rand-mac-address=0, but neither option worked with my Xubuntu 17.04 laptop.  I reinstalled Xubuntu 16.10 and the wifi connection is working.  I think this wifi problem is being looked into by Ubuntu's development team.  Any suggestins?  Should I just hang out with 16.10 for a future release or try another distro?  I appreciate the help.      [/FONT][/COLOR]

---

### Post by wildmanne39 on 2017-05-09
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

Run it from 17.04

---

