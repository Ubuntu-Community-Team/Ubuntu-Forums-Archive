---
title: "Problems installing Ubuntu Studio"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by suddentwigs on 2010-02-26
**Problems installing Ubuntu Studio** 
[FONT=Times New Roman][SIZE=3]Hi there. I have recently completed my first build. All hardware seems to be functioning correctly but I am having some issues with operating system installation. I first tried 64studio; however its installer will not recognise my DVD drive as it is SATA. I connected an old IDE drive in an attempt to work around this, but it is so old that it will not play DVD-Rs, and for some reason 64studio needs to be booted from a DVD-R. I next tried Ubuntu Studio 9.10. This installed fine, but when I booted the OS for the first time, it ran through Memtest, and when it completed this it simply restarted the test. When invited to press Escape I did so, which rebooted the system back into memtest. It is worth noting at this point that regular Ubuntu 9.10 also doesn’t run, but that doesn’t concern me. I then tried Ubuntu Studio 9.04, which installed fine, but froze during first boot. Regular Ubuntu 9.04 runs absolutely fine, so I tried upgrading to Studio using the package installer within the operating system. It sorted the appearance, but it won’t download Ardour, which I would like to use. It comes up on the list in the software centre, but it won’t let me check the box and doesn’t explain why. Can anyone help? I’m quite frustrated as I have designed this machine especially for audio work and as yet have had no success. My hardware specs are as follows:[/SIZE][/FONT]

[SIZE=3][FONT=Times New Roman][COLOR=black]Gigabyte GA-H55M-USB3 Motherboard Core i7 Socket 1156 Intel H55 Micro ATX RAID Gigabit Ethernet LAN[/COLOR][/FONT][/SIZE]
[COLOR=black][SIZE=3][FONT=Times New Roman]intel Core i3 530 2.93GHz Socket 1156 4MB L3 Retail Box Processor[/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]G.SKill RipJaw 4GB (2x2GB) DDR3 PC3-12800 1600MHz CL8 Dual Chann[/FONT][/SIZE][/COLOR]
[COLOR=black][COLOR=black][FONT=Times New Roman][SIZE=3]Samsung SH-S223L Internal SATA DVD-SM Drive With Lightscribe[/SIZE][/FONT][/COLOR][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]Samsung HD103SJ SpinPoint F3 1TB 7200RPM SATA II 3GB/s 32MB Cach[/FONT][/SIZE][/COLOR]

[COLOR=black][FONT=Times New Roman][SIZE=3]Help! Thanks.[/SIZE][/FONT][/COLOR]

---

### Post by dvlchd3 on 2010-02-26
Try updating via command-line.  I've run into that problem when running 9.04 where packages wouldn't allow me to check them in the Update Manager, however, if I did it via command-line, everything upgraded fine.

```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by suddentwigs on 2010-02-26
Hi there. I have recently completed my first build. All hardware seems to be functioning correctly but I am having some issues with operating system installation. I first tried 64studio; however its installer will not recognise my DVD drive as it is SATA. I connected an old IDE drive in an attempt to work around this, but it is so old that it will not play DVD-Rs, and for some reason 64studio needs to be booted from a DVD-R. I next tried Ubuntu Studio 9.10. This installed fine, but when I booted the OS for the first time, it ran through Memtest, and when it completed this it simply restarted the test. When invited to press Escape I did so, which rebooted the system back into memtest. It is worth noting at this point that regular Ubuntu 9.10 also doesn’t run, but that doesn’t concern me. I then tried Ubuntu Studio 9.04, which installed fine, but froze during first boot. Regular Ubuntu 9.04 runs absolutely fine, so I tried upgrading to Studio using the package installer within the operating system. It sorted the appearance, but it won’t download Ardour, which I would like to use. It comes up on the list in the software centre, but it won’t let me check the box and doesn’t explain why. Can anyone help? I’m quite frustrated as I have designed this machine especially for audio work and as yet have had no success. My hardware specs are as follows:

[SIZE=3][FONT=Times New Roman][COLOR=black]Gigabyte GA-H55M-USB3 Motherboard Core i7 Socket 1156 Intel H55 Micro ATX RAID Gigabit Ethernet LAN[/COLOR][/FONT][/SIZE]
[COLOR=black][SIZE=3][FONT=Times New Roman]intel Core i3 530 2.93GHz Socket 1156 4MB L3 Retail Box Processor[/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]G.SKill RipJaw 4GB (2x2GB) DDR3 PC3-12800 1600MHz CL8 Dual Chann[/FONT][/SIZE][/COLOR]
[COLOR=black][COLOR=black][FONT=Times New Roman][SIZE=3]Samsung SH-S223L Internal SATA DVD-SM Drive With Lightscribe[/SIZE][/FONT][/COLOR][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]Samsung HD103SJ SpinPoint F3 1TB 7200RPM SATA II 3GB/s 32MB Cach[/FONT][/SIZE][/COLOR]

[COLOR=black][FONT=Times New Roman][SIZE=3]Help! Thanks.[/SIZE][/FONT][/COLOR]

---

### Post by switch10 on 2010-02-26
That is very odd that 9.04 works and 9.10 does not.  Did you check the MD5 sum after downloading?  It may have gotten corrupted.  Also when burning ISO images, burning at the lowest possible speed always reduces errors for me.  

open a terminal and do:
```
 sudo apt-get install ardour 
``` 

to install ardour.  

You will run into some audio latency problems running the generic kernel with the regular Ubuntu install.  The studio versions run a Real Time kernel.  It works great, no latency issues at all.  

I would try to re-download, and re-burn, and then re-install ubuntu studio for best results.  Try the 8.04 version maybe.  Thats what I use, and I love it.

On a side note, Ardour is really a great program.  I have never used pro tools, but I've been using Ardour for years now, and I can't imagine anything better.  I'm in 2 different bands, and we use Ardour for all of our recording.

Good Luck :)

---

### Post by gallifrey on 2010-02-26
I would also check that you have the repo containing ardour checked in your software sources. i often forget to do this on a new install.

---

### Post by suddentwigs on 2010-02-26
Thanks for your suggestions! I look forward to trying them out. The problem with 9.10 is that it installs correctly, but once the desktop displays, it immediately freezes if I move the mouse, and will not respond to anything except pushing the reset button. The lights on the keyboard go out too. I haven't been burning slowly or checking the disc integrity or anything, I always thought if a disc was dodgy it just wouldn't install. Now I know better.

---

### Post by frodon on 2010-02-26
Threads merged.

Only one thread per support request please.

---

### Post by paleoJunky on 2010-03-18
I just built a GA-H55M-USB3 with core i3 530 using Ubuntu 9.10 x64. I had issues with the system locking up and applications lagging. After searching around I found that upgrading the kernel to 2.6.33 will help and also there is evidence that Gnome is at fault. So try the kernel upgrade and installing kubuntu-desktop and selecting KDE session when you log in. The newer kernel stopped the freezing and KDE stopped the application lagging. Sorry I don't have the links, I was frantically trying things to solve the problem. Just google around and you can find the "how to" for each.

---

