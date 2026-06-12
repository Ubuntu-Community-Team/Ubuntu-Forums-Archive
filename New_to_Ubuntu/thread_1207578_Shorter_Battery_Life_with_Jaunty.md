---
title: "Shorter Battery Life with Jaunty"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by danzber on 2009-07-08
Hello All,

I apologize if this has already been addressed.  I have a Lenovo Y530 laptop with the NVidia GeForce 9300M graphics card.  I have both Windows Vista (64 bit) and Ubuntu 9.04 (Jaunty, also 64 bit)) installed on it.  I have found that when I use Vista (with the default balanced power management setting), I get almost twice the battery life as I do with Jaunty.

Is this normal?  I am using the default power settings in Ubuntu (screen is dimmed while on battery, etc.).  Are there configuration steps I can take to improve Jaunty's power performance?

I really appreciate any help!

---

### Post by bear24rw on 2009-07-08
i have also noticed this on my laptop, even disabling stuff with powertop doesnt help much..

---

### Post by ivanvajar on 2009-07-08
Look for CPU frequency scaling and HDD spindown settings on this forum or via Google.

---

### Post by binbash on 2009-07-08
Enable laptop-mode and play with its configuration files.

---

### Post by XCan on 2009-07-08
I think this is actually quite normal. Although people have reported longer battery time in Linux vs Windows, I believe the average user without doing some ninja tweaks will get worse battery life.

---

### Post by zo3adams on 2009-07-08
Found the same results with default Ubuntu install. Especially with compiz running with full effects vs. none.

The laptop mode mentioned up-thread is discussed in more depth here:
[http://www.totalnetsolutions.net/2007/08/13/how-to-increase-battery-life-in-ubuntu-or-debian-linux/](http://www.totalnetsolutions.net/2007/08/13/how-to-increase-battery-life-in-ubuntu-or-debian-linux/)

I found mounting with "noatime" and the screen brightness to be the most beneficial settings.

---

### Post by danzber on 2009-07-09
Thanks for the suggestions everybody.  I've tried them (at least to the best of my limited Linux skills/knowledge), and haven't seen much better battery performance (maybe a few minutes).  I think I agree with XCan; an average user (maybe below average?) like me will get worse battery life.  That's fine; I mostly use my laptop at home anyway.  I was just curious, mainly.

---

### Post by pointyblue on 2009-07-10
I'm on a netbook with Ubuntu 9.04 and experience the same problem. (It used to run XP.)

In my mind this is a major handicap. As well as decrease the usability of the computer it's also pretty stupid in these times of increased CO2 awareness.

A guide on how to optimize for better power management would be really helpful.

---

### Post by unutbu on 2009-07-10
Although you have a different laptop, you may be able to find some useful tips and tricks here: [sdennie's HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773&highlight=USB+writes")

---

### Post by LewRockwell on 2009-07-10
[http://www.lesswatts.org/projects/index.php](http://www.lesswatts.org/projects/index.php)

.

---

### Post by rush_ad on 2009-08-06
I am experiencing the same problem with 9.04. Battery life in Windows is double in my case. I am going back to Windows for the time being.

Windows 7 it is then...

---

