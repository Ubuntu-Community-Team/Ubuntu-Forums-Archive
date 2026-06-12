---
title: "i'm new..and I have a strange thing with ubuntu 9.04"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by uki12 on 2009-05-10
Hey there...

Okay so..i install ubuntu....(i hope i install it corectly...i use a ext3 format) and..i get some packages, i update it....and then...i have 2 problems:
1. When it runs..i cant use compiz and the ATI control centre, thught, the driver is "installed" form add/remove programs:)...the odd thing is..that i had ubuntu 8.10 and..then it worked...i erased ubuntu after i almost messed up bad my entire hdd:)(it sux being a newby at sth)
2. after first reboot it doesn't start anymore...its little strange....the screen shows me...in the middle 2 ubuntu loading pictures...and in the lower part of the screed its..like..static...like..you know..the old color tv's..when you didn't get signal...its sht like taht:))...very very strange...the thing is...before first reboot it works just fine!

PS: I have an F-S Amilo D1845 notebook with a P4@2.8Ghz, 512MB RAM, and an Mobility Radeon 9700 series..its a pretty good notebook...it cna handle ubuntu..it even handles the "all new" Windows 7 beta:))

---

### Post by anewguy on 2009-05-10
When you get the goofy screen on reboot, try holding down ctrl-alt and pressing F1.  This should get you to a logon screen - just enter your normal userid and password.  You should now be at a command prompt.

If the above works, then the driver for your video card needs to be updated.  Post back the output of the following:

cat /etc/X11/xorg.conf

lspci


It's possible you may be able to get this to work with Envyng, though I haven't had luck with an older Radeon card.  From the command line, try to install envyng:

sudo apt-get install envyng

If it does install, then try this:

envyng -t

Follow the prompts, being sure to ask it to remove the existing driver and then try to add a new driver.  If that fails, report back here with the failure.

Dave :)

---

### Post by uki12 on 2009-05-12
> **anewguy said:**
> When you get the goofy screen on reboot, try holding down ctrl-alt and pressing F1.  This should get you to a logon screen - just enter your normal userid and password.  You should now be at a command prompt.

If the above works, then the driver for your video card needs to be updated.  Post back the output of the following:

cat /etc/X11/xorg.conf

lspci


It's possible you may be able to get this to work with Envyng, though I haven't had luck with an older Radeon card.  From the command line, try to install envyng:

sudo apt-get install envyng

If it does install, then try this:

envyng -t

Follow the prompts, being sure to ask it to remove the existing driver and then try to add a new driver.  If that fails, report back here with the failure.

Dave :)



hey there:)

well the problem is not fixed..yet...i reinstalled linux...and i put the envyng driver...i still had no acess to ati control centre..and..not after first, but after SECOND!(imporvemet) reboot it had faulty screen..>.<....and that combination..it didn't work.....i don't like this...i think i'll go ahead and install ubuntu 8.10 :)..i think it will work better>:)

cya!

---

