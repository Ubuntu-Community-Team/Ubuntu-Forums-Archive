---
title: "Looks like a corrupt hard drive"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by OutOfReach on 2009-01-24
So I was stupid enough to forget to unmount a remote filesystem that I mounted with sshfs when I shutdown my desktop...
Ubuntu, upon reboot when my laptop started to get really laggy, threw me errors that looked similar to:
```

ata1.000: Error: {DRDY ERR}
ata1.000: Error: {UNC}

```
And then EXT3-fs said that it couldn't read a block or inode (dont remember which).
and then it loops...

Now I sit here with a laptop with a (seemingly) corrupt hard drive. I have tried to delete all partitions and leave it all unallocated, it worked but now I cannot install any operating system (havent tried Windows but I expect the same), they all give me the same error as above when trying to install.

Is there hope?
Or is it completely gone?

---

### Post by handydan918 on 2009-01-24
Seems like a good spot for a live cd. Boot up a live cd and mount your HD, and see if you can read it...

Also check in with the BIOS, see if it's recognized there...

---

### Post by OutOfReach on 2009-01-24
Before I formatted the drive, all of the partitions were mountable except #5, which was the filesystem that was mounted via sshfs...
Which led me to believe that if I wiped this partition, everything will work again, but no, Ubuntu still gave me the same errors. So I deleted all the partitions on my hard drive (with GParted via a SystemRescueCD I had around) to see if that would solve it, again no avail.

There might be a better way to format my hdd and possibly fix this problem?

---

### Post by OutOfReach on 2009-01-24
Looks totally wrecked, the DST test in my BIOS failed, so now I know that it is not fixable (also checked with the Windows XP recovery console on the CD).

*sigh* Now I gotta buy a new hard drive...

---

### Post by starcannon on 2009-01-24
I've been seeing a few more laptops come through my place lately, and HDD's are always an issue on laptops. 

Deal is, HDD's do not like to be subjected to shocks of any sort; laptops are terrible for giving a HDD the very thing it does not like.

Some things HDD's do no like: bookbags, setting them down, dropping them, bumping them, riding around in a bouncy car, bus, train, plain, etc... etc...

On my personal laptops HDD's will be replaced with Solid State Disks as the Hard Disks die. Solid State Disks(SSD) have no moving parts, no needles to go skating across a platter; we like this, this is good. Now the book bag is no longer a high risk area, its actually a fairly safe storage solution.

GL and Have fun.

---

