---
title: "Log files, where?"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by tacomodo on 2009-05-01
Sitting happily ls'ing in a terminal window my computer all of the sudden just rebooted itself.

Are there any logfiles I can check to see if it was anything software related?

And also, if anyone happens to know at the same time - where are the ufw log files?

---

### Post by y_garti on 2009-05-01
use the gnome-system-log :)

---

### Post by MrWES on 2009-05-01
> **tacomodo said:**
> Sitting happily ls'ing in a terminal window my computer all of the sudden just rebooted itself.

Are there any logfiles I can check to see if it was anything software related?

And also, if anyone happens to know at the same time - where are the ufw log files?

System | Administration | System Log -- from there you can view and review system logs.

Bill

---

### Post by PriceChild on 2009-05-01
Incase you ever find yourself without a gui, you can see the logs displayed there in /var/log

---

### Post by MrWES on 2009-05-01
> **PriceChild said:**
> Incase you ever find yourself without a gui, you can see the logs displayed there in /var/log

Nod...

```
dmesg | tail
```
```
dmesg | more
```
```
dmesg | less
```
or

```
cat /var/log/auth.log | less
```

Lots of ways to do many things in Ubuntu!

Bill

---

### Post by tacomodo on 2009-05-01
Great, thanks for the replies guys!

Didn't make me any wiser, though...

I see maybe a few hundred UFW BLOCK INPUT log messages, all from addresses I don't know and only on my torrent port I have forwarded. Any chance this could be the source of my sudden reboot? Feels like I'm being hacked... :confused:

---

### Post by cariboo on 2009-05-01
I would check for hardwre problems, before blaming the operating system. 

As far as blocked ip addresses, that's normal. I don't check the firewall logs often, but there are usually hunderds of blocked ip addresses every day.

As long as the ip addresses are blocked, your firewall is doing it's job.

---

### Post by tacomodo on 2009-05-01
hehe I wasn't blaming the operating system.

The blocking is well and good but **could** have been an indicating someone was trying something, and finally succeeded.

Anyway, thanks again for the replies

---

### Post by MrWES on 2009-05-01
> **tacomodo said:**
> hehe I wasn't blaming the operating system.

The blocking is well and good but **could** have been an indicating someone was trying something, and finally succeeded.

Anyway, thanks again for the replies

Did you take at look at 

/var/log/auth.log ?

---

### Post by rannable on 2009-07-28
go to system/administration/log file viewer

---

