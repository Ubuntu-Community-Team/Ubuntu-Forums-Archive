---
title: "Slow or no response when I try to open programs"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by omaralqady on 2008-12-12
Hi, I just started using Ubuntu a week ago and I have a problem when I try to open some programs (i.e. Synaptic Package Manager), I click on its shortcut in the System-->Administration Menu and then on the panel at the bottom of the screen a small bar appears that says "Starting Admini......" and after a while the program sometimes starts and sometimes nothing happens at all. I'd appreciate any help with this problem :D

---

### Post by sneeks on 2008-12-12
what are your system specs please mate,and might be able to shed some light on it..

---

### Post by omaralqady on 2008-12-12
I have an Acer Aspire 3050 laptop with the following specs:

Kernel:Linux 3omar 2.6.24-22-generic i686 GNU/Linux
-I also have Windows XP on another partition just in case

Processor: AMobile MD Sempron 3500+ 1.8 GHz

RAM: 1 GB

VGA: ATI Radeon Express 1100 (integrated and set to 64 MB)

And this is the info about my partitions:
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7             22018772   4227772  16672476  21% /
varrun                  484464       112    484352   1% /var/run
varlock                 484464         0    484464   0% /var/lock
udev                    484464        56    484408   1% /dev
devshm                  484464        80    484384   1% /dev/shm
lrm                     484464     39788    444676   9% /lib/modules/2.6.24-22-generic/volatile
/dev/sda1             10231392   9338232    893160  92% /media/$Y$T3M
/dev/sda6             23539744  16221680   7318064  69% /media/F!L3$

Is this enough or do you need anything else??
And thanks for your reply :)

---

### Post by NullHead on 2008-12-12
Does it still do that if you log out and back in again?

---

### Post by omaralqady on 2008-12-12
I haven't tried logging off and on but I tried restarting (probably the same effect) and it does go away when I do that, but not for good, it still happens sometimes and every time it does I need to reboot.

---

### Post by omaralqady on 2008-12-13
Is this the only solution to restart whenever it happens or is there something could do to prevent this from happening??

---

### Post by oldos2er on 2008-12-13
Type "gksu synaptic" in a terminal, and if there is any output, please post it here.

---

### Post by omaralqady on 2008-12-13
There was no output it just opened the Synaptic Package Manager. But I was only using the package manager as an example, this also happens when I try to open system programs such as software sources, hardware drivers, ...
But it's not constant, sometimes all goes well, other times nothing happens. So it might be something with the system programs, I'm not sure just a guess :)

---

### Post by omaralqady on 2008-12-14
I tried gksu synaptic once again today after I had tried to open the package manager and software sources and neither opened. when I typed it in a terminal there was no output although for a little while it acted like it was going to start it and the little tab appeared on the panel and the cursor turned into the busy symbol and then nothing happened, the cursor returned to normal, the tab disappeared, no output on the terminal, but it didn't show another prompt, just a blank line. What does this mean, if anything, and what should I do??

---

### Post by Kellemora on 2008-12-14
Hi Oma

I don't know what's causing it, I have weird things happen too.
Like I click on something to open it, it appears in the panel for a second or two, then disappears and it never opens.

Rather than reboot, If I just hit CTRL-ALT Backspace key, this restarts the X-window and everything works fine then.
It still takes time, but is quick compared to rebooting.

Knock on simulated woodgrain, haven't had to do that in quite a while now.

But I thought you might like to know about the CTRL-ALT Backspace way of doing it since it is faster than rebooting.

TTUL
Gary

---

### Post by omaralqady on 2008-12-14
Thanks Gary, I'll try that next time :D
ps. it's Omar :)

---

