---
title: "Where is Battery Indicator Ubuntu 10.10 netbook"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by mirroalex on 2010-10-12
Hi everyone:KS,

I'm new to ubuntu netbook edition or in more general to ubuntu, i had ubuntu 10.04 desktop previously so it had battery indicator but today i have installed ubuntu 10.10 netbook and i can't find battery indicator or any place where i can check my battery state.

is there anyone who can bring me to light? :guitar:

---

### Post by Hippytaff on 2010-10-12
Not sure where the icon is...still on 10.04 and its on the panel, but you can get the info from the terminal

```

acpi

```

You can open a terminal by doing Ctrl+Alt+t

---

### Post by mirroalex on 2010-10-13
> **Hippytaff said:**
> Not sure where the icon is...still on 10.04 and its on the panel, but you can get the info from the terminal

```

acpi

```You can open a terminal by doing Ctrl+Alt+t


Thanks i will give it a try, about 10.04, yes battery indicator was ok but in 10.10 NETBOOK there is not any battery indicator even i looked at the ubuntu page where there are examples of features of 10.10 netbook and in the pictures there is not such thing as battery indicator !

P.S ubuntu 10.10 DESKTOP is ok also problem is netbook edition! may be u don't have to know your battery state in netbook edition! :(:confused:

---

### Post by maharaja2 on 2010-10-13
I don't have that indicator too, but it shows up when i unplug my power cable.

---

### Post by mirroalex on 2010-10-14
> **maharaja2 said:**
> I don't have that indicator too, but it shows up when i unplug my power cable.

Yeah that is the solution, plug and unplug ac power seems to fix that, now i have battery indicator!

THANKS.

---

### Post by JohnTheLutheran on 2010-10-17
This one was baffling me, too. But when the indicator is there, right-click it, choose "Preferences", go to the "General" tab and then select "Always display an icon" to have the indicator visible at all times (useful with my netbook's very low-capacity battery...).

---

### Post by mirroalex on 2010-10-20
> **JohnTheLutheran said:**
> This one was baffling me, too. But when the indicator is there, right-click it, choose "Preferences", go to the "General" tab and then select "Always display an icon" to have the indicator visible at all times (useful with my netbook's very low-capacity battery...).

Thanks Bro.

---

### Post by DanaLou on 2010-10-21
> **JohnTheLutheran said:**
> This one was baffling me, too. But when the indicator is there, right-click it, choose "Preferences", go to the "General" tab and then select "Always display an icon" to have the indicator visible at all times (useful with my netbook's very low-capacity battery...).

LOL I see the icon; it appears for about .5 seconds after I re-plug my ac adapter in .. not long enough to right-click though :)

EDIT: haha, waited for about 5 seconds, then the icon stayed on and made the adjustment in the general tab. Thanks JohnTheLutheran :D :D

---

### Post by severusd on 2010-10-26
I just got Maverick this week running on a Acer Aspire One ZA3 and am enjoying it greatly, but really missing the battery indicator.

The fix is great but does not persist for me across reboots.

It's pretty impractical to have to connect to the mains every session.

My feeling is that there is a bug but since this is both my first netbook and my first experience of Ubuntu I am ready to stand corrected.

---

### Post by Hippytaff on 2010-10-26
> **severusd said:**
> I just got Maverick this week running on a Acer Aspire One ZA3 and am enjoying it greatly, but really missing the battery indicator.

The fix is great but does not persist for me across reboots.

It's pretty impractical to have to connect to the mains every session.

My feeling is that there is a bug but since this is both my first netbook and my first experience of Ubuntu I am ready to stand corrected.

If you think it's a bug, which is possible, check out the bug part of the launchpad and add your experience...helps the devs

[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)

my favorite bug report [https://launchpad.net/ubuntu/+bug/1](https://launchpad.net/ubuntu/+bug/1) :-)

---

### Post by connyh on 2010-12-03
> **mirroalex said:**
> Hi everyone:KS,

I'm new to ubuntu netbook edition or in more general to ubuntu, i had ubuntu 10.04 desktop previously so it had battery indicator but today i have installed ubuntu 10.10 netbook and i can't find battery indicator or any place where i can check my battery state.

is there anyone who can bring me to light? :guitar:
To get your icon back open system->control center, go to hardware and select power management, click on general an then on always display an icon.

---

### Post by rutharanga on 2010-12-26
I have ubuntu 10.10 installed on my laptop and after update is done i've noticed that my power icon was missing.
Here are the steps I've followed.

Go to System -> Preferences -> Power Management
then go to the "General" tab.
There you can find section called "Notification Area"
Then mark your preference and click Apply.
There we go..!:D Battery icon is now visible on your Desktop Notification area.

---

