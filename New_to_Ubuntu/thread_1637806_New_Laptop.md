---
title: "New Laptop"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by stsguitar23 on 2010-12-04
Hi,
    My birthday is in a few days, and my parents bought me a Dell Inspiron 15r (New)
I'm not super smart with computers on anything, but i know it has: 

Windows 7 home premium 64 bit
4GB DDR3 Shared duel channel memory
500GB 5400rpm HDD
Intel HD+ Graphics
New 2010 Intel® Core™ i5-460M

(If anymore information is needed i might be able to get it, just ask)

(Is it a problem that Windows will come preloaded onto the computer? I mean, I imagine they would send me a disk with it.)

I've been looking at this for a while, and I thought if I'm getting a new computer, a good time to install Ubuntu would be right away.

I've looked around, and I saw that there was an option to duel boot it with windows, so I would really like to do that.
But I'm rather unclear on what the benefits of it would be (Why should I, Why shouldn't I?)

I don't think i'll need much help on the installation, because I know there are tutorials and Youtube videos out there for that.
I was planning on using this

[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)

I guess the main question I'm asking is; How does the duel boot operate after I install them both?
Is it that when I boot the laptop, it gives me a choice of which system to use? And what about my files? If I make a file in Windows, will I be able to access it in Ubuntu, and will there be compatibility problems?

I also own an Ipod (gosh, so many different brands going on here) and I hear that Ubuntu doesn't support Itunes, so I would just use Windows for that?

I'm not sure how clear I was being throughout all of that. But I'm really unsure on what I want. So any input would be helpful. Thanks.

---

### Post by tekkidd on 2010-12-04
It will load grub and tell you somthing like 

Ubuntu 10.04 2.5.46
Ubuntu 10.04 2.5.46 (Recovery)
Windows 7

Just choose windows 7 and you will boot into windows

And if you install BURG it will give you a pretty menu

If you have any more questions or need help join my blog: tekkidd.tumblr.com

---

### Post by anewguy on 2010-12-05
If I might suggest, either run off a LiveCD for a while, or perhaps install to a USB flash drive and run that for a while.

Why?  I think you need to take some time to try ubuntu first and give it while.  your parents are buying you a nice laptop, and I'd hate for that to turn into a bad situation (you did WHAT to the laptop we bought you???!!!).  Try it for a while - see if ubuntu offers anything you can't do with Windows.  I'm a supporter of ubuntu, but it's not for everyone, nor does it fit everyone's needs.  If you can do what you want without it, in particular with a new computer and a new supported OS, the only reason to really install it would be to "play" (that includes learning something new).  Until you are quite sure about everything, I wouldn't change what you've got.

just me......

Dave ;)

---

### Post by Megaptera on 2010-12-05
My Dell came with a restore partition and three restore discs. Before you make radical changes - as suggested - try Ubuntu live CD first and also make sure you know how to use whatever Dell recovery options you're given if you do go for a dual-boot.

I ditched Vista and went for Ubuntu alone on this Dell 'cos there were no Windows features I needed such as iTunes. Dual boot does give you the best of both.

Useful guide for sharing data between  Ubuntu/Windows if you go that route (different file systems) [http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

### Post by fidamehran on 2010-12-05
You have another option to go for. The Wubi install.
I will tell you what to do in a bit. But first, your options.
1. First, run Live CD (Boot from an Ubuntu live CD) and get the feel of the OS.
Please note, the OS will be considerably slow to respond than usual. Don't let the slow response time demotivate you. Observe the difference in menu orientation, software options, and other stuff, in comparison to Windows. If you like what you see, go for the next step.

2. Now, provided that you liked the looks (trust me, there is more of the looks to be seen in Ubuntu), then log on to Windows. Download Wubi ([www.wubi.com](www.wubi.com)) and the last Ubuntu ISO file from [www.ubuntu.com](www.ubuntu.com)

3. Now put the Wubi.exe and the Ubuntu ISO in the same folder. Then Right click the Wubi.exe and click "Run as Administrator".
Tell the installer which drive to install Ubuntu in (other than the drive where you have Windows {usually C:}). Also select what size you want to install in. Then hit Install.

4. Once installation is complete, PC will restart and give you Boot options. Select Ubuntu and it will continue the installation in Ubuntu. Finally, when the installation is complete, you will get into Ubuntu.

Why Wubi?
Because, it installs just like another Windows program "inside" Windows, and can be uninstalled through Control Panel --> Uninstall a Program. 

After you use it for a few days, if you like it, you can continue keeping the Wubi install, or uninstall it and install in real Dual Boot mode (as in putting in the CD from Startup and installing from beginning.)

I still use Ubuntu in Wubi. Although many Ubuntu Gurus discourage this (because it seems to them like the Ubuntu is a slave to Windows), but actually it is a very good way to use Ubuntu. Only thing is that the Windows installation has to remain intact and free from being Corrupt, if you want to continue using the Ubuntu. Coz, the Ubuntu installed through Wubi has the Boot records in Windows MBR.

Anyway, I think Windows 7 is pretty much stable compared to previous Windows versions. So, it should be safe to try Ubuntu and not worry about it.

---

### Post by philinux on 2010-12-05
Here's what I did with my new Acer 1410. 

In windows I shrank the partition as much as I could. There is a limit as some files cannot be moved. I got about half free.

I then installed ubuntu to this free space using the manual partitioning, taking the advanced step at the end to install grub to that partition and not the MBR.

Back in windows I downloaded and installed easybcd and configured it to boot the ubuntu partition.

This way if I have a warranty issue there will be no hassle.

---

### Post by Mark Phelps on 2010-12-05
Dell's typically come with the disk already segmented into 4 primary partitions, and since that is the limit you can have, there is no simple way to add another partition for Ubuntu.  This will require you to REMOVE an existing partition -- not a good idea and a risky thing to do.

If you open a terminal using the Ubuntu LiveCD, and enter "sudo fdisk -lu" (that's a lowercase L, not a one), and post the results here, we can see how your drive is partitioned.

Can't really provide any detailed advice until we have that information.

However, BEFORE you do anything else, run the Win7 Backup feature, select the option to create a Repair CD, create and burn a Win7 Repair CD.  You are likely to need that later should problems develop with the Win7  boot loader during dual-boot setup.

And finally, MS has come a long way since the Vista days, and a lot of the bad press you have heard about Vista poor performance and lack of features has been largely fixed in Win7.  So, unless you have some compelling reason to switch over from Win7, it would really be best to follow the advice others have already given -- use Ubuntu in LiveCD mode for a while before you attempt any kind of installation.

---

### Post by TBABill on 2010-12-05
> **Mark Phelps said:**
> there is no simple way to add another partition for Ubuntu.  This will require you to REMOVE an existing partition -- not a good idea and a risky thing to do.

Not true. I have a Dell Inspiron 1564, very similar to the 15r the OP will be getting. I simply "install side by side" and do nothing further to keep my Win7 partitions in tact and use Linux. I still boot into both when necessary. I have kept my Win7 partition in tact and installed both my sda6 Linux partition and a separate swap partition, and I have done so with about 15 different Linux installs to that same configuration in the last 6 months.

To the OP, if you choose to install Ubuntu, just make sure you know what you want your partitions to look like and be positive you are not installing onto any Windows partition.

---

