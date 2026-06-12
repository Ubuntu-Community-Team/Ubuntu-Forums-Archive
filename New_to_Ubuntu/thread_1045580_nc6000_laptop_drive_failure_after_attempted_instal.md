---
title: "nc6000 laptop drive failure after attempted install"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Humanitarian2112 on 2009-01-20
Folks,

I have an HP (Compaq) nc6000 laptop, it's been functioning fine using xp. Having multiple systems, I decided to see what the latest flavors of Linux have to offer and decuided to load ubuntu on this machine. I made an installation cd, went through the menus, on step 4 (partitioning), I set up 1 gig of swap, a /, /boot, /home, and /usr/local partitions using ext3. The system froze  some percentage into this step; didn't do anything for about an hour ( I have patience). After deducing that something had occurred, i hard cycled the machine and now get an error 1728 - hard drive failure. Additional attempts to reload ubuntu will not see the hard drive. What has happened? -and I tend to discredit hard drive failure, because it was working perfectly prior to this attempted install...

any help is appreciated...

---

### Post by JoshuaRL on 2009-01-20
Could you boot into the LiveCD and open a terminal?  Then post here the output of:
```

sudo fdsik -l
```
And that's a lowercase L, not a 1.

---

### Post by Humanitarian2112 on 2009-01-20
sudo fdisk -l provides no output -returns to command prompt.

---

### Post by handydan918 on 2009-01-20
Well, that doesn't sound so good...If you are running from the live cd (presumably!) try running gparted and see if it recognizes a drive. You might also ask your bios....

Thing is, when a hard drive fails, it has to fail at some point in time. Given the thousands of installs that happen every month, SOMEWHERE, a drive will fail during the install.

Maybe you just got lucky...

If you can't find the  drive with either gparted or the bios, I'd say you got lucky.

---

### Post by Humanitarian2112 on 2009-01-20
not found in gparted or bios. got lucky? lucky by having a thousand dollar web browser that was "freeware"?

---

### Post by JoshuaRL on 2009-01-20
> **Humanitarian2112 said:**
> not found in gparted or bios. got lucky? lucky by having a thousand dollar web browser that was "freeware"?

Well, here lucky is meant in the ironic sense.  Sorry.  Do you happen to have a warrantee left on the drive or computer?  If so, it would be a good idea to check into getting it replaced.

---

### Post by handydan918 on 2009-01-20
> **Humanitarian2112 said:**
> not found in gparted or bios. got lucky? lucky by having a thousand dollar web browser that was "freeware"?

Yep, if it wasn't found by either bios or gparted, I'd have to say it likely gave up the ghost. 
guess I don't understand the reference to a > thousand dollar web browser that was "freeware"

If I guess right, that lappy is about 4-5 years old, and that is certainly old enough for a drive to be thrashed to death....
I just had to put a new drive in my lappy because I set it down a little hard before the drive was done spinning down...it happens.

---

