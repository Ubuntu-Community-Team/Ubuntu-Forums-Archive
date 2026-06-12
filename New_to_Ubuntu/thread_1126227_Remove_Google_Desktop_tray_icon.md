---
title: "Remove Google Desktop tray icon"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by hesjnet on 2009-04-15
Hi Guys. I'm doing some cleaning on my desktop and shortcuts and I'm wondering if it's possible to have Google Desktop running without the icon in the panel / tray?

I found out that i could remove the anoying Opera icon by changing command from
```
/usr/bin/opera
```
to
```
/usr/bin/opera %u -notrayicon
``` 

That worked great! But doesn't work with Google Desktop.

Any ideas?

---

### Post by hesjnet on 2009-04-17
bump

---

### Post by Knacker on 2010-07-14
bumping an old question again to see if anyone has figured a trick out for this. 

it seems even more relevant since the google desktop icon has stopped rendering as you'd hope it would (i.e. with a transparent background) in 10.10.

any ideas?

---

### Post by stringpicker on 2011-01-09
I had the same issue. I finally ended up removing the Indicator applet by right clicking on the area and selecting "remove from panel", then manually adding it again.

Google Desktop still works without the icon in the panel. 

K.

---

### Post by sior on 2011-08-21
Bump. Any hints on where I can find the google desktop icon would be appreciated.

Thank you in advance.

---

### Post by sior on 2011-08-21
In case anyone is looking for the Google Desktop icon, it is located at /opt/google/desktop/resource .

---

### Post by DancerJeff on 2011-11-29
I run: ps -A | grep gdl
 3412 ?        00:00:13 gdl_box
 3419 ?        00:00:00 gdl_service
 3420 ?        00:00:00 gdl_config
 3421 ?        00:00:00 gdl_indexer
 3422 ?        00:00:03 gdl_fs_crawler

I then kill gdl_box.  The icon is gone, my cpu is back, and Google desktop search still works.

As a side note: I had to log into gnome classic to get link to google desktop, I then bookmarked it and can use it in kde4

---

### Post by DancerJeff on 2011-12-06
This command will start google desktop, and then kill the system tray icon.

```

/opt/google/desktop/bin/gdlinux; sleep 1; pkill gdl_box

```

Google desktop works for another minute or two, once it realizes the tray is gone it also quits. 

This allows you to us Google desktop search when you need with no cpu slowdown.  If is not there, simple run the command again.

I could possible at this to cron job every minute.  The command needs to be ran whenever the "gdl_service" process ends. Running it again is fine.

```
ps -A | grep gdl_
```
11144 ?        00:00:00 gdl_service
11145 ?        00:00:00 gdl_config
11146 ?        00:00:00 gdl_indexer
11147 ?        00:00:03 gdl_fs_crawler

---

