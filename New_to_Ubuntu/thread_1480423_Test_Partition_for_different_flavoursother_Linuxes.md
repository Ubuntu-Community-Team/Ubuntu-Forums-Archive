---
title: "Test Partition for different flavours/other Linuxes"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by Blutkoete on 2010-05-11
Hello!

First I was wondering whether "Linuxes" is a correct plural, but that's not the point.

I was trying some live CDs of other Ubuntu flavours and other Linux distributions, but to really test them, I want to install them, using a third partition for that.

My question is: What happens to GRUB in that case?

There's WIN7 and my standard Ubuntu 10.04, but if I install e.g. Lubuntu or Fedora on a third partition, will that new installation install a new GRUB that'll overwrite the Ubuntu 10.04 GRUB? And if I remove that third operating system again, will my computer be able to boot?

Thank you very much,

Blutkoete

---

### Post by oldfred on 2010-05-11
Computers only boot from the MBR of the primary master hard drive. So you have to manage what distribution you want to be in charge of booting. Most installs will give you a choice of where to install the boot loader or not install it at all. If the distribution uses old grub I would install it to the test install's partition - PBR and chainboot. (windows entries are chainloaded so it is actually common to chainboot). Even then Ubuntu's grub2 osprober will probably find the install and set it up with a sudo update-grub command. But we also do get posts where it has not quite set up some distributions correctly and have to make fixes. Chainbooting would be the quickest fix if that is available. Grub2 does not like to be in a PBR - something about blocklists not being reliable. But it can also be installed to a partition.

Grub2 with chainboot examples
[http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0)

---

### Post by spydeyrch on 2010-05-11
So, there are two options in my mind's eye:

1.) Use a VM for the "test system". This won't mess with your GRUB at all and in the end you could get rid of it if you want to and not mess up your already existing OSs. If you have questions, just ask. :)

2.) This method is a little more complicated and requires that you have at least two HDDs. If you would like details let me know. I didn't want to post them and then find out that you don't have a second HDD, it would have been a waste of time because it is kind of a lengthy description. :P

-Spydey :guitar:

---

### Post by Blutkoete on 2010-05-11
Thank you two!

I'm making a data backup now and then I'll just try it out. Sadly my only second HD is an external non-bootable one. I used VMs on my Macbook once, but I want to test the distributions for speed & hardware compatibility (and a VirtualBox emulating sound won't tell me whether the sound is better or worse with the distribution).

So I'll just do it the experimental way.

What makes me wonder is how I'll be able to distinguish the distributions in the boot menu ... if it just says "Linux Kernel 2.6.3xxxxx" a lot of times I won't be exactly able to tell which is what. But there is surely a way to hardcode more helpful names into GRUB later.

---

### Post by Arla on 2010-05-11
> **Blutkoete said:**
> What makes me wonder is how I'll be able to distinguish the distributions in the boot menu ... if it just says "Linux Kernel 2.6.3xxxxx" a lot of times I won't be exactly able to tell which is what. But there is surely a way to hardcode more helpful names into GRUB later.

At least in Grub2 it seems to "figure out" that there are multiples and notes which partition they are on.

I have 10.04 on two partitions (one is "stock" waiting for maverick, the other is my regular user) both have the same kernel right now, and it shows one as on SDA6, the other as being on SDA9.

---

### Post by spydeyrch on 2010-05-11
> **Blutkoete said:**
> 
What makes me wonder is how I'll be able to distinguish the distributions in the boot menu ... if it just says "Linux Kernel 2.6.3xxxxx" a lot of times I won't be exactly able to tell which is what. But there is surely a way to hardcode more helpful names into GRUB later.

In my menu, it shows each distro by it's name:

Mint 8
Ubuntu 10.04
Windows 7

Hopefully it will do the same for you. I didn't have to edit it to show the names.

-Spydey :guitar:

---

### Post by Blutkoete on 2010-05-11
Works like a charm :P.

And now my ridiculous large Swap partition isn't ridiculous large anymore, but there's Lubuntu installed. I think I'll keep it as a clean, fast surf & battery mode system while doing the important stuff with the standard Ubuntu.

And yes, it gives me different names and the partition in the GRUB menu, so everything is fine. Maybe I'll look through the GRUB documentation how to change the names to something nicer just because.

So thank you very much.

Next thing to do is to report a bug to the Lubuntu guys (if you don't install GRUB at first, it fetches it when you upgrade the system and tries install itself to the MBR if you don't read the screen messages carefully and abort) and find whether it's a problem that both Buntus use the same swap.

---

### Post by spydeyrch on 2010-05-11
@ Blutkoete - 

I like your sig. Interesting to think about. :popcorn:

-Spydey :guitar:

---

### Post by oldfred on 2010-05-11
Only if you hibernate would using the same swap cause problems, since swap and hibernation would be in the same place.

More grub2 info:
General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
drs305's hack to get hidden timeout to work:
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)

Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
OR:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu. Or you can copy it to 09_custom and make it executable and it will be at the top of your menu.

---

### Post by Blutkoete on 2010-05-11
Thanks.

My menu now gives me boot options like "Lubuntu 10.04" and "Ubuntu, 2.6.xx.x" which is much nicer than the long versions before :). Next step: Find out while he doesn't show the background picture, but that should be a breeze with all that documentation.

@spydeyrch: That sig came to my mind when my flatmate held a Ubuntu-and-SUDO-are-so-great speech some time ago when I was still using Windows XP only.

---

