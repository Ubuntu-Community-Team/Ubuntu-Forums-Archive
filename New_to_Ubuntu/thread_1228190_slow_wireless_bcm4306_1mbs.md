---
title: "slow wireless bcm4306 1mb/s"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by JohnCDI on 2009-07-31
I've been reading tons of different articles about different solutions and I can't seem to find a way to get this to work. I'm using jaunty and ive got a  bcm4306 with the b43 drivers ive tried ndiswrapper and with no success im still trying to figure it out. I can connect to my network fine just with bouncing speed rates sometimes at most up to 11Mb/s ive tried to set it manually using iwconfig and it will display the set rate but is still actually much slower. Any help would be greatly appreciated.

---

### Post by Liolikas on 2009-07-31
Force g mode somehow in options.

---

### Post by swoll1980 on 2009-07-31
This might not be the best option, but I used ndiswrapper, and the win drivers for my broadcom, and it work great. I had the same problem you did. The Linux driver worked, but It was extremely slow.

---

### Post by JohnCDI on 2009-07-31
well than maybe its possibly how im installing ndiswrapper with the driver could you possibly show me how you went through the install when i tried i often got the error "unable to see if hardware is present" but then after it showed it as the driver and on the graphical ndis it even said underneath it hardware present "yes" i have blacklisted the other drivers but im still having this problem thanks for your reply

---

### Post by jacklinux on 2009-07-31
if your not worried about breaking the router/modem try flashing the firmware to make sure your router is at 100%. i flashed mine and found only 75% was being used since i changed settings my router now get 5MB.

---

