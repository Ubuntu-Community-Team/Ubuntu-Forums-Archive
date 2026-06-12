---
title: "Cannot Connect to Wireless Networks (HP Mini 1000)"
date: 2015-07-03
forum: Networking &amp; Wireless
---

### Post by throwaway22 on 2015-07-03
Hello, 

I cannot connect to any wireless networks on my HP Mini 1000 running Xubuntu 14.04

The HP Mini has a broadcom 4312 lp-phy card. 

I have read bout the drivers, I have installed 14.04 three times now, the latest time with full updates.


I have read about the b43 and b43 legacy drivers which I have both tried, the STA drive is on there now and the laptop can see the networks, however after inputing the network password, the prompt returns and never connects.


The LAN port does work with no problems.



Im stumped here, any help would be much appreciated. 


Thanks.

---

### Post by kerry_s on 2015-07-03
run additional drivers, you just need the firmware. next time when you install, select " install third party ..." & you will have wifi after reboot.

i have the hp-mini 210-1010nr, currently running elementary os.

---

### Post by throwaway22 on 2015-07-03
I did select "install third party drivers" the STA driver is shown there, on the last install i purged and uninstalled it. and tried the b43 drivers. still nothing.

I can understand why I can see all the networks but not connect. Clearly the card is working, just not connecting.


Ideas?

---

### Post by kerry_s on 2015-07-03
did you run additional drivers ? it does it all automatically. it's slow but just wait.

---

### Post by throwaway22 on 2015-07-03
yes, and mine is showing exactly the same as yours.

---

### Post by kerry_s on 2015-07-03
try going to edit connections, delete/remove everything there. then reselect your wifi from the list.

click on the wifi icon-> edit connections

---

### Post by throwaway22 on 2015-07-03
tired that, first time it said "connection does not exist" after a restart, connected and everything works. Not sure what happened but all is well now.


Thanks kerry_s

Problems Solved!

---

### Post by kerry_s on 2015-07-03
that's good.
do you got the max ram ? 2gb

if so, elementary os has the wifi working from the get go. good to keep as a live, just in case. you need at least the 2gb to run well.

a few tips:
install zram-config to maximize the ram.
32bit runs better than 64bit, not sure why just does.
if you haven't updated to ssd, you should.
if you have tearing issues you need to do the 20-intel.conf fix:
gksudo mousepad /usr/share/X11/xorg.conf.d/20-intel.conf

```
Section "Device"
   Identifier "Intel Graphics"
   Driver "intel"
   Option "AccelMethod"  "sna"
   Option "TearFree" "True"
EndSection
```

---

