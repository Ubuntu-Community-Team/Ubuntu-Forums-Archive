---
title: "Add more swap space"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by bhavya juneja on 2010-08-15
Hello,
   I installed ubuntu 10.04 on my system on dual boot with windows 7 using manual partition in which i made my swap space to 1.5gb whereas my ram is 4 gb. But now when i sleep my system with lots of programs running on, I find problems when I start it again, it gets kind of very slow.
   Also, initially I was having no sound so I upgraded my alsa to 1.0.23 and it worked but sound also stops working after i sleep.
   I don't know what the problems are but I think the former one can be resolved by adding more swap space but I don't know how to do that too, and I don't have any idea about the latter one.
Can anyone please help?
Thanks in advance.

---

### Post by Azrael3000 on 2010-08-15
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Be sure to select your swap partition and also swapoff (right click -> Swapoff) before doing anything.

---

### Post by Paqman on 2010-08-15
> **bhavya juneja said:**
> But now when i sleep my system with lots of programs running on, I find problems when I start it again, it gets kind of very slow.


Do you suspend the system, or do you hibernate? Swap is only used in the latter, when the contents of memory are copied into your swap space. Adding more swap will not help with suspend.

You also mention that you've got ALSA problems. What version of Ubuntu are you running, and how did you upgrade ALSA? The default sound system in Ubuntu is Pulse Audio these days, and the most recent version of ALSA available in the Ubuntu repos is 1.0.22

---

### Post by bhavya juneja on 2010-08-15
> Do you suspend the system, or do you hibernate?
   I am really sorry i mentioned sleep, yes that happens when I hibernate the system. So should I add more swap space and how should I do it by repartitioning or creating a file and using it as swap space?

> You also mention that you've got ALSA problems. What version of Ubuntu are you running, and how did you upgrade ALSA? The default sound system in Ubuntu is Pulse Audio these days, and the most recent version of ALSA available in the Ubuntu repos is 1.0.22
   I am running ubuntu 10.04. I found an article to upgrade ALSA to 1.0.23. This is the link
04/[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/")

Also I found that sound not only stops working when i suspend, it stops working sometimes even after my screen gets locked and when i reboot, it starts working again.
Thanks in advance.

---

### Post by Paqman on 2010-08-15
> **bhavya juneja said:**
> I am really sorry i mentioned sleep, yes that happens when I hibernate the system. So should I add more swap space and how should I do it by repartitioning or creating a file and using it as swap space?


To hibernate effectively you'll need to make the swap partition at least as big as the RAM. During hibernation the contents of RAM are written to the swap partition, so that it's preserved after the system powers down. You will probably need to use Gparted from your LiveCD to expand your swap partition.


> 
   I am running ubuntu 10.04. I found an article to upgrade ALSA to 1.0.23. This is the link
04/[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/")

Also I found that sound not only stops working when i suspend, it stops working sometimes even after my screen gets locked and when i reboot, it starts working again.
Thanks in advance.

Was there some reason you suspected the problem was ALSA? What hardware do you have?

---

### Post by bhavya juneja on 2010-08-15
> You will probably need to use Gparted from your LiveCD to expand your swap partition.
   Actually I installed ubuntu from my pen drive. Can I also repartition from Gparted available in Ubuntu Software Centre? And will it effect any loss of data or programs installed?

> Was there some reason you suspected the problem was ALSA? What hardware do you have?

I have an intel HDA ALC 269 sound card and a sony vaio eb 16 system. I actually found a thread in which they had the same problem and he did the same.
[http://ohioloco.ubuntuforums.org/showthread.php?t=1543758]("http://ohioloco.ubuntuforums.org/showthread.php?t=1543758")

---

### Post by CharlesA on 2010-08-15
You'd need to boot off a livecd/liveusb and run gparted from it (or just download a gparted livecd) since I don't think you can work with mounted partitions (and if you could, you shouldn't)

***Always*** backup any data on the drive before you resize or work with partitions.

---

### Post by HermanAB on 2010-08-15
Howdy,

You could use a swap file.  Read 'man swapon'.

---

### Post by Paqman on 2010-08-15
> **bhavya juneja said:**
> Actually I installed ubuntu from my pen drive.

That's fine, just boot up into the pen drive and run Gparted from there.

The reason you'll want to be running the system from a USB stick or a CD is that you cannot alter any partitions that are in use. So if you boot from the hard drive you can't change all the partitions on it. Even when running from the USB stick, you'll still need to disable your swap partition (right click in Gparted and "swapoff") as the live system mounts any swap partitions it finds automatically, to improve performance.

---

### Post by bhavya juneja on 2010-08-23
Sorry for the late reply, but thank you all and I finally increased my swap space equal to RAM, well I had a bit of problem in that as when I rebooted my swap space was not on and so I edited fstab file and finally it is solved now.
   About the sound problem I found an article on ubuntu help centre which explained exactly the problem I had and I have done that hoping sound never goes again.

But thank you all.

---

