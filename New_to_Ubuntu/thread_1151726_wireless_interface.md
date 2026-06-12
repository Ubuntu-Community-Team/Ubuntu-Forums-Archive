---
title: "wireless interface"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by pramodmmuraly on 2009-05-07
i have upgraded my jaunty kernel from 2.6.28-11-generic to 2.6.28-12-generic in my dell 1420 inspiron laptop but now my wifi driver is not showing,and wireless is not working.
output of ifconfig doesn't shows the wireless interface.
but in my previous kernel it is shown as eth1 but now it is missing.

Broadcom Corporation BCM4312 802.11b/g (rev 01) is my interface and is showing in lspci output.
iwconfig is also not showing the interface

plz any body help me in this issue.

---

### Post by anewguy on 2009-05-07
Ok, I've never used the built-in driver, but it should be there for the 43xx series I think.  Check under system/administration/hardware drivers and see if it shows a restricted driver.  It would probably say not in use and you would just need to enable it.

If not, and IF you used ndiswrapper previously, ndiswrapper and the Windows driver should work for that chipset.

Not having used the built-in driver, someone else would need to help you there (there are many posts on the forum for it).

If you use ndiswrapper, I can help you with that.

Dave :)

---

### Post by lkraemer on 2009-05-07
It would really be nice if you had some idea on what guide or HOWTO:
you followed in getting it working the first time.

If you Open a Terminal Window, cut & paste each line - one at a time:
```

lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwconfig 

cd /
cd /lib/firmware
ls -alt
cd /b43
ls -alt


```
Then post the output, as this will give us a clue as to what you have done.

You either used:
1. Ndiswrapper and a Windows Driver....bcmwl5.inf & sys
2. bcm43xx module and some Firmware.... B43 & B43legacy  *.fw
3. b43 and some Firmware that was downloaded/extracted when you
   enabled the Driver.

lkraemer

---

### Post by pramodmmuraly on 2009-05-13
thanks for the interest
actually i dont used any ndiswrapper in jaunty.
i m using the proprietry driver supported by ubuntu only.
but now its ok jaunty is supporting the driver now.
thanx

---

