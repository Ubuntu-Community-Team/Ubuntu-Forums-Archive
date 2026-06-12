---
title: "Problem when booting ubuntu 11.04"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by Slasher The Great! on 2011-06-21
Hi all,
i have just tried to install ubuntu 11.04 on my system but after it finishes and reboots, the logon screen appears i fill in the details and it blank screens. i have been waiting for it to load since 9 am in the morning.

my previous OS was windows 7 and it worked fine 

system specs:

Shuttle-x PC sn41g-v2
ATi Radeon 3850 hd
Corsair TwinX 2GB XMS PRO

[B][B][FONT=Verdana][SIZE=1]](*,)](*,)](*,)

Any help will be gratefully appreciated
Thank You
[/SIZE][/FONT][/B][/B]

---

### Post by hobbit1983 on 2011-06-21
when you log in select Ubuntu Classic from the options at the bottom of the screen and let us know if that gets you to a desktop or not.  The problem may be in loading the unity desktop.

---

### Post by Redblade20XX on 2011-06-21
Can you press cntrl+alt+f2 on the black screen and post the response, if any?

---

### Post by dFlyer on 2011-06-21
Before you installed the OS did you run a live desktop cd to be sure your computer was compatible? Can you get to a terminal by pressing Ctl-alt f2 and run this command:

/usr/lib/nux/unity_support_test -p

all your answers have to be yes to run unity.

Did you check the md5sum of the downloaded iso?

Can you start clasic gnome from the login screen?

---

### Post by Slasher The Great! on 2011-06-21
Thanks for the quick response,
i was too confident in the output.

it lets me press Ctrl+Alt+F2 and it says:

[drm:radeon_ib_schedule] * ERROR * Radeon: Couldn't schedule IB (6)
[drm:radeon_CS_ioctl] * ERROR* Failed to schedule IB
Radeon: Gpu lockup cp stall for more than 10016 msec

---

### Post by Slasher The Great! on 2011-06-21
and to add to that, the logon screen doesnt come up any more? #-o
I've downloaded the ati drivers for if that helps.:D

I have to go to bed now so...
night night speak to you in the morning

---

### Post by Slasher The Great! on 2011-06-22
hi,
is there anyway of installing the drivers whilst the os is installing?
thanks

---

### Post by dFlyer on 2011-06-22
As far as I know, it can only be installed during install if it's on the install ubuntu cd. Are you able to start the classic gnome desktop?

---

