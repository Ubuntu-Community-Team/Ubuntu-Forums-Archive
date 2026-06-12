---
title: "batteries"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by kiraku on 2009-12-21
hi:

after update to 9.10, my battery doesnt last more that 20 minutes... before is use to last at least 1 hour...

i have a compaq presario c700, with 1 Gb RAM, 120 Gb HD, and Intel Pentium dual core processor of 1.46 Ghz each...

so, what could it be????

---

### Post by kiraku on 2009-12-22
so, nobody have an idea?

---

### Post by 3rdalbum on 2009-12-22
Is there a program that's hammering your CPU? Have you checked in "top" or "System Monitor" to see?

Have you tried installing and running the Powertop program?

One hour is a rather short amount of time to get from your battery - maybe it's on its last legs.

---

### Post by lotharmat on 2009-12-22
Left click on the battery icon in the notification area at the top of the screen then click on the battery in the context menu that pops up.

There is a 'capacity' field in the dialog box that pops up that tells you your batteries capacity and overall health.

hth.

---

### Post by LowSky on 2009-12-22
sounds like the battery is on it last legs. it should last more than an hour wen fully charge, hopefully more than 2-3 hours.

---

### Post by kiraku on 2009-12-22
> **3rdalbum said:**
> Is there a program that's hammering your CPU? Have you checked in "top" or "System Monitor" to see?

Have you tried installing and running the Powertop program?

One hour is a rather short amount of time to get from your battery - maybe it's on its last legs.

i let my pc works on batteries doing "nothing", almost 0% cpu, and still last only 20 minutes...

i'll try powertop and comment later...

the batterie has always last like an hour...

---

### Post by frogotronic on 2009-12-22
> **kiraku said:**
> hi:

after update to 9.10, my battery doesnt last more that 20 minutes... before is use to last at least 1 hour...

i have a compaq presario c700, with 1 Gb RAM, 120 Gb HD, and Intel Pentium dual core processor of 1.46 Ghz each...

so, what could it be????

Hello,

  It could be a mis-configured application, or something (process) that's hanging.

_Two things to try:_

1)  If this is an Intel motherboard, you can find out by installing "[powertop]("http://www.lesswatts.org/projects/powertop/")".

```
sudo apt-get install powertop
```

Then reboot and run it by 

```
sudo powertop
```

Check what's running/eating up your CPU.


2) Do you have "laptop-mode-tools" package installed?

```
sudo apt-get install laptop-mode-tools
```

Also, you have to enable it, by

```
sudo gedit /etc/default/acpi-support
```

change 

```
# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines.  (Note: This is reported to cause breakage in
# Debian - see deb bug #425800.  Leaving enabled for Ubuntu for now
# since presumably it's still valid here.)
ENABLE_LAPTOP_MODE=false
```

to 

```
# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines.  (Note: This is reported to cause breakage in
# Debian - see deb bug #425800.  Leaving enabled for Ubuntu for now
# since presumably it's still valid here.)
ENABLE_LAPTOP_MODE=true

```

Then, reboot - see if that helps spin down your HDD and save battery.


- CH


P.S.  Also check Powemanager and play with those settings.

P.P.S  Or, if your battery is more than two years old, it could just be dying.

---

### Post by kiraku on 2009-12-22
> **LowSky said:**
> sounds like the battery is on it last legs. it should last more than an hour wen fully charge, hopefully more than 2-3 hours.


my notebook has like 2 years... on that time, that was that batteries last, at least here...

i have another recently acquired and his batteries last like 3 hours...

---

### Post by kiraku on 2009-12-22
cement_head:

it seems that your 2nd suggestion solved the problem... effectively, the parameter was setted to false, so i changed it to true and now the battery seems to be uncharging at normal rate...

also, i checked powertop and it doesnt seems to be any process that eat battery above normal...

so, thanxz for all, you really helped me...

and thanxz to all of you that help...

cya

---

### Post by underquark on 2009-12-22
Is your wifi constantly on?  Bluetooth? GPS recevier? Anything else likely to draw power?

---

### Post by kiraku on 2009-12-22
> **kiraku said:**
> cement_head:

it seems that your 2nd suggestion solved the problem... effectively, the parameter was setted to false, so i changed it to true and now the battery seems to be uncharging at normal rate...

also, i checked powertop and it doesnt seems to be any process that eat battery above normal...

so, thanxz for all, you really helped me...

and thanxz to all of you that help...

cya


quote to my self...

is lasted a bit more that before, but only 35 minutes...

the odd thing is that the uncharging rate is normal like to 75%, and then suddenly drop out to 5%...

---

### Post by kiraku on 2009-12-22
> **underquark said:**
> Is your wifi constantly on?  Bluetooth? GPS recevier? Anything else likely to draw power?

yes, my wifi is always on because im using it...

however, the thing are (i think) just like before the update to 9.10, it was after that the problem started...

besides, powertop doesnt show bigger problems...

---

### Post by Marvin666 on 2009-12-22
Do you have power management features enabled? If you need more run time you might wanna use the features more aggressively. The last laptop I had lasted 45 mins without any power management, and a few hours with aggressive settings.

---

### Post by kiraku on 2009-12-22
> **Marvin666 said:**
> Do you have power management features enabled? If you need more run time you might wanna use the features more aggressively. The last laptop I had lasted 45 mins without any power management, and a few hours with aggressive settings.


how do i enable them? and what you mean by aggresives??

---

