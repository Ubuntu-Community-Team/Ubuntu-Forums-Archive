---
title: "Can I install 11.04 alongside my Windows 7?"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by papuccino1 on 2011-04-30
Does Wubi work with Ubuntu 11.04 and is the speed of the OS the same as natively installing the operating system via a regular install?

Thanks for the help! :)

Ideally, I would like to turn on my Toshiba A665 and have a menu pop up asking me if I want to boot Windows 7 or Ubuntu.

Thanks!

---

### Post by sikander3786 on 2011-04-30
Yes reportedly, Wubi is working for 11.04 and Windows 7 but I've never been a Wubi fan so can't advise much.

For a dual-boot pop up menu, a Wubi install or even a proper install would let you choose between Windows and Ubuntu at start up.

A proper install is a bit faster than Wubi and is less troubling most of the times. See this link if you want to properly dual boot.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

---

### Post by Frogs Hair on 2011-04-30
Wubi won't be as fast as traditional dual boot , but it is great for a Ubuntu trial or occasional use . I have let some Wubi users borrow my 11.04 disk and it seems to be working fine with Win 7 . Download the ISO and Install with Wubi and if you like 11.04 then Move to a traditional dual boot. I got started that way. I don't know when Wubi for 11.04 will be on the Ubuntu Website that is why I suggest downloading the ISO . I currently dual boot Win 7 32 bit and Ubuntu 11.04 64 bit.

---

### Post by pierreyy on 2011-08-02
i own a toshiba a665 aswell with dual boot between win 7 and ubuntu 11.04 asnd it works very well... except the backlite keyboard...

---

### Post by lkraemer on 2011-08-02
Not from my experience.  Win7 gobbles up all but one partition.
Maximum of 4 Primary Partitions for any Physical hard drive.

Linux requires at a minimum two partitions, / & swap.  And you only
have one available as Primary.  I guess you could make one more
extended partition and install both there, but I'm not a big fan of
extended partitions due to a massive problem years back.  I'd rather
suggest buying a new drive, removing Win7 and installing Linux on the
new drive and never look back.  You won't be sorry.

lk

---

### Post by pierreyy on 2011-08-18
> **lkraemer said:**
> Not from my experience.  Win7 gobbles up all but one partition.
Maximum of 4 Primary Partitions for any Physical hard drive.

Linux requires at a minimum two partitions, / & swap.  And you only
have one available as Primary.  I guess you could make one more
extended partition and install both there, but I'm not a big fan of
extended partitions due to a massive problem years back.  I'd rather
suggest buying a new drive, removing Win7 and installing Linux on the
new drive and never look back.  You won't be sorry.

lk

   my experience is infront of me and $10 says it works:P... i had absolutely no problem installing, forget the whole extended partition stuff... it works fine ( except the backlite keyboard)

---

### Post by im.saravanan on 2011-08-19
I think a clean install is better than wubi. 
And you not worry about what kind of partitions it should be. because Ubuntu takes care of it automatically during installation. If no more primary partitions can be created it creates extended.

Plz correct me if i am wrong.

---

### Post by abnordude on 2011-08-19
Not much of a fan of wubi. 

I think that dual boot is quite better.
Also, while installing, Ubuntu recognizes the windows installation and asks whether you want to install Ubuntu alongside windows.
There will be no worry about partitioning as the installer will do that work for you.
And you will get the desired result.

---

