---
title: "Broadcom Corporation BCM4312 802.11b/g funny problem"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by toLa` on 2008-10-15
Hi guys,

Been a while since I last posted on here! :D

So I now have a new Dell laptop (Inspiron 1520), had it since around June time, and now only just started to get Linux fully back up and running on it.

Everything is working, including the Wireless, which dmesg grep states as being a Broadcom Corporation BCM4312 802.11b/g (Dell 1395 mini wlan card).

However, in order to get the wireless working, I must first disable, and then enable the driver for it in 'Hardware Drivers' under System > Administration. Once it has been re-enabled, it works great, but next time I reboot, I must do the same thing again.

I thought that it might be something to do with the Broadcom driver being blacklisted from startup, but from what I can see, that isn't the case.

Upon booting to the OS (which is Ubuntu 8.04.1 x64 (4gb ram...)) Hardware Drivers states that the device is enabled (tick in the box), but is not in use (red circle compared to the green one).

If someone could help me out with this that'd be ace, and apologies if this has been covered elsewhere, I have searched for workarounds on numerous occasions :o

Best regards,

Peter

---

### Post by Ayuthia on 2008-10-15
> **toLa` said:**
> Hi guys,

Been a while since I last posted on here! :D

So I now have a new Dell laptop (Inspiron 1520), had it since around June time, and now only just started to get Linux fully back up and running on it.

Everything is working, including the Wireless, which dmesg grep states as being a Broadcom Corporation BCM4312 802.11b/g (Dell 1395 mini wlan card).

However, in order to get the wireless working, I must first disable, and then enable the driver for it in 'Hardware Drivers' under System > Administration. Once it has been re-enabled, it works great, but next time I reboot, I must do the same thing again.

I thought that it might be something to do with the Broadcom driver being blacklisted from startup, but from what I can see, that isn't the case.

Upon booting to the OS (which is Ubuntu 8.04.1 x64 (4gb ram...)) Hardware Drivers states that the device is enabled (tick in the box), but is not in use (red circle compared to the green one).

If someone could help me out with this that'd be ace, and apologies if this has been covered elsewhere, I have searched for workarounds on numerous occasions :o

Best regards,

Peter
When you start up, can you check and see if the wl driver is loaded?  From the Terminal:
```
lsmod|grep wl
```If nothing returns, try the following:
```
echo wl | sudo tee -a /etc/modules
```
This will add the wl module to /etc/modules so that it is loaded upon booting.  

Hope that helps.

---

### Post by toLa` on 2008-10-15
> **Ayuthia said:**
> ... try the following:
```
echo wl | sudo tee -a /etc/modules
```
This will add the wl module to /etc/modules so that it is loaded upon booting.  

Hope that helps.

That worked a treat, once logged in, it now automatically connects to my home/work wifi :)

Many thanks for your help,

Peter

---

### Post by skippy2007_2335 on 2008-11-16
Great advice!  I had to do the same after deactivating the Broadcom STA wireless driver on my Ubuntu Mini 9.  I was trying it out, and it turns out it removed the wireless device from /etc/modules.

Thanks!

---

### Post by Timoteo32 on 2010-02-14
Did you restart of something??  I'm having the same problem and I can't seem to get it going. This is what came up for me:

t@dell-desktop:~$ lsmod|grep wl
wl                   1281364  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl

t@dell-desktop:~$ echo wl | sudo tee -a /etc/modules
[sudo] password for t: 
wl

t@dell-desktop:~$ 


Is that what was supposed to happen?  Still not working :(

---

