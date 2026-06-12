---
title: "Initialzing Squid Cache Folder"
date: 2016-04-27
forum: Networking &amp; Wireless
---

### Post by keepitperso on 2016-04-27
Hi Guys,

So I have installed squid on my little raspberry pi. It actually works! I have a bug when I try to initialize my cache squid directories, (and before anyone says, i have checked that it has the correct user access and I do not believe it is the issue here as it has created all the other folders...)

Here is what I get when I run :
```
squid3 -z
```

```
root@pi:~# squid3 -z
root@pi:~# 2016/04/27 09:48:00 kid1| Set Current Directory to /var/spool/squid3
2016/04/27 09:48:00 kid1| Creating missing swap directories
2016/04/27 09:48:00 kid1| /cache exists
2016/04/27 09:48:00 kid1| Making directories in /cache/00
2016/04/27 09:48:00 kid1| Making directories in /cache/01
2016/04/27 09:48:00 kid1| Making directories in /cache/02
2016/04/27 09:48:00 kid1| Making directories in /cache/03
2016/04/27 09:48:01 kid1| Making directories in /cache/04
2016/04/27 09:48:01 kid1| Making directories in /cache/05
2016/04/27 09:48:01 kid1| Making directories in /cache/06
2016/04/27 09:48:01 kid1| Making directories in /cache/07
2016/04/27 09:48:01 kid1| Making directories in /cache/08
2016/04/27 09:48:01 kid1| Making directories in /cache/09
2016/04/27 09:48:01 kid1| Making directories in /cache/0A
2016/04/27 09:48:01 kid1| Making directories in /cache/0B
2016/04/27 09:48:02 kid1| Making directories in /cache/0C
2016/04/27 09:48:02 kid1| Making directories in /cache/0D
2016/04/27 09:48:02 kid1| Making directories in /cache/0E
2016/04/27 09:48:02 kid1| Making directories in /cache/0F
```

I have let it run for hours, several times. Deleted and recreating the cache directory, whatever happens, it hangs, it stops at the last line and does not come back to prompt.
```
Making directories in /cache/0F
```
I have no error message, it just hangs.

I would be grateful if anyone can help this command run properly without me having to stop it every time. After stopping it, The 0F folder is created, I just do not know if it has created everything it needs and if it needs to run more things.

Emmanuel

---

