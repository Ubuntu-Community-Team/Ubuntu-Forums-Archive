---
title: "Wireless stopped working"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by Macros42 on 2008-05-21
Wireless on my Dell Inspiron has been working perfectly for months but last night I turned it on and it has just stopped. No updates took place between it working and not. It's not detecting any wireless networks at all - even the neighbours which it usually sees so it's not just my router. I checked syslog and it seems to be deactivating eth0 at startup

[http://pastebin.com/m5fa5076a](http://pastebin.com/m5fa5076a)
and after turning off WPA
[http://pastebin.com/maf1902c](http://pastebin.com/maf1902c)

So I took the big hammer approach and upgraded from Gutsy to Hardy - it was something I'd planned anyway. But it makes no difference.

Any ideas what's gone wrong?

---

### Post by nixscripter on 2008-05-21
Network manager sometimes switches off interfaces when you do something like plug in an ethernet cable. The last few lines indicate it configured wired ethernet "instead of" the wireless. Do you have an ethernet cable plugged in? Try unplugging, rebooting, and see if that helps.

---

### Post by Macros42 on 2008-05-21
I didn't have an ethernet cable plugged in. I did later on to post the logs in pastebin but whether the cable is in or not I get the same result.

---

### Post by nixscripter on 2008-05-22
If you enable the interface manually and scan do you get anything?

```

sudo ifconfig eth0 up
sudo iwlist eth0 scan

```

This is just to make sure the hardware is working as expected.

---

