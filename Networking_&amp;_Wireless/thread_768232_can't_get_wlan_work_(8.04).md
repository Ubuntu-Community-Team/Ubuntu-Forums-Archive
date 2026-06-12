---
title: "can't get wlan work (8.04)"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by Vedelaar on 2008-04-26
Hello,

I have a problem with my wlan card.
I installed the newest ubuntu server (8.04) and dit the following tutorial:
[http://ubuntuforums.org/showthread.php?t=202834&highlight=wlan](http://ubuntuforums.org/showthread.php?t=202834&highlight=wlan)

But now, my system gives 4 errors:

1. intel_rnd: FWH not detected
2. ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command
3. ipw2200: Failed to send ASSOCIATE: Already sending a command.
4. BUG: soft lockup - CPU#0 stuck for 11s! [ipw2200/0:2906]

I get the first error while booting.
I get error 2 and 3 when typing my username
and i get the last error when shutting down my system or while restarting /etc/init.d/networking
after this last error, the system does nothing anymore, except repeating the error every second...

My network works only when i don't get the last error, this happens sometimes...

I have the following wireless card (found with lspci -v | less):
Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

Why do i get the errors, and what am i doing wrong?

edit: has it somethinh to do tith the fact my wlan is called eth1 and not wlan0 as they tell me in all the tutorials?

Thanks

Derk

---

### Post by LauraSakura on 2008-04-29
I have this problem too... and it worked in gutsy! but I started getting these error messages when I upgraded to hardy.

---

