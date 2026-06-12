---
title: "Installation stuck at 5%"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by HazzaJ on 2009-04-20
Hi everyone

I'm new to ubuntu and so far am liking its simplicity. However I am having a few issues trying to install it. (I have only been able to boot it directly from a disc.)

So... I am trying to install 8.10 (and yes a realize there is an update on the way) from a CD. I'm trying to install it on my laptop and override or get rid of windows as my OS and use ubuntu as my main and only OS. My laptop specs are as follows: 1.4ghz processor, 1024mb ram and a 40gig HDD. 

Anyways I am able to go through all the installation processes as normal. At step 4 out of 7 i select the automatic/guided option and am able to continue. When i finally hit the install button it starts to install and gets stuck at 5% which is: *Creating ext3 file system for / in partition #1 of SCSI1 (0,0,0)...*. It stayed like this for ages. 

The first time it happened I just restarted my comp. It originaly had 2x20gig partition and it now has 1 or 2 and windows is gone. When I try to start my comp without the disc it says: No active Partition.

I have tried to install it several times and every-time it gets stuck at 5%.  Could someone please tell me how to get around this and get ubuntu installed on my HDD? 

Hope this made sense.

Thanks,
HazzaJ

P.s. I did a search and couldn't find the answers so sorry if this has already been answered before.

---

### Post by hesjnet on 2009-04-20
Sounds like a burn that has gone wrong. I reccomend you try to burn a new copy and use a lower burn-speed.

You still have a computer to do this on right?

---

### Post by HazzaJ on 2009-04-20
Cheers for the quick reply! 

Yeh, i do have another computer to burn a new CD. And its burning as we type. 
I'll see if it works then post back.

HazzaJ

EDIT: Ok so I tried a new CD and it still gets stuck at 5%. I'm going to give it a bit longer (leave it over night) and see if its going in the morning. Hopefully my laptop won't over heat and burn the house down.

---

### Post by Sef on 2009-04-20
Instead of trying to install, go down the list to "Check disk for errors" (or something similar.)

---

### Post by Kirk M on 2009-04-20
If what Sef suggests still doesn't get the install running and since you're replacing Windows altogether, try this:

Do a live CD boot up and use the partition manager to remove all partitions on the hard drive so that the entire hard drive is unallocated space. Once that is done, try another install.

HTH

---

### Post by egalvan on 2009-04-20
> **Sef said:**
> Instead of trying to install, go down the list to "Check disk for errors" (or something similar.)

And after you finish checking the CD for errors,
check the memory for errors...
it's called "memtest86+"...

let it run at least 30 minutes...

These tests will help root out problems...

---

### Post by riza hylviu on 2009-04-20
it stopped two times with different cd at 5%, i don't think that is a burn issue.
try making it manual: delete all the partitions and create a 2gb one for the swap and the rest for the system, choosing the ext3 file system. If it does not work try the ext2 or ext4 with jaunty

---

### Post by john stiles on 2009-04-20
The above sound like good suggestions. If you still have problems though, see if another distro eg. Suse installs.

---

### Post by HazzaJ on 2009-04-21
Ok...
So a second CD presented the same problems so I assume its not a disc issue. 
I tested the memory and it said there were no errors.
I tried manual: I set 2000mb for "swap area" and the rest i said ext3 file systems and mounted it at "/". Is this correct? and it still didnt work. 
I tried replacing ext3 with ext2 and now its stuck at 1%. and it still didnt work.

What should i try now?

btw how long should i be expecting it to take to partition the HDD?

thanks,
HazzaJ

---

### Post by supererki on 2009-04-21
i havent seen this kind of problem but i would try :

1. download gparted and burn it to the disk and try to partition your harddisk with it ... 
2. try to write installation files to the usb drive and boot from there.
3. try different kernel.
4. try reiserfs ?

but its just a guess. good luck!

---

### Post by fballem on 2009-04-21
First of all, I admire your patience and your determination!

I would like to suggest that you download the Jaunty Beta and see if that installs. They have fixed a number of problems. Before you install it, please make sure that it boots to a live CD. I would then recommend installing once the live CD is up an running (there should be an icon for the installation on the desktop).

---

### Post by HazzaJ on 2009-04-21
> **supererki said:**
> i havent seen this kind of problem but i would try :

1. download gparted and burn it to the disk and try to partition your harddisk with it ... 
2. try to write installation files to the usb drive and boot from there.
3. try different kernel.
4. try reiserfs ?

but its just a guess. good luck!
thanks but...
I cant use gparted as my cd drive uses the ubuntu CD to run the OS and thus i cant run a second CD.

I also tried writing to a usb stick using the tool in ubuntu. However I dont think it works because i cant start ubuntu from it?!? 

Ill wait till the new version comes out before I try a different kernal.

Could this be a HDD issue? Should I get a new HDD?

---

### Post by feelshift on 2009-04-21
> Could this be a HDD issue? Should I get a new HDD? 
No. Just wait a couple of days for Jaunty to come out and try it (it has support for ext4 so try formating your partition with it instead of ext3 or ext2). :)

---

### Post by Sef on 2009-04-21
1) >  Could this be a HDD issue? Should I get a new HDD?     Unlikely.   Could be you have a bad set of cds.   Buy a new pack and see if one of those works for you.

2) [quote][No. Just wait a couple of days for Jaunty to come out and try it (it has support for ext4 so try formating your partition with it instead of ext3 or ext2). :smile:[quote]

Best not to use ext4.  It is still in beta, and there are problems with it losing data.  Also Ubuntu currently does not automatically boot up with ext4.

3) Also does the live cd run ok?

---

### Post by supererki on 2009-04-21
> **HazzaJ said:**
> thanks but...
I cant use gparted as my cd drive uses the ubuntu CD to run the OS and thus i cant run a second CD. 
you can make a bootable cd containing only gparted partition tool and not ubuntu. so perhaps you are able to partition your harddisk then..
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)


[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

check this tutorial for bootable usb.

---

### Post by supererki on 2009-04-21
perhaps try some other distro like suse or sth for partitioning ?

---

### Post by ugm6hr on 2009-04-21
Does the LiveCD actually work (i.e. Try Ubuntu without affecting your computer option)?

If yes - try using Partition Editor (GParted) to reformat your HD:
1GB swap, Rest as ext3.

Then install using the "Manual" option:
swap mounted as swap
ext3 mounted as /

It appears the partitioner in the Live Install is misbehaving.  Hopefully using GParted to do this will bypass the issue.

Also - did you check the md5sum on the downloaded iso file?  And did you try Sef's suggestion of using the "Check for errors"?

---

### Post by HazzaJ on 2009-04-21
Thanks for all the replies.

-Yes I can run ubuntu from the Live CD.

-I am currently trying to use gparted Live CD to partition the hdd. 
Hopefully it works.

I made 1 partition that is 2gb for linux-swap and the rest for ext3. I was un-sure how to set where to mount (like when you manually do it during the linux install) it or even if I needed to.  

If this fails then ill, firstly learn about the other ideas (different distro, sth, etc). 

I'll post back with results soon.

---

### Post by egalvan on 2009-04-21
> **HazzaJ said:**
> thanks but...
I cant use gparted as my cd drive uses the ubuntu CD to run the OS and thus i cant run a second CD.

Gparted also comes on its own Live CD, called gpartedLiveCD (clever name, that)

And it's also available as a USB / PXE / HD install...

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)


You can also try partedmagic LiveCD, a mini-distro that also works quite well.

[http://partedmagic.com/](http://partedmagic.com/)

This is the one that I use to partition all the drives on machines that I install software on.



> Could this be a HDD issue? Should I get a new HDD?

As others have stated, it is not likely to be a bad drive.
Possible, but not probable :)


Download the iso you want to try
Jaunty comes out in two days, but the mirrors will be swammped for some time, so you may need patience for a direct download.
Try torrents at this time, you will get much better download rates, and the reliability factor inherent in torrents

Next, check the iso with md5 or sha to verify the download.

Burn at slow speed (4x-8x)

Check the media for errors the first time you boot it.

finally, check for memory errors using memtest.

Hopefully, you will have a better time this go-around. :)

ErnestG

---

### Post by egalvan on 2009-04-21
One last suggestion...

Since you want to erase the drive and have Ubuntu as your only system,
then you may want to try erasing your drive first.

**Darik's Boot and Nuke** is an excellent way to COMPLETELY erase a drive.
I have used it for over two years to totally wipe drives clean.

[http://www.dban.org/](http://www.dban.org/)


download the iso, burn to CD and boot and nuke.

Note...
 there is no recovery option after you nuke a drive... 
make sure you want to erase the drive...
Use with care, it is a powerful tool.

---

### Post by HazzaJ on 2009-04-21
> **egalvan said:**
> One last suggestion...

Since you want to erase the drive and have Ubuntu as your only system,
then you may want to try erasing your drive first.

**Darik's Boot and Nuke** is an excellent way to COMPLETELY erase a drive.
I have used it for over two years to totally wipe drives clean.

[http://www.dban.org/](http://www.dban.org/)


download the iso, burn to CD and boot and nuke.

Note...
 there is no recovery option after you nuke a drive... 
make sure you want to erase the drive...
Use with care, it is a powerful tool.

Sounds good. Ill give it a go if gparted doesnt work. Its still working away at the moment.

---

### Post by HazzaJ on 2009-04-23
Now i'm really stuck!

I tried gparted and it still got stuck at 5% so i moved on to the boot and nuke.

I downloaded it and ran it and thought i would finally be able to get ubuntu but it just made it worse.

Now I cant even get to the installation steps or even boot directly from the live CD. All i get is a lot of numbers and words which seem to repeat something about a logical block. 

I tried to run gparted from CD but it seems to come up with the same things. 

What can I do? i'm really starting to think there maybe be something with HDD?!?

And help would be appreciated.

---

### Post by ilushkin on 2009-05-22
hugh, im expiriencing the very same problem. I will try 8.04.

---

### Post by ilushkin on 2009-05-22
> **ilushkin said:**
> hugh, im expiriencing the very same problem. I will try 8.04.

Mevermind, It was stuck for 20 min on 5% then moved on. False alarm, I assume.

---

### Post by ortayus on 2009-06-05
I was so happy when I saw this thread since I have the exact same problem.  I first tried Kbuntu 64bit, then Ubuntu 64bit, and then a lower version of Ubuntu 32bit.  I took a drive from an older PC that has XP on it and I am trying to use it but it gets stuck every time at 5%.  I have been making my discs with Vista64 but I will try to make a disk with XP and see if that makes a difference.  

Here is the hardware.
mobo: Asus P5N-D
chip: Intel Q9300 2.4GHz quad core
Drive: WD SATA I 120GB
Graphics: XFX 9800GTX+
Memory: 4GB (2x2GB) Crucial Ballistics


When I get done this will be a triple boot machine with Ubuntu, XP32, and Vista64.  But right now I have my Vista and XP drives unplugged.  Once I get Ubuntu loaded I will add it to the Vista boot loader.

---

### Post by knuckle dragging monkey on 2009-06-05
Hazza J i am new to ubuntu just like you  and i had the same problem. did it give you a boot error if so and even if it did not. I had to burn 3 cd's because the burn speed was to high. So i finaly bured it at x2 speed and it worked i know that sounds very low but it worked for me try it at x2 speed befor you try any thing more. take care and i hope that helps.

---

### Post by ortayus on 2009-06-06
> **knuckle dragging monkey said:**
> Hazza J i am new to ubuntu just like you  and i had the same problem. did it give you a boot error if so and even if it did not. I had to burn 3 cd's because the burn speed was to high. So i finaly bured it at x2 speed and it worked i know that sounds very low but it worked for me try it at x2 speed befor you try any thing more. take care and i hope that helps.


I made another disc using the slowest burn I could (4x on my 5 year old laptop) and it didn't work.  Actually I got the boot disk error so I would say this set me back.  

I also tried the "alternative" install and that gets stuck at 33% formatting.  

I have no idea why it does not like this drive. It passed all the checks.

---

### Post by ortayus on 2009-06-06
Okay, I found an earlier version of GParted and it won't work on my drive.  It fails whenever I try to make a ext3, ext4 or ext2 file systems.  The site is down so I can't get the latest Gparted version but I will try that when it is back up.

---

### Post by knuckle dragging monkey on 2009-06-07
well i hope everything works out for you. There is nothing more frustrating then a computer that wont ply fair. Good luck to you and take care bro.

---

### Post by ortayus on 2009-06-07
Before I call it quits with this drive I will hook it up to my AMD box and see what happens.

---

### Post by lkraemer on 2009-06-08
Hazzaj,
If you will look at the drive labels and find the Manufacturer Name,
then go to their website, you can download Diagnostics for the
Drive.  Is it an IDE or SATA Drive?  What Size?  Are you sure
the Jumper for Master/Slave/Cable Select is correct?

Also Gibson Research makes and sells Spinrite that does a good job
testing drives.  Version 5 will only do IDE drives.  Later versions
will do SATA.

lkraemer

---

