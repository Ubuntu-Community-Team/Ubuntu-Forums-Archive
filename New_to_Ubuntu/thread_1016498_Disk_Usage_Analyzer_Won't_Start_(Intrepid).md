---
title: "Disk Usage Analyzer Won't Start (Intrepid)"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by nowhere@cox.net on 2008-12-20
My disk usage analyzer won't start any more. This message is in several of the logs

```
Dec 19 20:13:09 legolas kernel: [ 332.025818] baobab[6711]: segfault at 1 ip 00007fb81a7c5110 sp 00007fff27cf2468 error 4 in libglib-2.0.so.0.1800.2[7fb81a75c000+c3000]
```

I booted in the older kernel 2.6.27.9 instead of 2.6.27.11 and it still won't start so I don't know if it's related to the kernel update or not.

Any ideas? I reinstalled both the packages named in the error to no avail also.

Thanks!

---

### Post by rcgeary71 on 2008-12-22
Me too.

kernel: [  903.540365] baobab[6825]: segfault at 1 ip 00007f8d05b7b110 sp 00007fff130a7838 error 4 in libglib-2.0.so.0.1800.2[7f8d05b12000+c3000]

Appears to have been reported already:

[https://bugs.launchpad.net/ubuntu/+source/baobab/+bug/309894](https://bugs.launchpad.net/ubuntu/+source/baobab/+bug/309894)

---

### Post by Gunbullet on 2008-12-29
Hm same situation here, when I try to launch the Disk Usage Analyzer nothing happens after I click on the application through the menu. Thought I had done something wrong since I'm new in the world of Ubuntu (translated = fiddling around with a big smile on my face :)) anyone seen or heard anything more about this problem?

---

### Post by nowhere@cox.net on 2008-12-29
Yes, actually I reported it. There hasn't been any activity on it yet tho. Been a while...

---

### Post by ArcaneMagus on 2008-12-29
If it helps at all in the debugging of this issue mine only started doing this after I changed what drives it was supposed to scan to only be a secondary drive.

---

### Post by ArcaneMagus on 2008-12-29
Just tried deleting ~/.gconf/apps/baobab but it didn't fix the issue. Will keep investigating.

---

### Post by Gunbullet on 2009-01-02
Interesting, after making a clean new installation of Ubuntu the Disk Usage Analyser seems to be up and running on my system (8.10 Intrepid). I wonder what the problem was or if it will return?

---

### Post by pdowling on 2009-01-03
I just started having this problem yesterday.  I was able to get it started from a command promt with...

gksudo baobab

Appears to work, but still don't know why it won't start any other way.

---

### Post by nowhere@cox.net on 2009-01-09
I'll try it but if it works it's pretty obvious. The tool never used to require root privileges to run...

I'll let you know later this evening.

---

### Post by Gunbullet on 2009-01-12
How did it go with the test?

---

### Post by nowhere@cox.net on 2009-01-14
I would still not start, even with the gksu. Same errors in the log.

---

### Post by nowhere@cox.net on 2009-01-22
Bump... Also, maybe reinstalling it would work? Can anyone give me a clue how to install it? If I try to uninstall it, like the whole Ubuntu install would go with it...

---

### Post by nowhere@cox.net on 2009-02-02
Without any solution, I'll have to resort to a re-install of Intrepid. I use this tool very often to help clean the huge number and sizes of media files I deal with and the time spent manually surfing each directory to try to find the big folders is taking too much time.

---

### Post by artnis on 2009-02-04
> **rcgeary71 said:**
> Me too.

kernel: [  903.540365] baobab[6825]: segfault at 1 ip 00007f8d05b7b110 sp 00007fff130a7838 error 4 in libglib-2.0.so.0.1800.2[7f8d05b12000+c3000]

Appears to have been reported already:

[https://bugs.launchpad.net/ubuntu/+source/baobab/+bug/309894](https://bugs.launchpad.net/ubuntu/+source/baobab/+bug/309894)

I started having this problem yesterday (Intrepid) after I reset in the preferences menu the devices to include in the file scan to my external hard disk only.

I fixed the problem today by doing the following:
In the terminal I opened the app using the command  gksudo baobab.
When the Disk Usage Analyzer opened I then placed a check mark on all devices shown in edit>preferences to include them in the file scan and closed the application.

I then went to the "edit menus" for editing the panel(s) menu (right click any panel) and selected the Disk Usage Analyzer under Accessories.
Once this was selected there is a button on the right to show Properties.
Click this button and there is a place to enter a Command. In this area I typed gksudo baobab and closed the window. It now works the way it did before when I selected it from the Applications>Accessories menu.

---

### Post by nowhere@cox.net on 2009-02-10
Thanks artnis. Interestingly, I had tried gksu baobab from the terminal with no luck. Tonight I tried gksudo baobab from the alt-f2 dialog and it will start up. Only problem is that it's running as root so the home button scans the root home folder...

At least I can clean up my data drive now tho. Any ideas why it has to be root all of the sudden?

Thanks!

---

