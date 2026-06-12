---
title: "iwpriv, 2.6.24 kernel, and iwl3945?"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by mma8x on 2007-12-17
i've been messing around with the [[COLOR="Red"]zen[/COLOR]]("http://ubuntuforums.org/showthread.php?t=623874&highlight=zen") 2.6.24 kernel for a 64 bit thinkpad r61 running gutsy.  

so i've nearly got it configured perfectly, and brightness finally works using the nvidia beta driver.  

the last sticking point is the wifi.  i am now using the uwl3945 driver within the new kernel.  everything works well except that i am unable to use iwpriv settings to set power control; this is a significant power drain (at least 1 w).  my error message is:
```
wlan0     no private ioctls.

```

i can't find any mention of this anywhere else, so i'm not sure if it's a configuration issue (the interface was named eth1 using the stock kernel) or if this is the result of the new module.  anybody have any insight?

---

### Post by mma8x on 2007-12-20
ok, still haven't figured this out, but a workaround is to set 
```
echo 7 > /sys/bus/pci/drivers/iwl3945/0000\:03\:00.0/power_level

```

power consumption when idling is about 0.1W.

---

