---
title: "Help needed im really in it now.."
date: 2011-08-06
forum: New to Ubuntu
---

### Post by spillage on 2011-08-06
Hi All,

Yesterday I added an extra 1tb hd to my system as you can never have enough and now it wont boot 10.04.

I seems to start the plymouth splash page but stops..

I just get some broken graphics at the top.

I have set up a separate /home but for the life of me cannot see how to install a fresh installation and use my old /home.

Do I just add the swap, / and not set up any thing as /home ?????

Its seems to only allow you access to one partition in the set up..

any help would be appreciated...

Please not I have had to get on here with a 2.8" mobile screen so have tried the google stuff but as you can imagine its not too easy...


cheers,

spill.

---

### Post by zero2xiii on 2011-08-06
Ah this is a pretty straight forward solve (in some way)

To setup a new ubuntu install and using your previous install's home directory:

Simply during install:
Setup the path to / (and format)
Setup the path to SWAP (automaticaly formated)
Setup the path to the PREVIOUS /Home (and DONT format!)

You will get a notice that says you should backup, all aplication data in folders NOT marked for format will be lost.. Dont worry about this, just continue. It wont over write the files in the home directory, and once booted, it should be like you never left (as all aplication's settings is also stored in the /Home directory of the user) Just make sure to setup the username to be the exact same as teh previous install, otherwise you will need to copy the old home's contend to the newly created home directory of the new user.

As to WHY this all happend? I have no idea, possibly attaching the new HDD caused the partions to be shifted around (eg SDA became SDB) and thus ubuntu cant find the partitions, try changing the prioroty in in BIOS of the devices, and also try to attach the HDD to another port (esp if its a SATA drive, try putting the drive with ubuntu on in the SATA-0 port and then the new drive in the SATA-1 port.)

---

### Post by spillage2 on 2011-08-06
Thanks ever so much zero....


I think the lack of sleep and the feeling you have lost everything frazzled my brain..Just needed a kick up the butt..

All up and running a few tweeks needed...

This is why linux kicks windoz backside....god bless the ability to have a separate /home well worth the effort to set up in the first place...

The ability to install a fresh install but still keep you old settings emails and everything else is just amazing...


Spill.

---

### Post by zero2xiii on 2011-08-06
Glad I could help :)

Please remember to mark the thread as solved.

---

### Post by Noncon on 2011-08-06
> **spillage2 said:**
> Thanks ever so much zero....


I think the lack of sleep and the feeling you have lost everything frazzled my brain..Just needed a kick up the butt..

All up and running a few tweeks needed...

This is why linux kicks windoz backside....god bless the ability to have a separate /home well worth the effort to set up in the first place...

The ability to install a fresh install but still keep you old settings emails and everything else is just amazing...


Spill.

Probably, but you usually don't have to re-install Windows after installing a hard drive. :)

Glad you got it working, but as a newbie myself, I'm wondering what caused the original problem. 

kj

---

### Post by JKyleOKC on 2011-08-06
> **Noncon said:**
> Glad you got it working, but as a newbie myself, I'm wondering what caused the original problem.It's impossible to say, from a distance, but the most likely reason is that the new drive caused existing drives' names to change, such as /dev/sda becoming /dev/sdb. This can happen because the names are actually created during the boot process, not remembered anywhere between sessions, and are assigned in sequence as the drives acknowledge their initialization commands. If the new drive responds before the old one, it gets the "sda" designation!

That's why the "UUID" identifiers are preferred in the /etc/fstab file; I thought that all recent versions of Ubuntu used them by default. However if you don't see them in your /etc/fstab file, it's fairly easy to change things so that they will be used in the future. Search the forums for "UUID" or "fstab" and you'll find lots of discussion...

---

### Post by CatKiller on 2011-08-06
> **Noncon said:**
> Probably, but you usually don't have to re-install Windows after installing a hard drive. :)

No, but you might need to phone Microsoft and beg them to allow you to continue using your computer.

---

