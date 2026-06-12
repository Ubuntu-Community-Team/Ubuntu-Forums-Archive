---
title: "Hardware Drivers box is empty in Jaunty"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by susanne260 on 2009-05-12
If I boot off the Intrepid Live-CD, I can easily install the graphics drivers via the "Hardware Drivers" box. Everything works great.

But when booting off the Jaunty Live-CD, the "Hardware Drivers" box is empty. Why is that? :confused:


I'm using Ati Radeon X1900XTX and Viewsonic P227F CRT monitor. Both the resolution and the refresh rate are off. It doesn't go any higher than 75Hz.

---

### Post by jespdj on 2009-05-12
You can't install hardware drivers when booted off the live CD. You'll have to install Ubuntu on your harddisk for that.

I've noticed that sometimes, when running Ubuntu for the first time after installation, the Hardware Drivers list is empty. You just have to wait some time, or run the Update Manager once, and reboot, and then the drivers will become visible.

---

### Post by swoody on 2009-05-12
Like jespdj said, I haven't seen any drivers in "Hardware Drivers" on a LiveCD before. Mine always appear after installation, and sometimes only after running updates. It all depends on the driver, the version of Ubuntu you're installing, and your specific hardware, but chances are if the driver was available under Intrepid, it's available under Jaunty. Are you looking to install Jaunty on your harddrive, or are you just planning on running the LiveCD?

---

### Post by Elfy on 2009-05-12
I have got the hardware drivers to report an nvidia, you need to change your software sources to allow proprietary software at least.

---

### Post by susanne260 on 2009-05-12
[QUOTE=jespdj]You can't install hardware drivers when booted off the live CD. You'll have to install Ubuntu on your harddisk for that.[/QUOTE]

That's strange. I can install the hardware drivers when booted off the LiveCD in Intrepid, so I assumed it would also work in Jaunty without installing it on the disk.

[QUOTE=jespdj]I've noticed that sometimes, when running Ubuntu for the first time after installation, the Hardware Drivers list is empty. You just have to wait some time, or run the Update Manager once, and reboot, and then the drivers will become visible.[/QUOTE]

I just installed Jaunty on the harddrive, next to Intrepid. But the Hardware Drivers box is still empty. Even after running the Update Manager, installing all the updates and then rebooting a few times.

Then I tried this: "apt-get install xorg-driver-fglrx" and rebooted again. But now it just locks up the whole system in Jaunty when the login screen comes up. Even hitting Ctrl+Alt+F1 nor Ctrl+Alt+Del doesn't do anything. :\

---

### Post by skymera on 2009-05-12
Your X1900 is unsupported by FGLRX.
You need to use the opensource driver.

---

### Post by susanne260 on 2009-05-12
> **skymera said:**
> Your X1900 is unsupported by FGLRX.
You need to use the opensource driver.

Do you mean it's just not supported yet? It will be supported in the near future, no?

I can't use the opensource driver, because then I'd have go through the xorg.conf-editing-hell again. :\

---

### Post by skymera on 2009-05-12
No it's no longer supported by AMD.

Even on Windows they've been dropped.

As far as i know in Xorg.conf the driver line should read "ati".
This selects the opensource driver for you.

---

### Post by susanne260 on 2009-05-12
> **skymera said:**
> As far as i know in Xorg.conf the driver line should read "ati".
This selects the opensource driver for you.

Tried it, but unfortunately it didn't change anything. I still can't change the refresh rate any higher than 75Hz.

Jaunty looks like a great release! It's much faster, snappier and looks more polished. =)

Too bad the xorg.conf-editing-hell is what stops me from using it. I guess I have to continue using Intrepid until I get a new monitor someday. A refresh rate of 75Hz would kill my eyes. :(

Thanks to everyone who tried to help, though! =)

---

### Post by anewguy on 2009-05-12
I also have a Radeon card - mine is a 9250 - and had the same trouble when I tried flgrx.  I just went back to the default xorg.conf that only says default video device in the device section.  Everything has been working fine - compiz, etc. - so I posted Monday night asking about a driver.  Turns out in my case I was being stupid -> I looked at the xorg log file in /var and it shows it loading the open source Radeon driver.  I think this all has something to do with the changes they made whereby they are trying to make things more automatic and get away from xorg.conf.  I think you could still specify clock ranges there for the monitor though using the vertical and horizontal rates.

Dave :)

---

### Post by AmrH on 2010-01-18
You may have recently changed your software downloads server under "Software Sources." If that's the case, revert back to the original server and tell us what happens.

---

### Post by Nerd King on 2010-01-18
One common cause of these problems is crap mirrors. The one for Thailand is rubbish for instance and is usually missing files. Because of that, off the live cd the drivers show, but once installed they don't. I have to change to the US servers for them to show. It could be that with the 2 different versions you're on different mirrors and one's crappy. In that case, swap to America.

---

