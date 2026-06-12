---
title: "[SOLVED] Wireless doesn't work with Wicd after running Kismet"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by jmjohn on 2008-08-06
Hello all,

I'm having somewhat of a problem and I would greatly appreciate it if anybody has any ideas for me.

After I run Kismet and shut down, my wireless doesn't work.  On reboot, the system works fine.

This didn't happen when I was using the default network manager for Ubuntu, but I just switched to Wicd.

I've tried
```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
sudo ifdown -a
sudo ifup -a
```

...in the hopes that by resetting the wireless configuration it would restore the system to pre-kismet defaults.  However, these commands didn't work.  Are there any other network-reset-type commands to try? 

Any ideas?  I very much appreciate any help.

Thanks,
glass.dimly

P.S. I've got an Intel 4965 802.11a/g/n Dual-Band Mini Card running the wext driver, with Hardy 8.04 vanilla kernel.  Let me know if any other info is needed.

---

### Post by postpwnjudgemint on 2008-08-09
hey i had the same problem and i am very excited to help out a fellow linux distro user. ubuntu rocks! so anyways all you have to do is run the following code:

sudo airmon-ng -start <interface> [<channel>]

have fun if this doesnt work feel free to email me.

---

### Post by jmjohn on 2008-10-28
This is a driver failure to return to monitor mode after exiting Kismet. Here's my workaround:

If you type $ sudo iwconfig
You may see something like Mode:Monitor, which is rfmon mode.

We want to change that to Mode:Managed

Thus, try to connect to a wired network in Wicd. This shuts off the wlan0 or whatever interface you're using for wireless and attempts to use your eth0 interface.

Next:
$ sudo iwconfig wlan0 mode managed

Changes the mode of wlan0 to managed, which allows you to use Wicd for wifi once again.

Make sure to substitute "wlan0" for the name of the interface you're using for wireless.

-glass.dimly

---

### Post by jackgu1988 on 2009-08-11
hi! when i try ```
sudo iwconfig wlan0 mode managed
``` i get that wlan0 is already in use! so the best thing to do is: ```
sudo airmon-ng stop wlan0
sudo iwconfig wlan0 mode managed
```works perfect for me!

---

