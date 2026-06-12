---
title: "Wired Ethernet Not Coming Back From &quot;Sleep&quot;"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by Nullack on 2008-06-07
Hi folks :) Really could do with some help here please Im out of items to try :(

So I have a wired 100mb ethernet nic, standard via rhine II. It works fine, Ive got static IPs running to my gateway. I have the power settings in Ubuntu Hardy set to turn of the monitor only and not to sleep. Strangely, if I leave the PC on and come back to it, I wake up the monitor with the mouse but I have no network connectivity despite eth0 being online. I cant even ping my gateway when the fault happens after resuming from a period of no network traffic.

If I do an ifconfig eth0 down and then up, it doesnt fix it. Ive tried static and DHCP setups and both have the problem. The only way to bring the network back is to reboot the machine all together.

I dont know how to diagnose this further :confused:

---

### Post by Nullack on 2008-06-07
Still scratching my head on this :confused:

---

### Post by Nullack on 2008-06-08
Option one: Cry
Option two: Throw PC into the trash
Option three: have beer

Im having a beer. Free beer for anyone who enters legend status by helping me! Love yas :)

---

### Post by darascon on 2008-06-08
I am having the same problem as well. All my internets drop when i go into sleep. Even though my wireless will not work, the card looses recognition. My hard eth line drops as well. Anyone have ideas?

---

### Post by Nullack on 2008-06-11
Im outta beer and Im getting mistry :( Hehe

Anyway:

sudo ifconfig down / up doesnt work

Doing DHCP or static IPs doesnt work

Nothing seems to work except a reboot????

Help please!

---

### Post by Nullack on 2008-06-11
Well Ive bugged it, and it turns out another person already reported the issue way back in 2007.

[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/111282](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/111282)

If you have this bug too why not attach your sys info to the bug or assist in helping understand / fix it better :) Im outta ideas now, all my comments are in the bug on launchpad.

Think I need a scotch, hard liquor time now :)

---

### Post by Nullack on 2008-06-12
In case anyone into the future searches this thread I have come up with a workaround that atleast prevents needing to reboot:

[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/111282](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/111282)

I need to share the love, but would someone please, pretty please, do a root cause fix of the bug if they can :guitar:

---

