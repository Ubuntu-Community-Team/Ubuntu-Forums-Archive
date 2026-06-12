---
title: "Stalled Ubuntu install, now Windows wont boot"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by misterman73 on 2010-12-11
Hi all,

I screwed up big. I think Ubuntu is really cool, and I jumped right into the installation last night off a live CD. Now, I'm not computer illiterate, I know how to do a few things, but I'm no Linux pro. The installation went late into the night and I did something stupid. I had the installation running in a one workspace off the live CD (which is really cool, btw) and was browsing mozilla in another. Then, I went back to check on the installation and it was stuck on "RF Change in progress!" and saying something about a sleep something or other. I got frustrated and put the computer into suspend. 

Stupid, right? So, I immediately turned it back on. Ubuntu wont turn back on, so i turn the computer off completely and try Windows 7, which  will also no longer boot. I have to use the Ubuntu live CD to even get on my computer. When I went into restart the installation, it showed two Ubuntus, one I presume the one I had failed to install completely and the Ubuntu I was about to install. There was no mention of another type.

HELP.

Are all my files gone? Is windows gone?

Bonus information:

I'm using a gateway all in one.
I wouldnt know what a partition was if it bit me, which it very well could have given this situation,
I want to leave windows in the dust.

---

### Post by Mariane on 2010-12-11
Your files are probably still there somewhere. When you boot from the Ubuntu CD try looking for them. 

Also, what exactly happens when you boot up without the CD? Do you see the grub menu? (A list of boot-up choices)

Mariane

---

### Post by Rubi1200 on 2010-12-11
Hi and welcome to the forums :)

First things first, do NOT attempt to install/reinstall/change/delete anything.

Instead, from the LiveCD run the boot info script linked at the bottom of my post (instructions included).

Post the results back here so we have a clear overview of your setup and can advise you on the best move.

Thanks.

---

### Post by Tricity on 2010-12-11
> **misterman73 said:**
> 
Bonus information:

I'm using a gateway all in one.
I wouldnt know what a partition was if it bit me, which it very well could have given this situation,


This tidbit about the partition is crucial. A partition is a limited space on a hard disk, much like a room in a house. Unfortunately, most computers that come pre-installed with Windoze use up the entire hard disk with one single partition (more like a house with one single huge room, rather than having three separate rooms for, say, Linux, another OS, and your data).

If you want to install Ubuntu side-by-side with another O/S on the same hard disk, you need to have at least two partitions on your hard disk. There are probably tons of posts out there that tell you how to shrink the C: partition and then add an empty partition for Ubuntu.

BUT HEED RUBI1200's ADVICE - you can only be successful if you get to the previous working state. Working on a half-clobbered disk can make things worse. In fact, let me suggest that you boot from the LiveDVD and FIRST OF ALL rescue all your important data onto an external drive. THEN try to restore Win7.

---

### Post by Trandre on 2010-12-11
This helped me in with the same problem:


> **sikander3786 said:**
> You need to reboot and see what happens. Based on your issue, either Problem # 1 or Problem # 2 from this guide would apply and there are solutions listed as well ;-)

courtesy of forum member Rubi1200

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If you don't feel confident, feel free to post back here or in that thread, whichever you prefer.

After the problem is Solved, I would suggest to apply the *Permanent Fix* from that page in order to avoid the update problems in future.

Good Luck!

---

### Post by misterman73 on 2010-12-11
> **Rubi1200 said:**
> Hi and welcome to the forums :)

First things first, do NOT attempt to install/reinstall/change/delete anything.

Instead, from the LiveCD run the boot info script linked at the bottom of my post (instructions included).

Post the results back here so we have a clear overview of your setup and can advise you on the best move.

Thanks.

A friend of mine who claimed to know Linux came over and told me to just restart the install. This was before I saw any of these replies. I want to kill him, but I have more important things to attend to. Upon reading this, he immediately pulled the plug on my computer. Literally. I dunno if this was the right thing to do or not, but hey, live and learn. I am currently rebooting ubuntu off the live CD, and will do the boot script thingy and post the results in a few.

Honestly, I will destroy him. :mad:

---

### Post by misterman73 on 2010-12-11
> **Mariane said:**
> Your files are probably still there somewhere. When you boot from the Ubuntu CD try looking for them. 

Also, what exactly happens when you boot up without the CD? Do you see the grub menu? (A list of boot-up choices)

Mariane

When i boot up without the CD nothing happens. It shows the gateway welcome screen and then nothing. Black screen.

---

### Post by misterman73 on 2010-12-11
> **Rubi1200 said:**
> Hi and welcome to the forums :)

First things first, do NOT attempt to install/reinstall/change/delete anything.

Instead, from the LiveCD run the boot info script linked at the bottom of my post (instructions included).

Post the results back here so we have a clear overview of your setup and can advise you on the best move.

Thanks.

Another problem: Firefox wont load any pages, or it loads them so slow I only get text.

I'm screwed.

---

### Post by TCHebb on 2010-12-11
It sounds like you're trying to boot off the half-installed Ubuntu instead of the LiveCD. Try restarting and booting to the CD. Make sure that you don't boot from the hard drive until you can run the boot info script and get replies here. If the GRUB menu comes up, just press the power button to turn off the computer, make sure the boot order is set correctly in the BIOS and try to boot off the CD again.

---

### Post by misterman73 on 2010-12-11
Well, after hours of messing with it, I managed to get some of my mission critical files off the hard drive, some corrupted, some not. Eh. I've decided to wipe the harddrive and install Ubuntu again on a clean slate off a USB. And boy, does it take forever.

Dont worry, however, about my Linux woes being over. I'll be back.:popcorn:

---

