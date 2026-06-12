---
title: "can't get xmacrorec2 to work"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by PGScooter on 2009-07-14
Hi, I've tried xmacrorec2 but can't seem to get it to work. It just does nothing after it asks for a "quit key"

```

pedro@system76-pc:~$ xmacrorec2 > macrofile
Server VendorRelease: 10600000
XRecord for server ":0.0" is version 1.13.


Press the key you want to use to end the application. This key can be any key, 
as long as you don't need it while working with the remote display.
A good choice is Escape.

The chosen quit-key has the keycode: 38
XQueryPointer returned: 1
Got Start Of Data
Skipping...

```
I try a bunch of stuff and then have to press ctrl-c to get out of it. Nothing goes into macrofile.

I've done a lot of searching and have found people who have had similar errors but could not find a solution.

I have also tried gnee, but there is an error that comes up for me for which the developer says he is working on a work around.

Thanks

---

### Post by PGScooter on 2009-07-15
Here is the bug report:
[https://bugs.launchpad.net/ubuntu/+source/xmacro/+bug/367685](https://bugs.launchpad.net/ubuntu/+source/xmacro/+bug/367685)

---

