---
title: "Udevd[81] Error Message"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by lhb1142 on 2010-11-28
I am using an Asus Eee PC 1000/Linux (Intel Atom processor N270 @ 1.60 GHz) which I converted from its original (now non-supported) Linux distribution to Ubuntu 10.04. Everything worked fine.

Recently I effected a network upgrade to 10.10. Everything appeared to go smoothly and everything worked; I have few programs installed on this simple computer, preferring to use it mostly for e-mail.

However, now when I boot, after entering my BIOS password but before I see the Ubuntu login screen, I am getting many messages (all reading the same except for the [number]:

Udevd[81] worker did not accept message [number] Connection refused -1 Kill it

(something like that)

and I see the 10.04 background rather than the 10.10 one. Then the login screen appears, I log in normally, and within a few seconds the background changes to the 10.10 one and everything else proceeds normally.

I read on a post how to upgrade the udev (udevd) and it worked - until I used BleachBit which seemed to undo the udev upgrade.

This anomaly is causing me no real problem but I'd like to get rid of it if anyone has a fix (a simple one please, though I can and do use the Terminal).

Thanks for reading this and for any help.

Lawrence

---

### Post by jtarin on 2010-11-30
Sounds like you didn't get a complete update. Go to Synaptic package manager and look for the Plymouth package and see if it needs an update.

---

### Post by lhb1142 on 2010-11-30
> **jtarin said:**
> Sounds like you didn't get a complete update. Go to Synaptic package manager and look for the Plymouth package and see if it needs an update.

Dear 'jtarin',

I tried reinstalling every 'plymouth' component which was installed (it seems that I had and, of course, have all that are necessary) but the problem persists.

Not only do I get that Udevd[81] error (the worker will not accept the message) but when the background appears prior to the Login dialog, it is the 10.04 background. 

I log in normally and that background persists; once the panels pop up, the background instantly changes to the 10.10 background.

I presume this is some sort of bug which affects certain computers; I do not have this problem on my Acer Extensa 5620-6419 machines (two of them) and my ZaReason Teo Netbook, all of which are running 10.10 (as is the Asus Eee PC 1000). (I am using the standard Ubuntu Desktop Edition, not the Nebook Remix; while I effected a 'clean' install on one of my Acers, the other one, the ZaReason, and the Asus had network upgrades from 10.04.)

As I said, it doesn't appear to affect any of the functions; the Asus works normally but it is an annoyance which I should like to eliminate.

Perhaps my computer needs new workers who will accept messages!   ;-)

Thank you for writing and for trying to help me.

Lawrence

---

### Post by GregorMaxwell on 2010-12-08
I have exactly the same error log on boot up with my eeepc 901 running 10.10 netbook remix. I cleanly installed 10.10 from a USB stick and have previously used 10.04 nbr, 9.04 nbr, and the terrible Xandros on the same machine. As suggested, I have checked the Plymouth components in synaptics and all are up to date.
Any further ideas on this annoyance?
Thanks,
Gregor

---

### Post by rulorojo on 2011-01-04
I've got exactly the same problem during boot , using Ubuntu 10.10 installed from USB on a Asus 901. Otherwise everything running smooth.

---

### Post by rebecacaca on 2011-01-04
I've got this problem too - has anyone filed a bug report?

Edited to add: I'm using an ASUS EEE 900

---

### Post by lhb1142 on 2011-01-05
It seems that at least certain people, including myself, all of whom are using Asus netbook computers, have this problem.

Can I assume that you all have the Intel Atom N270 (running at 1.60 GHz) chip in your computers?

If so, this would appear to be a 'bug' with that particular chip.

It did not occur in Ubuntu 10.04. Perhaps in 11.04 it will disappear.

In any case, it is more of an annoyance than a real problem as it does not seem to affect the computer in any other way.

Nonetheless, it would be helpful if someone could a) determine the cause and b) correct it.

---

### Post by dude1phoenix on 2011-01-06
Hello. I submit that bug on launchpad: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/698125](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/698125) :-|

---

### Post by arsya on 2011-01-13
I have the same problem on my dell mini 9. Does this issue occur only on netbook?

---

### Post by jtarin on 2011-01-13
> **arsya said:**
> I have the same problem on my dell mini 9. Does this issue occur only on netbook?It would be of some certainty to assume as posted above if you have that chip you have this problem. I for one do not know if this chip is only found in Netbooks but Intel states it is used in netbooks, handhelds and  smartphones, to list a few.

---

### Post by potatan on 2011-02-06
I get the same issue on my Dell Mini 10V, with an Intel Atom processor.

---

