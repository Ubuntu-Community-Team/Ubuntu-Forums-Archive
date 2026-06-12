---
title: "ubuntu installation fails"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by mistypotato on 2009-03-15
Hi,

I have installed ubuntu dozens of times with no problem.  So, I offered to install it for a friend on his computer and guess what?  ;)

Here's what's happening.

Right after I enter his username and password and it's entering the partitioner, it fails every time I re-try with the following message...

**[COLOR="Red"]The creation of swap space in partition #5 /dev/sda failed.[/COLOR]**

That's it.  I cannot use gparted or any other means that I can find that will partition the HD :(

**********
It may be worth noting that I had to LOW LEVEL format the drive because of a virus before installing ubuntu but I thought that the ubuntu partitioner would be able to create the necessary partitions.  If not, then I can use acronis to lay down a basic file system on the HD THEN go back and install ubuntu.
**********

your advice is appreicated.

thx

---

### Post by Temposs on 2009-03-15
You'll have to reinstall, looks like. Something with the initial partitioning got mucked up.

Have you installed with that particular CD before? Did you check the md5 sum?

---

### Post by damis648 on 2009-03-15
Can you boot up the LiveCD and post the output of
```
fdisk -l
```

---

### Post by Moop on 2009-03-15
Try using a GParted live cd?

---

### Post by mistypotato on 2009-03-15
Good Morning how are you and Thanks foir the replies :D

After posting this, I went back and tried acronis and it even reported it could not write to the drive so something went rally sour with the drive so I'm going to try low level formatting it again and then try your suggestions.

Thank you SO much for taking the time to answer :KS:KS:KS:KS:KS

---

### Post by mistypotato on 2009-03-15
Yeow!

It appears something has happened to the HD.

I'm going to have to get the manufacturer's diagnostic disk and find out if it's fixable or not.

Have a super day all and thanks again for your help.

You folks are the GREATEST !! :KS:KS:KS:KS:KS:K

---

### Post by mistypotato on 2009-03-16
Turns out it WAS the HD.

Apparently the Low Level format deleted the bad sectors table and so the install didn't know to avoid those sectors.  Many Hard Drives are considered New and good if they have less than an industry standard of bad sectors.

Reformatting with the option to mark bad sectors cured the HD.

---

