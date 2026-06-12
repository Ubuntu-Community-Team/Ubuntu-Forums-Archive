---
title: "Duel BOOT, XP/UBUNTU 64"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by 9000cse on 2011-02-20
Hi, I'm new here.  I have a silly question regarding UBUNTU 64
I have just installed it onto one of my systems,  Great, love it.  Now the question.
I have what I call the main system. and that runs XP sp3.  I want to be able to duel boot this, for the time being.
Reason, there are some programs that I cannot run under UBUNTU, or Linex for that matter.
Is there a way of doing this?  UBUNTU, would have a drive to itself, 160Gig.
So, can I do this?

Cheers
Andy  :guitar:  :lolflag:    Sorry, just liked these two  :P

---

### Post by davidmohammed on 2011-02-20
welcome to the forums,

yes - the option you want is to "install side by side" - see [here]("http://www.ubuntu.com/desktop/get-ubuntu/download") (section 4 step 4).  Then on step 5 just choose the drive you want ubuntu to install onto.

---

### Post by 9000cse on 2011-02-20
> **davidmohammed said:**
> welcome to the forums,

yes - the option you want is to "install side by side" - see [here]("http://www.ubuntu.com/desktop/get-ubuntu/download") (section 4 step 4).  Then on step 5 just choose the drive you want ubuntu to install onto.

Thanks, I'll give it a go.

Andy

---

### Post by oldfred on 2011-02-20
You do have to pay attention to which drive you are installing into. And if you want a choice on which drive has grub's boot loader, you have to use manual install.

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

---

### Post by 9000cse on 2011-02-20
Hi Oldferd.
Thanks for this info.
So I really need to split the 160 gig drive into 3 - 20 gig, /Primary - 2 gig, /Swap -  the remainder /Home  Or split the remainder into 2 for /Home  &  /Data
I have 4 gig of ram BTW,  Three disks, 2 SATA 300 & 500 + this IDE 160 that I'll put Ubuntu on.

On booting, the system. do I get a menu to say boot to:- XP or UBUNTU sort of thing?

I may have to do my sons system again?
Cheers Guys. And thanks for your input.

---

### Post by oldfred on 2011-02-20
Yes, if you set the IDE drive as the boot drive then grub will load a menu of systems to boot. 

Some systems have issues on drive order with mixed IDE & SATA drives. SATA drive boot order is set by software/BIOS. IDE drives always were set with jumpers or location on the 80 conductor cable select cable. Originally only primary master was the boot drive. So how its works, you may have to experiment.

---

### Post by 9000cse on 2011-02-20
OK, I see where your coming from on the boot sequence.  I'll have a play.  Have not set any thing up as yet. Getting pointers before I wipe the system down by mistake.

Tell me, how would you split 160 gig drive up?

Cheers
Andy

---

### Post by oldfred on 2011-02-20
If you are just starting out with Ubuntu, I would suggest 20 to 25Gb for root, 2GB for swap unless you want to hibernate then equal to RAM+a fraction. The rest I would make /home. 

I had a standard dual boot XP install with just root, swap and soon created a shared NTFS partition for Firefox & Thunderbird profiles, so whichever system I booted I had the same links & email. Now I have a larger drive, converted to /data so I could share Linux data and multiple root partitions. I prefer to do clean installs of Ubuntu, but keep old one for backup/reference. Then I added another for the beta of the next to test, and then maybe one or two more..... it just keeps growing. I left extra unallocated as I was not even sure what wanted with new drive. With only 20 or 25GB per system partition it is easy to go overboard.

---

### Post by 9000cse on 2011-02-21
Hi All, OK, I think I can close this thread now. Thanks to the help I have received here from you guys. 
Everything works a dream. OK, so I have to hit F11 to boot from the drive that holds UBUNTU, but what the heck, 2 seconds longer to get to the desktop. Well I suppose I could die in that time, so does it matter.  I have installed most of what I need. there are one or to other bits of SW that I will look into.  
Now to cut XP down to size, get some sapec back for UBUNTU.
Once again, thanks to all for your help.
Andy, well pleased.  "Can I get rFactor to work under UBUNTU????" :popcorn::popcorn::popcorn:

> **davidmohammed said:**
> welcome to the forums,

yes - the option you want is to "install side by side" - see [here]("http://www.ubuntu.com/desktop/get-ubuntu/download") (section 4 step 4).  Then on step 5 just choose the drive you want ubuntu to install onto.

---

### Post by oldfred on 2011-02-21
Ubuntu should give you a choice to boot windows. If not:

sudo update-grub

Then in BIOS set the Ubuntu drive as the first to boot.

Games are not as well supported in Linux. If they do not have a linux version, it might run in wine. Most gamers dual boot.

---

### Post by 9000cse on 2011-02-21
> **oldfred said:**
> Ubuntu should give you a choice to boot windows. If not:

sudo update-grub

Then in BIOS set the Ubuntu drive as the first to boot.

Games are not as well supported in Linux. If they do not have a linux version, it might run in wine. Most gamers dual boot.


BIOS will not let me have the IDE drv first boot. SATA over rides it.
Hitting F11 brings up a menu for you to choose which drv to boot from. Then sudo update-grub comes up with a nice menu, not in colour mind :D  Then I take it from there.

I'll give wine a go in the morning, I'll let you know.  But don't hold you breath waiting :D:D
Thanks again.
Andy

---

### Post by 12apennachi on 2011-02-21
"Duel Boot" 
I think you should let the partitions joust and that might just take care of it. Haha jk

---

### Post by Dutch70 on 2011-02-21
> **12apennachi said:**
> "Duel Boot" 
I think you should let the partitions joust and that might just take care of it. Haha jk

:lolflag:

---

