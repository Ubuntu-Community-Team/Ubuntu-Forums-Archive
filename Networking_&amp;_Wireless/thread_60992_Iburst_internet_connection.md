---
title: "Iburst internet connection"
date: 2005-08-30
forum: Networking &amp; Wireless
---

### Post by Light-Jedi on 2005-08-30
Hey,

I am having a little trouble getting my iburst internet ocnnection to wokr on ubuntu, this is driver related once i get the 2.6 pcmcia drivers installed for my modem i should be able ot connect via a ppoe dialer.

Now i have a copy of the pcmcia iburst drivers for kernel 2.6 and i have installed both the kernel headers and kernel source for ubuntu via apt-get. But now when i go to make the driver i get the following error.

make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/lj/Desktop/iburst-1.2.1.tar.gz_FILES/iburst-1.2.1 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [default] Error 2

Now i am pretty new to linux and i have searched google and other sources with no real help so this is sort of my last resort.

thanks in advance

---

### Post by tehwa on 2005-08-30
I believe make is looking for your linux-headers, but can't find them.

On my machine, location /lib/modules/2.6.10-5-386/build is a shortcut to the linux-headers. Specifically on my machine it points to /usr/src/linux-headers-2.6.10-5-386.

If you fire up File Browser and move to /lib/modules/2.6.10-5-386/ does a shortcut to your linux-headers exist in the form of a 'build' folder with a blue arrow?

---

### Post by Light-Jedi on 2005-08-30
no there is no build folder in /lib/modules/2.6.10-5-386

so i did

root@Mew:/lib/modules/2.6.10-5-386 # ln -s /usr/src/linux-headers-2.6.10-5-386/ build


and it fixed the issue thanks alot for your help

---

### Post by PeaceMakr on 2005-09-04
Ok im impressed with your skills, but im totally new to Linux and im still learning how to find my way in the directories... can you please explain plainly HOW and WHAT must i do to get this iburst of mine going, oh WHAT do i need, do i download something ?

Thanks, i promise to trash xp when im happy with Linux : )

---

### Post by lucid on 2005-09-06
Peacemakr, as I'm very inexperienced with Linux I won't presume to give you advice as to how you might be able to fix your problem, but I can offer my experience with getting an iburst modem working:

I tried the Linux drivers for my Kyocera iburst Acess bridge modem and immediately copped error messages. Lacking the skills to nut those errors out I tried something else. The modem was connected as USB (ethernet was specificly not recommended in the modem guide), so I reconnected it through ethernet, and followed the instructions provided in the Unofficial Ubuntu Starter Guide. Worked a treat. 

By the by, thanks for the Starter Guide! It was perfect for giving me the hard and fast way to get functionality in Linux so that I could take the time to learn Linux while using it to do the stuff I normally do on a comp. This was the key difference between my abortive attempt with Fedora Core and my successful one with Ubuntu. Cheers!

---

### Post by PeaceMakr on 2005-09-06
Can someone tell me where to get a copy of this guide?

---

### Post by lucid on 2005-09-06
[QUOTE=PeaceMakr]Can someone tell me where to get a copy of this guide?[/QUOTE]

[http://www.ubuntuguide.org/]("http://www.ubuntuguide.org/")

---

