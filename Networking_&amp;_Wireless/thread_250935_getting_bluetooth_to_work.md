---
title: "getting bluetooth to work"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by Rule on 2006-09-04
Hi, I got a bluetooth phone (nokia 6265i) and I would like to copy/move files from phone to pc and vice versa.

I downloaded gnome-bluetooth but when I run gnome-bluetooth-manager I keep getting

```
  File "/usr/lib/python2.4/site-packages/gnomebt/manager.py", line 274, in ?
    BTManager ().main ()
  File "/usr/lib/python2.4/site-packages/gnomebt/manager.py", line 85, in __init__
    if not self.btctl.is_initialised():
gobject.GError: Can't get device id of hci0

```

I have a HP L2000 laptop, OpenSuSE was able to detect my bluetooth but in Dapper it doesnt even show up when I use "lspci -v"

TIA

Rule

---

### Post by Rule on 2006-09-04
well I found this guide [http://ubuntuforums.org/showthread.php?t=34740&highlight=obex](http://ubuntuforums.org/showthread.php?t=34740&highlight=obex) 

and when I run "hcitools scan" all I get is "Device is not available: No such device" which is weird cause my bluetooth was working on OpenSuSE :confused:

---

