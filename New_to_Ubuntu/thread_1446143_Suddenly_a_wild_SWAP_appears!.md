---
title: "Suddenly a wild SWAP appears!"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by bornagainpenguin on 2010-04-03
I'm using Ubuntu Karmic with all updates (that I know of) and everything seemed to be shaking out okay.  Then earlier I went to check System Monitor about something and discovered that it was claiming a 248.5MiB swap existed somewhere.  This is disconcerting because I have an eeepc with an SSD drive so I did not install Ubuntu with a swap...

Can someone tell me how I now suddenly have a swap and what I need to do to disable it and then make sure this doesn't spontaneously happen again?  Thanks in advance!

--bornagainpenguin

---

### Post by Naitsirhc Hsem on 2010-04-03
have you looked at gparted?

---

### Post by bornagainpenguin on 2010-04-03
> **Naitsirhc Hsem said:**
> have you looked at gparted?

Yes and gparted doesn't list there being a partition that would be used for swap.  This leads me to wonder if Ubuntu created a swap file somewhere on me.  I know it is possible to do so, but as I posted above being on a netbook with an SSD I never bothered with such stuff...

--bornagainpenguin

---

### Post by srs5694 on 2010-04-03
Type "swapon -s". That should show you what file or partition is being used for swap. You can then check /etc/fstab to see if there's a corresponding entry, and if there is, disable it by putting a "#" character as the first character on its line.

As to how this happened, I don't know. There are so many tools in Ubuntu (and many other modern Linux distributions) that assume an "I-know-better-than-any-stinking-HUMAN" attitude to administration that I wouldn't want to guess what might be doing it.

---

### Post by bornagainpenguin on 2010-04-03
> **srs5694 said:**
> Type "swapon -s". That should show you what file or partition is being used for swap. You can then check /etc/fstab to see if there's a corresponding entry, and if there is, disable it by putting a "#" character as the first character on its line.

Typing in the first gave me this:

```
bornagainpenguin@blessings:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/ramzswap0                          partition	254508	0	100
```

Checking my fstab revealed no corresponding partition (unless I sorely misunderstood what was set when I did some SSD optimization...)

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=089b5722-17a6-46ad-a986-ce6b579efb4b /               ext4    noatime,errors=remount-ro 0       1
# /usr/local/misc was on /dev/sdb1 during installation
UUID=ec5f9cad-a4f3-4aba-b759-7908d5547be7 /usr/local/misc ext4    defaults,noatime        0       2
#
#
# SSD optimization...
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
none /var/tmp aufs noatime,br:/tmp=rw:/var/tmp=ro 0 0
none /var/cache aufs noatime,br:/tmp=rw:/var/cache=ro 0 0
```

At this point it looks like Ubuntu saw the ramdisk intended for the /tmp and arbitarily decided this would be a good place to use for swap...  Is that what you think too or did I somehow instruct the system to do what it is doing and failed to realize it?

> **srs5694 said:**
> As to how this happened, I don't know. There are so many tools in Ubuntu (and many other modern Linux distributions) that assume an "I-know-better-than-any-stinking-HUMAN" attitude to administration that I wouldn't want to guess what might be doing it.

Heh...yup.  That sort of thing works out well when it works.  The problem is when it doesn't work, things get so broken no one can do anything to fix it, or at least the poor slob who only knows a few things here and there like myself gets stuck...

So, any way...  Did I do this (unintentionally)  or am I getting bit by something trying to "help" me and failing?

--bornagainpenguin

---

### Post by Sir Jasper on 2010-04-03
Hi again,

If you open your terminal and insert:
sudo swapoff /dev/ramzswap0 
does System Monitor still report it as in use?

Even if that works it will not be permanent.

My regards

Addendum:
It has been kindly pointed out to me that I originally omitted a space from the above which I have now corrected, and I am told it works.

---

### Post by bornagainpenguin on 2010-04-03
> **Sir Jasper said:**
> Hi again,

If you open your terminal and insert:
sudo swapoff/dev/ramzswap0 
does System Monitor still report it as in use?

Even if that works it will not be permanent.

My regards

Yes it did, after I added a space to the command so it would execute.

```
sudo swapoff /dev/ramzswap0
```

(Not trying to be a pain in the #### to someone who is trying to be helpful, but I want this to be clear in case someone else with the same issues comes accross this post in Google.)

So now what do I do to make this permanent?  Also any ideas as to what might be causing it?

Thanks for your help.

--bornagainpenguin

---

### Post by NightwishFan on 2010-04-03
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

This should answer some questions.

---

### Post by WelshChris on 2010-04-03
This appears to be swap created on the fly on weaker systems.

[http://code.google.com/p/compcache/](http://code.google.com/p/compcache/)

It's also disucussed on this thread.
[http://ubuntuforums.org/showthread.php?p=7268741](http://ubuntuforums.org/showthread.php?p=7268741)

Chris

---

### Post by bornagainpenguin on 2010-04-03
> **NightwishFan said:**
> [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

This should answer some questions.

Really?  Which ones?

I read the page, checked out a few things, but the instructions seem to be for someone who wants to add a swap or wants to learn how much swap they should have--not anything for someone who doesn't want a swap and doesn't understand why there is suddenly a swap somewhere when he didn't ask for one and doesn't want one.

Do you have a page that can explain to me where the swap came from and how to prevent it from coming back?

Thanks for your time.

--bornagainpenguin

---

### Post by Gone fishing on 2010-04-03
ramzswap

> Essentially, it allows systems with weaker specs to run Ubuntu without any major hickups (lag) (found on another thread)

Have a look at [http://code.google.com/p/compcache/](http://code.google.com/p/compcache/)

Seems to be a way of creating a virtual compressed swap partition in RAM so as to make the most of limited RAM space - possibly as your netbook doesn't have a swap partition this is necessary to run memory intensive applications?

---

### Post by NightwishFan on 2010-04-03
Sorry, forgive me, I just figured this question was about standard swap, and I linked this. I read the thread after. Here is a link about compcache being used in the 2.6.33 kernel.

[http://kernelnewbies.org/LinuxChanges#head-2fce8c55c41f7d0bc23ecaa553ccc62d2328e5ee](http://kernelnewbies.org/LinuxChanges#head-2fce8c55c41f7d0bc23ecaa553ccc62d2328e5ee)

---

### Post by Sir Jasper on 2010-04-03
Hi,

You were not a pain at all and right to correct my error. I will make a correcting  addendum to my above post.

I wonder if it would be possible to add the code line in an added startup entry, but the sudo part may preclude that.

I don´t have any other ideas but I&#7743; sure others will know and advise your best course of action.

My regards

---

### Post by bornagainpenguin on 2010-04-03
> **WelshChris said:**
> This appears to be swap created on the fly on weaker systems.

[http://code.google.com/p/compcache/](http://code.google.com/p/compcache/)

It's also disucussed on this thread.
[http://ubuntuforums.org/showthread.php?p=7268741](http://ubuntuforums.org/showthread.php?p=7268741)

Chris

> **Gone fishing said:**
> ramzswap

 (found on another thread)

Have a look at [http://code.google.com/p/compcache/](http://code.google.com/p/compcache/)

Seems to be a way of creating a virtual compressed swap partition in RAM so as to make the most of limited RAM space - possibly as your netbook doesn't have a swap partition this is necessary to run memory intensive applications?

Bam!  You guys got it and fixed my problem right up!  I'm going to have to make a post to the Launchpad thread confirming that this appears to be an issue also occurring with remastersys installation.  I followed the instructions given in the Ubuntu Forums thread and it fixed my issue.  Thanks very much for your help--everyone who responded!

--bornagainpenguin

---

