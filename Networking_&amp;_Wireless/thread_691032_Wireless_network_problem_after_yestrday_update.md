---
title: "Wireless network problem after yestrday update"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by luka78 on 2008-02-08
Hi...

After last update i lost wth1 from all settings and now i don't have wireless. I Use Attheros chip and it all works fine from my 7.04 Ubuntu installation. Now, i don't know what happened, i just lose eth1 from Network settings.

What you suggest me to do first?

Thank you

---

### Post by Hightide on 2008-02-08
Hi luka78

Can you post output from

lshw -C network

regards

:)

---

### Post by lansalot on 2008-02-08
Hi

I'm getting the same after the update, output is :

* - network UNCLAIMED
description: Network Controller
product: PRO/Wireless 2200BG Network Connection
vendor: Intel Corporation
physical id: 5
bus info: pci@0000:06:05.0
version: 05
width: 32 bits
clock: 33Mhz
capabilities: pm cap_list
configuration: latency=32 maxlatency=24 mingnt=3

Grateful for any help, thanks :)

---

### Post by lansalot on 2008-02-08
Going to try this one when I get it home, but in the meantime if anyone else has any suggestions :

[http://ubuntuforums.org/showthread.php?t=345870](http://ubuntuforums.org/showthread.php?t=345870)

---

### Post by lansalot on 2008-02-08
Err. Embarassing. A handful of reboots (in and out of XP, surfing here etc) and I'm back up and running again.

Didn't change a thing.

lshw is now showing a logical name again. Very odd. That'll teach me not to run up the red flag so quickly in the future :P

---

### Post by evymetal on 2008-02-10
well I'm having the same problem, straight after the recent Kernel update ( which also had a restricted driver update I believe) - I've rebooted several times and can't get my wireless interface recognised.

Guess I'll carry on re-booting and hope, though.

---

### Post by evymetal on 2008-02-10
Update:

My wireless is now working again. Not certain if it was anything I did, but what I did was :

Re-boot several times (no luck)

sudo /etc/init.d/networking force-reload (no luck immediately)

waited 10 minutes (well, my girlfriend nicked my laptop for 10 minutes)

- It was working! 

so, I guess that network manager needs a few minutes to update - not sure if it was reloading my networking that did it or rebooting, though.

---

### Post by Hightide on 2008-02-10
HI Lansalot

The output from ishw c network states 'Netwok UNCLAIMED' which indicates that there is a driver problem.

see Kevdog's wireless [tutorial]("http://ubuntuforums.org/showthread.php?t=571188"), it may help/


Regards

:)

---

