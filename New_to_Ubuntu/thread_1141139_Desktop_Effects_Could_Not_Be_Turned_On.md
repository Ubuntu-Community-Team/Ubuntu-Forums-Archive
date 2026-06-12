---
title: "Desktop Effects Could Not Be Turned On?"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Frosty G on 2009-04-28
Dear Ubuntu Forums, i have a problem
when i click "normal" or "extra" in desktop effects, i get an error saying they could not be turned on
when i go to the terminal and type "compiz"
i get:
"Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity "

what do i do?
i am using a HP tablet PC Laptop
Ubuntu Inteprid

---

### Post by PriceChild on 2009-04-28
Could you tell us what video card you have? If you don't know, type the following into a terminal:
```
lspci
```and paste the output here.

---

### Post by Frosty G on 2009-04-28
"01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)"
this one
could it just be that the video card sucks?
(i know it does)

---

### Post by accooper on 2009-04-28
I doubt your card has the ability to do any effects.  It is, sorry to say,  pretty low end.  I have an ATI All-In- Wonder 9800 with 256 megs memory and it will not do all but the simplest effects.

If you really want the effects I would suggest you up date you video card if you can.

:guitar:

Andrew

---

### Post by wizard10000 on 2009-04-28
> **Frosty G said:**
> "01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)"
this one
could it just be that the video card sucks?
(i know it does)

Take a look at this thread - it might help.

[http://ubuntuforums.org/showthread.php?t=757473](http://ubuntuforums.org/showthread.php?t=757473)

Good luck -

---

### Post by Frosty G on 2009-04-28
i would love to, but have you seen one of these things?
its so small i doubt they make replacement cards, probably just stuck with that one
thanks anyway guys

---

### Post by Frosty G on 2009-04-28
> **wizard10000 said:**
> Take a look at this thread - it might help.

[http://ubuntuforums.org/showthread.php?t=757473](http://ubuntuforums.org/showthread.php?t=757473)

Good luck -
this looks awesome mate, thanks

---

### Post by Frosty G on 2009-04-29
i ran the [compiz test]("http://forlong.blogage.de/entries/pages/Compiz-Check")
and this is what it said
Gathering information about your system...

 ```
Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
 Driver in use:         nv
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: nv driver in use 

Would you like to know more? (Y/n) Would you like to know more? (Y/n) Y

 The nv driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 
```

i just ran
```
 sudo apt-get install nvidia-glx-96
```
and it installed, but doesnt seem to have done anything
when i go system>administration>hardware drivers
i get an empty box with the message "No Proprietary Drivers are in Use on this System"
my video card is a
```
VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
```

what should i do?

---

### Post by skymera on 2009-04-29
I use Envy for all my restricted drivers

```
 sudo apt-get install envyng-gtk 
```

It'll appear under Applications > System Tools

---

### Post by Frosty G on 2009-04-29
ill try that thanks

---

### Post by kpkeerthi on 2009-04-29
The safest thing to do is to activate the driver from System -> Admin -> Hardware drivers. Ubuntu will install the right driver for.

---

### Post by kpkeerthi on 2009-04-29
And then enable desktop effects from System -> Preferrences -> Appearance -> Visual Effects.

---

### Post by Frosty G on 2009-04-29
> **kpkeerthi said:**
> The safest thing to do is to activate the driver from System -> Admin -> Hardware drivers. Ubuntu will install the right driver for.
when i do that its blank on both fields and says there arnt any drivers,
and gives no options

---

### Post by Frosty G on 2009-04-29
> **skymera said:**
> I use Envy for all my restricted drivers

```
 sudo apt-get install envyng-gtk 
```It'll appear under Applications > System Tools
it finished installing, but hasnt appeared there
do i need to restart?

---

### Post by kpkeerthi on 2009-04-29
> **Frosty G said:**
> when i do that its blank on both fields and says there arnt any drivers,
and gives no options

Well, then envy is the option I guess.

---

### Post by Kosimo on 2009-04-29
Why don't you give a try to install latest nVidia Linux drivers manually? It just takes a couple of steps.

Have a look in my sign

---

### Post by overdrank on 2009-04-29
Please do not create multiple threads on the same issue. Threads merged

---

### Post by Frosty G on 2009-04-29
sorry about that^

> **Frosty G said:**
> it finished installing, but hasnt appeared there
do i need to restart?
what do i do about this?

---

