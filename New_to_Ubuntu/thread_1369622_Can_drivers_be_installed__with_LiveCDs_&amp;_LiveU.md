---
title: "Can drivers be installed  with LiveCDs &amp; LiveUSBs?"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by neu5eeCh on 2010-01-01
Since I'm getting no satisfaction with my [last query]("http://ubuntuforums.org/showthread.php?t=1368713"), thought I'd ask the question with a little more clarity...

With two of my last three laptops, I've been unable to install drivers (wireless) while in live-mode.  Once Ubuntu was properly installed (on the HDD), however, the drivers installed flawlessly.

So... is the inability to install drivers in live mode standard behavior?

---

### Post by spiderbatdad on 2010-01-01
If you are talking about a live cd, then the answer is yes. The live cd is read only. It is possible to create other bootable devices and install additional software to the operating system. If you want to run strictly a live environment, you might consider knoppix instead.

Also this is still relevant: [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence) Though I wouldn't reccomend trying karmic's usb creator.

---

### Post by neu5eeCh on 2010-01-01
Thanks Spider. [COLOR=Silver]That hasn't been my experience with either LiveCD or LiveUSB, but I'll take your word for it.[/COLOR]

I'm not trying to run in a "strictly live environment". I've been trying to persuade my wife to kill windows on her netbook, but it's hard to demonstrate the superiority of Ubuntu (and Linux in general) when I can't get her wireless to work. That's why I'm asking if this only an issue in "Live Mode".

**Edit:** Just noticed that I misread Spider's comment. He was saying that I **can't** install drivers in live mode, which confirms my experience.

---

### Post by spiderbatdad on 2010-01-01
please tell us what netbook and what version of Ubuntu.

I could be wrong. I haven't spent much time running a live cd. Certainly you can edit files and the like, but I don't understand where you would be installing any programs unless you had storage or a partition prepared to which you could write.

---

### Post by neu5eeCh on 2010-01-01
HP Mini 1030NR.

As mentioned in my last post, another user has apparently [created a dual boot system]("http://www.youtube.com/watch?v=Dt_bLfyb7jE") on this tiny computer (all on a 16G solid state drive!), so I have no doubt that Ubuntu will work on her Netbook once I persuade her to switch.

Anyway, I tried with two different versions of Ubuntu 9.10 - both standard and Netbook remix.

I was about to try with Puppy, just to see....

---

### Post by spiderbatdad on 2010-01-01
ok sorry, I looked at your previous thread. How about trying to install the broadcom driver from the live cd. Check your software sources to be sure cd rom is checked then start synaptic package manager. Look for bcmwl-kernel-source, or something...just type bcm into the search window. Sorry I haven't had much experience with this driver...luckily!

---

### Post by neu5eeCh on 2010-01-01
Thanks again, Spider.

The problem isn't with finding or downloading the driver (which Ubuntu seems able to do) the problem is that "Live Mode" seems unable to "activate" it, or (to use its own terminology) put the wireless hardware **in use**.

I'm beginning to think that this is a Live Mode limitation.

It would seem to me that the Ubuntu "*powers that be*" ought to either remedy this or give users like myself some indication that this is a "Live Mode" limitation. I'm OK with the latter solution - at least newcomers won't think there's something wrong with Linux itself...

---

### Post by spiderbatdad on 2010-01-01
If you created a bootable usb with 2G and used the extra space for storage, I would venture you could use this driver. You can create the bootable usb using usb-creator, even from a live cd, but not Karmic's since it is broken. But if you had a copy of Jaunty, for example, or Hardy, You can boot the cd, plug-in the usb, and run usb-creator. This assumes you have an image stored on a working system. You select source by browsing, then highlight it. Then select usb as target...set extra space for persistence. I realize it's a little work, but it creates a bootable/installation usb device with some storage. Also if the image is on a working ext4 system there might be problems browsing the filesystem...not sure. A lot of issues exist since all the recent changes. I get around this by using an external drive to store the image I want to write to usb, and boot from an 8.04, or 8.10 live cd for usb-creator.

---

### Post by Ferretti on 2010-01-01
My sister has the same wireless card in her Mini 1030NR. To fix it, I went to System > Administration > Software Sources then checked the box that said "CDROM with Ubuntu 9.10 (Karmic Koala). Then I opened Synaptic Package Manager and searched for "bcmwl-kernel-source" and installed it. After a reboot, everything works perfectly. Hopefully this will work for you too. Best of luck!

---

### Post by spiderbatdad on 2010-01-01
> **Ferretti said:**
> My sister has the same wireless card in her Mini 1030NR. To fix it, I went to System > Administration > Software Sources then checked the box that said "CDROM with Ubuntu 9.10 (Karmic Koala). Then I opened Synaptic Package Manager and searched for "bcmwl-kernel-source" and installed it. After a reboot, everything works perfectly. Hopefully this will work for you too. Best of luck!

It would be great if you actually read the thread before posting.

---

### Post by Ferretti on 2010-01-01
I apologize. I had two tabs open. One was for the solution I just said to you. I typed it in the wrong thread. I'm sorry.

---

### Post by ST3ALTHPSYCH0 on 2010-01-01
Just a thought (and maybe not a good one). Why not use an 8 Gb usb stick as a target HDD for a full install? Then you get the ability to install everything you need, and the only change to the windows partition would be the addition of GRUB, which is fairly easy to replace with the windows boot loader if you decide that Ubuntu is a no-go.

---

### Post by spiderbatdad on 2010-01-01
Of course the best option is to write to HP and complain about their use of the broadcom network card. Tell them in future you will be sure to avoid any netbooks employing hardware that requires proprietary drivers. I would try to return it ;) in favor of an acer aspire one.
In fact I just submitted a message here, expressing my own disappointment in HP's choice of hardware requiring non-free drivers. [http://www.hp.com/hpinfo/execteam/email/hurd/index.html](http://www.hp.com/hpinfo/execteam/email/hurd/index.html)

---

### Post by neu5eeCh on 2010-01-01
> **spiderbatdad said:**
> If you created a bootable usb with 2G and used the extra space for storage, I would venture you could use this driver. You can create the bootable usb using usb-creator, even from a live cd, but not Karmic's since it is broken. 

Ah... so the problem is with Karmic? Interesting. In fact, I **did** use a 2G Flash Drive to create extra storage, but perhaps the issue with Koala is the reason it didn't work? If I can't get my wife to install Ubuntu without demonstrating that it actually *works, *I might go your route and download 8.04 or 8.10 for a live cd USB-Creator.

I may have to do this while she's not looking. None of this you, you know, inspires confidence... I feel like a used car salesman who can't start the damned car! Feh!

And, yes, HP t's me off. Their drivers don't even work in Windows for f's sake. Oh well. says HP, we're not making new drivers for ***that***. That's ancient. It's already 2 months old! But we have a new scanner/printer/whatever you might be interested in...

I'll write them... for all the good it will do...

---

### Post by neu5eeCh on 2010-01-01
> **ST3ALTHPSYCH0 said:**
> Just a thought (and maybe not a good one). Why not use an 8 Gb usb stick as a target HDD for a full install? Then you get the ability to install everything you need, and the only change to the windows partition would be the addition of GRUB, which is fairly easy to replace with the windows boot loader if you decide that Ubuntu is a no-go.

That's an idea I actually considered, but my fear is that Ubuntu would be noticeably slower running off a USB port. My wife needs to know that her little Netbook is going to hum like a sports car (compared to MS) once Linux is installed.

---

### Post by ST3ALTHPSYCH0 on 2010-01-01
I can tell you from experience that a Live environment is always going to be slower than a fully installed environment. W/ a transfer rate of up to 480 Mb/sec (as long as it's USB 2.0) I don't think you'll see a humongous difference. Another thought is a WUBI install, If you don't want it later you just remove it through "add/remove programs" in Windows

---

### Post by candtalan on 2010-01-01
> **ST3ALTHPSYCH0 said:**
> Another thought is a WUBI install, If you don't want it later you just remove it through "add/remove programs" in Windows
yes  this is a good idea. It is a very safe method of install with no messing with partitions or the like, and it uses the Windows boot manager. So it is really inside windows. It can be un installed in an instant too. 
A small caveat - after uninstall, I believe the windows boot loader retains the Ubuntu item, so a small windows file edit is required then to revert to a vanilla Windows startup screen.
hth

---

### Post by ST3ALTHPSYCH0 on 2010-01-01
Also, I'm not sure about 9.10 (although it should be similar), 9.04 installed in 2.7 Gb (I had it on a 4 Gb partition), so you can tell WUBI to make the folder only 4 Gb, and you can download your wireless driver in windows and leave it in a folder, then navigate to said folder from within Ubuntu (this applies to any install method) so you don't actually have to have internet access immediately after install.

---

### Post by neu5eeCh on 2010-01-01
> **ST3ALTHPSYCH0 said:**
> Another thought is a WUBI install, If you don't want it later you just remove it through "add/remove programs" in Windows

That's a great idea. However, during my research on her Netbook, I noticed that one can upgrade the hard drive with a 64GB RunCore Pro PATA Mini Zif Solid State Drive SSD, and I could upgrade the memory to 2 GB (though memory is expensive right now). Hell, if I put in a 64GB drive, she could dual boot and decide on her own.

I also found out why the HP mini  is *soooo* slow. Turns out it's Microsoft's fault. Here's here [one blogger]("http://www.notebooks.com/2008/12/12/hp-mini-1000-how-to-upgrade-ram-in-less-than-20-seconds-video/") summed it up:

* Microsoft introduces Vista. Everyone still keeps using XP.
* Netbooks become popular. They aren't powerful enough to run Vista.
* XP reaches its official end of life, and Microsoft wants to discontinue it. Netbook users complain they won't have an OS.
* Microsoft decides to allow XP to continue selling for a bit.
* Microsoft discontinues XP, but allows netbook manufacturers to continue licensing it, to force everyone else to buy Vista but allow netbook users to use a Microsoft OS.
* Microsoft decides to define a netbook as a machine that has 1GB of RAM or below.

In a nutshell, Microsoft forced HP to limit their configurations to 1G. The sooner I can eliminate Microsoft from my life, the better.

Thanks for everyone's help and suggestions.

---

