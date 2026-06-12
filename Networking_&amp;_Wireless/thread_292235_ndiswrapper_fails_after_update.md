---
title: "ndiswrapper fails after update"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by somersetsimon on 2006-11-03
I thought I'd cracked wireless networking, but it all went wrong again :-k 

I did a clean install of Dapper. Installed the very latest version of ndiswrapper (28?) and the very latest version of my Windows driver (zd1211b). I followed all the ndiswrapper commands and my wireless network was available immediately as wlan0 and iwconfig and ping showed it was connected :D :D 

A message popped up saying that updates were available, so I installed and rebooted. After rebooting, wlan0 was nowhere to be seen :( 

I tried to go through the ndsiwrapper process again and got:

[HTML]simon@linux1:~/InsDrvTemp_USB$ sudo ndiswrapper -i ZD1211BU.INF
installing zd1211bu ...
simon@linux1:~/InsDrvTemp_USB$ ndiswrapper -l
installed drivers:
zd1211bu                driver installed, hardware (1582:6003) present
simon@linux1:~/InsDrvTemp_USB$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-27-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted[/HTML]

1) Did the upgrade kill it? I think the kernel went from 15.25 to 15.27

2) Did the reboot kill it?

How do I get ndiswrapper working again?

---

### Post by encompass on 2006-11-03
When you have dirvers that are not opensource and part of ubuntu you have to reinstall them to get them to work with the new kernel.
When you boot you can press escape and go to the old kernel and use it wth the working, we hope, driver.  Until you get it installed with your new kernel.

---

### Post by odelay on 2006-11-03
I am, by no means an expert on this, but each time I did some sort of update (or sometimes just restarted my computer) and wireless broke, I just type this in a terminal.

```
sudo depmod -a
sudo modprobe ndiswrapper
```

That get's my green wifi light back on and I'm able to see wlan0 in networking.

You may need to redo the ndiwrapper thing, but it never hurts to do this first.

---

### Post by somersetsimon on 2006-11-03
Still get the same error after trying depmod

---

### Post by somersetsimon on 2006-11-03
> **encompass said:**
> When you have dirvers that are not opensource and part of ubuntu you have to reinstall them to get them to work with the new kernel.
When you boot you can press escape and go to the old kernel and use it wth the working, we hope, driver.  Until you get it installed with your new kernel.

That was it. Thanks. I reinstalled ndsiwrapper and everything is fine.

---

