---
title: "Something Simpler than lshw &amp; lspci"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by Andavane on 2008-12-16
Have found about lshw & lspci which give masses of information.

Is there some simple way of finding basic information, i.e.
computer name
basic specs such as the MAC of this PC and device name
regards
JOhn

---

### Post by Andavane on 2008-12-16
more info:
on his Netgear Wireless ADSLK router, I see this device listed as
"UNKNOWN" followed by
the MAC address

---

### Post by MockY on 2008-12-16
System - Administration - System Monitor. Click the System tab. That gives you some basic information about your system.

---

### Post by mc4man on 2008-12-16
Look at lshw -help or man lshw

 sudo lshw -short

 sudo lshw -C network

Ect. ect.

sudo lshw -html > hardware.html (gives complete in readable form in home folder

---

### Post by northern lights on 2008-12-16
You can invoke 'lshw' with the '-C *class*' or '-class *class*' option to only show the given class of hardware.
The various classes can be found using 'lshw -short' or 'lshw -businfo'.

In your case, where you want info on your network devices, run```
sudo lshw -C network
```Further, for the MAC address, check```
ifconfig
```and the entry called *HWaddr*.

---

### Post by Andavane on 2008-12-16
> **MockY said:**
> System - Administration - System Monitor. Click the System tab. That gives you some basic information about your system.
Thanks, useful.
To be more specific, on his wireless router, I am getting
"UNKNOWN" followed by the MAC address of this computer,
even tho I named the computer "vaayubuntu-0" when setting up Hardy Heron.

regards John

PS: This is probably a different threaD now

---

### Post by northern lights on 2008-12-16
The whole network is functional, it's just that the router doesn't show a name? Does it matter than?

If I got you wrong can you please further describe the nature of your problem?


P.S.
Dude, your awesome. Can you teach me how to be in two places at the same time? I'd really love to be able to do that.
;-)

---

### Post by Andavane on 2008-12-17
> **northern lights said:**
> The whole network is functional, it's just that the router doesn't show a name? Does it matter than?

If I got you wrong can you please further describe the nature of your problem?


P.S.
Dude, your awesome. Can you teach me how to be in two places at the same time? I'd really love to be able to do that.
;-)

Hi, what's going on has its own thread now, viz:
[URTL]http://ubuntuforums.org/showthread.php?t=1012664[/URL]

Yes you're right - I guess it doesn't really matter, but with all these MAC codes, it's easier form to remember the name tag ;)
Regards
John

>"Can you teach me how to be in two places at the same time? I'd really love to be able to do that."
(1)[metaphysical]First you have to realise you're everywhere... thereafter 2 places is a doddle. ;)
(2) [empirical] Indian family takes up so much time; with modern communication the same same domestic things need attending to whether I be 'here' or 'there' (wherever those 2 places might be said to be), but do perchance need to check from time to time where the body is.
As you age it can become a problem remembering location ;)

---

