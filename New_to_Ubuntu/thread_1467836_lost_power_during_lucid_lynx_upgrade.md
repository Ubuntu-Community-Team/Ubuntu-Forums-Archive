---
title: "lost power during lucid lynx upgrade"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by princeofnam on 2010-05-01
While leaving my laptop to install the upgrades, I hadn't noticed how the power cord had slipped loose.  When I came back my computer must have shut off due to battery loss.  When I booted up my computer again, I couldn't boot up Ubuntu under any of the kernels, -20,-19, etc.  I get cryptic messages such as "unable to enumerate USB device on port 2," device not accepting messages," and "device descriptor read."  does anyone have any suggestions for what i should do? i definitely intend to recover my data.
 
I had been upgrading from 9.10 to the latest version of lucid lynx.

---

### Post by madjr on 2010-05-01
oh that sucks :(

this is why we recommend using the live-cd from scratch upgrades or [alternate cds]("http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD") and to backup before doing so.

the best thing you an do is burn one so you an recover


also if you can get to the command line, you could probably continue the upgrade

---

### Post by princeofnam on 2010-05-01
i can get to a "repair broken packages" option under recovery mode. would that help any?

---

### Post by princeofnam on 2010-05-01
xxx

---

### Post by The Fiddler on 2010-05-01
Don't worry, a similar thing happened to me and it's usually salvageable.

If you can get to a root terminal try using:

sudo apt-get install -f

to resume the installation and

sudo apt-get dist-upgrade

once install -f is complete.

If you get errors about broken dependencies, try installing the problematic packages with:

sudo aptitude install [package name]

and then resume the installation using the above commands.

I'm typing from a system salvaged with this method, right now, so it does work!

---

