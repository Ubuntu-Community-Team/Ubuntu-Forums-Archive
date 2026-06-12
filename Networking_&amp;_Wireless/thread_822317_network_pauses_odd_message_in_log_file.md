---
title: "network pauses odd message in log file"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by marks_linux on 2008-06-08
since one of the recent kernel updates to Hardy I have periodic network 'pauses' This happens if I am on either a wireless connection and also a vodafone connection using an Heuwia e800.

If surfing web then grabbing a page pauses for up to a minute. if on Skype the call drops.

In /var/log/messages I get an entry in the following format that corresponds to the pause:

date time my  machine name -- my username --

It may be a red herring but I've kept the log going for 4 instances of this and they are almost exactly 20 minutes apart?

Any clues?

---

### Post by chili555 on 2008-06-08
Like this one on my machine?> Jun  8 08:17:40 LAPTOP60 -- MARK --Hmmm, wonder why *your *name would appear on *my* computer.

Actually, -- MARK -- is just *messages* way of saying that nothing is going on that's noteworthy, but time is marching on, so I'll make a timestamp; every 20 minutes seems good!

It's a coincidence that your name is Mark.> This happens if I am on either a wireless connection and also a vodafone connectionThis suggests the issue is not your wireless, but your router or ISP.

You might also check:```
dmesg | grep wlan0
```Substitute your interface if it's not wlan0. When there is a 'pause' can you ping the access point?```
ping -c3 192.168.0.1
```Substitute your access point's address here. If there are no or very slow ping returns while a pause is going on, I'd look first at the router. Likewise, check pings to your ISP:```
ping -c3 dsl.bellsouth.net
```

---

### Post by marks_linux on 2008-06-11
yup the name coincidence threw me!

Anyhow it seems the network pause coincides with this message in /var/log/messages

 /USR/SBIN/CRON[20000]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })

this pauses the network, no internet, no pings, no email send recieve.

Nothing listed in my crontab and sudo crontab -l lists nothing either.

---

### Post by chili555 on 2008-06-11
Please see: [http://www.go2linux.org/sysstat-linux-performance-monitor-toolkit](http://www.go2linux.org/sysstat-linux-performance-monitor-toolkit)

It seems that *sysstat* is collecting and writing performance data. I am not familiar with sysstat myself. Perhaps you have installed a panel applet or some such that reports CPU cycles, memory usage, HDD activity, etc. 

These things are supposed to run quietly in the background, not hijack the whole computer.

You might search these forums for *sysstat*. You can always remove it.

---

### Post by marks_linux on 2008-06-12
thats done the trick, connection seems fine now. How odd!!

---

