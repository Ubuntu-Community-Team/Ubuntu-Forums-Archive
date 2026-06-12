---
title: "Ubuntu 9.10 &amp; NETGEAR WNDA3100"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by alpha123 on 2010-01-29
Hello everyone,

I am using Windows 7 64-bit and I just installed Ubuntu 9.10 using Wubi. Looks pretty nice, kinda reminds me of Mac OS not-X. Anyway, I am using the NETGEAR RangeMax WNDA3100 wireless card. I installed it from the installation autorun program, in case that makes any difference. Works fine with Windows 7. So, how do I get it to work in Ubuntu 9.10? Ubuntu currently has absolutely no internet connection. I looked at [http://ubuntuforums.org/showthread.php?t=885520](http://ubuntuforums.org/showthread.php?t=885520), and I don't have a file called WNDA31.sys. Also, I couldn't find D:\bin\config\ndis5\ on the disk (yes, my CD drive is D:). So could someone either please give me instructions for getting it to work (remember, Ubuntu has absolutely no internet connection), or attach the files needed.

Thanks,
alpha123

---

### Post by alpha123 on 2010-01-29
Um, a little help please?!

Thanks.

alpha123

---

### Post by tripolitan on 2010-01-29
The instructions in the thread you quoted, call for the .inf file. In any case, the .sys file for your particular adapter may not be exactly named as the one used. Personally, I would use whatever is on the driver CD for your usb wifi adapter for win xp (yes I know you're using win 7).

Of course, this is all assuming that you've installed the 64 bit version of Ubuntu (if that's even relevant with Wubi). And that you've installed ndiswrapper, kernel headers and all that stuff, per the instructions.

---

### Post by tripolitan on 2010-01-29
Unless you have something to add, please don't reply to your own posts.

---

### Post by alpha123 on 2010-01-29
It didn't ask for 32-bit or 64-bit with Wubi, so I assume that it just automatically detected it.

> In any case, the .sys file for your particular adapter may not be exactly named as the one used. Excuse me for being a little naive, but how am I supposed to find it then?!

Does [FONT=monospace]**sudo apt-get install ndiswrapper-common ndiswrapperutils-1.9 **[/FONT]and [FONT=monospace]**sudo apt-get install ndisgtk **[/FONT]require an internet connection? Because I can't connect to the internet from Ubuntu....

Thanks for the help,
alpha123

> Unless you have something to add, please don't reply to your own posts.

Very sorry about that.

---

### Post by tripolitan on 2010-01-29
No worries.

Yes, all apt-get commands require internet connection to "get" the packages "programs" ndiswrapper-common  and ndiswrapperutils-1.9 and ndisgtk from the software repository. Of course, you will have to install these packages from the CD, since you can't get on the internet. You might already have the kernel headers installed by default. ndiswrapper will tell you, if it can't find them.

---

### Post by alpha123 on 2010-01-29
Well, this could be tricky. I have a computer running Windows 7 (I'm using it right now) that I just installed Ubuntu 9.10 on. All the other computers in the house have Windows Vista (well, one ancient one has XP, but it's too slow to do anything). I installed Ubuntu by downloading and running Wubi, so there is no CD. Could I download the packages with Windows and use a USB stick to move them to the Ubuntu part of my computer?

Thank you,
alpha123

---

