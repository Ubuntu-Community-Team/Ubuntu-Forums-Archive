---
title: "system says battery may be broken"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by kapi on 2009-11-16
Installed 9.10. It's Fantastic!

my system loads in 6 second to the login. Anyway when I am logged in I receive a message " battery at 36% may be broken" or words to that effect. There's nothing wrong with my battery.

 It occurs when the desktop is loaded and I presume it's loading the wireless drivers and battery etc.

I know it's just a glitch - any ideas?

---

### Post by ukripper on 2009-11-16
There is abug reported for this on launchpad - check this - [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/437745](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/437745)

---

### Post by fromthehill on 2009-11-16
It just means that the current maximum capacity is 36% from the capacity it was supposed to be when you bought it.

there is probably nothing wrong with your battery. it just wont last as long as when you bought it.

type this in a console window to view your battery information
cat /proc/acpi/battery/BAT0/info

edit: too late :P

---

### Post by kapi on 2009-11-16
Thanks,

At least the development team are aware of it now, so that's a start.

Kapi

---

### Post by ukripper on 2009-11-16
> **kapi said:**
> Thanks,

At least the development team are aware of it now, so that's a start.

Kapi

I would still encourage you to add your comments to that bug. It should help make 10.04 better.

---

### Post by Rinzwind on 2009-11-16
Hmmm. I fell for it: I ordered a new battery. I needed a 2nd one though so it was planned too ;)

Mine shows:

cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         7800 mAh
**last full capacity:      3054 mAh**
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 780 mAh
design capacity low:     236 mAh
capacity granularity 1:  78 mAh
capacity granularity 2:  78 mAh
model number:            DELL UW2808
serial number:           56
battery type:            LION
OEM info:                Sanyo

---

### Post by ukripper on 2009-11-16
> **Rinzwind said:**
> Hmmm. I fell for it: I ordered a new battery. I needed a 2nd one though so it was planned too ;)



it is always good to have two;)

---

### Post by Rinzwind on 2009-11-16
> **ukripper said:**
> it is always good to have two;)

I need 2 anyways. LOL. I always end up with no power in the middle of my journey, Now I end up very short though so it became more urgent to get me a 2nd battery :X

I sure hope this gets fixed quickly. Very quickly. See my battery is old (2 years almost) so it somehow did not come as a surprise (also cuz it once had a hit when my notebook fell),

But bogus messages like this is something that's going to annoy me very soon and then I will be looking around for another Linux release ;)

---

### Post by zl1ogx on 2010-01-13
Been looking through the forum for a fix for this, tried one of them but no joy on my eeepc 4g.

So anyone know of a fix that works?

Ian

---

### Post by tom.swartz07 on 2010-01-13
> **zl1ogx said:**
> Been looking through the forum for a fix for this, tried one of them but no joy on my eeepc 4g.

So anyone know of a fix that works?

Ian

there isnt much *to* fix. the only real way to make sure that it doesnt happen is to verify that your battery's capacity is truly at a critical point (anything below 50%) and if so, buy a new one.

Other than that, Youre pretty much relegated to acknowledging that you know your battery is broken.


Hope this helps!

---

### Post by grekko on 2010-02-05
> **tom.swartz07 said:**
> there isnt much *to* fix. the only real way to make sure that it doesnt happen is to verify that your battery's capacity is truly at a critical point (anything below 50%) and if so, buy a new one.

Other than that, Youre pretty much relegated to acknowledging that you know your battery is broken.


Hope this helps!

This isn't so much a fix as it only removes the warning message but, if you are so pissed off with it appearing at each boot here's a link that will show you how to stop it popping up.

[http://linux.aldeby.org/get-rid-of-your-battery-may-be-broken-notification.html](http://linux.aldeby.org/get-rid-of-your-battery-may-be-broken-notification.html)

---

### Post by zl1ogx on 2010-05-02
Just installed 10.04 netbook remix on my eeepc 4g and still getting the broken battery error.  King of thought that this was being looked at.

---

### Post by finalwebsites on 2010-05-07
I have the same problem for my ASUS eee 
the warning says that my battery has only 2.3% capacity, but this informationis wrong, still can use the laptop for 90-120 minutes

---

### Post by newtesla on 2010-05-18
Just to confirm: Eee 701 4G, 10.04 on 8GB SD card, battery had juice for over 2 hours, yet it constantly said that it is broken and had only 1.9% of capacity.
But, when clicked on battery icon and chose "laptop baterry" - it stated 9% (but it was over 1 1/2 hours running on battery already), energy when full 0.8Wh, and design energy 43.7Wh.

And it still runs for over 2 hours.

I think that the only correct measurement is voltage - soon after 6.9V reached, it went off - now charging, and it says 40% for 7.9V, which I think is ok.

Anyway, bug.

---

### Post by finalwebsites on 2010-05-18
Just installed my old Pentium4 latptop with ubuntu and I get the message that the capacity of my battery is less than 25% and that the battery might be broken.

The battery has 0% capacity and is broken, I think it's just a bug for several types of batteries. It's just disturbing that the message shows up after every start.

---

### Post by s.fox on 2010-05-18
Hello,

I noticed this yesterday on my AA1.  My battery was 40% charged and I received a notification that it was broken.  

-Silver Fox

---

