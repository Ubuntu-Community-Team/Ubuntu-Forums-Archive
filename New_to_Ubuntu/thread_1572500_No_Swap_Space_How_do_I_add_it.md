---
title: "No Swap Space How do I add it?"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by GaryTheCat on 2010-09-11
Pretty much as the title suggests

I installed ubuntu on my dad's pc but there doesn't appear to be any swap space. How can I add it?

TIA

G

---

### Post by Lateralis on 2010-09-11
I guess double check to ensure there isn't a swap partition somewhere on the compter: 

```

sudo blkid | grep swap

```

If there is a swap partition somewhere on the computer, you should get something like:

/dev/sdb5: UUID="0462dfde-4f74-44cd-bf3c-6aa4d264d0a1" TYPE="swap"

You can then turn swap on or off by issuing 
```

sudo swapon <device>
and 
sudo swapoff -a

```

respectively, where <device> is the /dev/sdXY label; in my case /dev/sdb5.

If you get nothing, then you will have to either: 

- make a swap area using **mkswap** command.  I've never used it before so would advise caution.  Esentially you specify to Linux a file or device as a temporary swap area

- Make a new partition, format it as swap and then add the necessary lines to /etc/fstab to automount at boot.  The formatting can be done using **gparted**, although the usual warnings about damaging/destroying data with any changes to a hard drive's partition table should be heeded.

---

### Post by rocknrollmouse on 2010-09-11
I had a similar problem about a year ago.  
I learnt to read, and build you command set before before acting, & everything went well.

Check your SWAP status as advised by Lateralis.

These are the links I used to help resolve my missing SWAP:
My post; different ubuntu & disk config, but same problem: [http://ubuntuforums.org/showthread.php?t=1255240]("http://ubuntuforums.org/showthread.php?t=1255240")
Good advice [http://ubuntuforums.org/showthread.php?t=841988&highlight=Missing+SWAP+partition]("http://ubuntuforums.org/showthread.php?t=841988&highlight=Missing+SWAP+partition")
SWAP for beginners [https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")
Manual for swapon/swapoff [http://manpages.ubuntu.com/manpages/lucid/man8/swapon.8.html]("http://manpages.ubuntu.com/manpages/lucid/man8/swapon.8.html")

Hope this helps,
Simon

---

