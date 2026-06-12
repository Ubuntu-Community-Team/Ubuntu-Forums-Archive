---
title: "not enough room on the disk to save?"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by Whatnotery on 2009-06-08
ok so I'm trying to download a zip file with firefox but every time I get midway through the download a window pops up saying:
[FONT=Courier New]
There is not enough room on the disk to save /home/john/HIA 024 - The Little Hands of Asphalt - Leap Years.zip.

Remove unnecessary files from the disk and try again, or try saving in a different location.[/FONT]

I know for a fact that there is enough space on my hard drive. how do I fix this problem?

---

### Post by nandemonai on 2009-06-08
> **Whatnotery said:**
> ok so I'm trying to download a zip file with firefox but every time I get midway through the download a window pops up saying:
[FONT=Courier New]
There is not enough room on the disk to save /home/john/HIA 024 - The Little Hands of Asphalt - Leap Years.zip.

Remove unnecessary files from the disk and try again, or try saving in a different location.[/FONT]

I know for a fact that there is enough space on my hard drive. how do I fix this problem?

Please post the output of this command in terminal:

```
df -h
```

You may have space on your Windows disk but I'm assuming your wubi virtual drive is maxed out.

---

### Post by lhb1142 on 2009-06-08
I don't know if this will help you but it may be worth a try.

When I've run across a "strange" problem and can't figure out what is wrong (most often I'm doing nothing wrong), what I do is to restart the computer and then try again to do whatever it I was doing with no success.

Often this is enough to "clear" whatever was causing a problem on the computer and the process then proceeds normally.

Good luck.

---

### Post by cariboo on 2009-06-08
Depending on how many packages you installed and how many updates you have done, you may be able to claim a fair amount of hard drive space by cleaning out the archived packages in /var/cache/apt/archives. to do this open an Applications-->Accessories-->Terminal and type:

```
sudo apt-get clean
```

and to clean out any unneeded dependencies, in the same terminal type:

```
sudo apt-get autoremove
```

on average this should gain you about .5Gb of free hard drive space.

---

### Post by Whatnotery on 2009-06-08
> **nandemonai said:**
> Please post the output of this command in terminal:

```
df -h
```You may have space on your Windows disk but I'm assuming your wubi virtual drive is maxed out.
   

heres what I got:
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      8.5G  8.0G   23M 100% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M  104K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M  144K 1003M   1% /dev
tmpfs                1003M  396K 1002M   1% /dev/shm
/dev/sda3              51G  9.6G   42G  19% /host
lrm                  1003M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   24K 1000K   3% /tmp
/dev/sda2              52G   23G   29G  45% /media/ACER

---

### Post by Ocxic on 2009-06-08
Your hard drive is full, 8.5G cap, 8G used, 23MB free. you either need a bigger hard drive/partition or delete unnecessary files from your computer.

---

### Post by Whatnotery on 2009-06-08
> **Ocxic said:**
> Your hard drive is full, 8.5G cap, 8G used, 23MB free. you either need a bigger hard drive/partition or delete unnecessary files from your computer.
   
how do you increase the size of a partition?

---

### Post by nandemonai on 2009-06-08
It can be tricky, but if you want to resize your wubi disk then you can try:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

Be sure to backup first in case anything goes awry.

---

### Post by jediknight64 on 2009-06-08
> **nandemonai said:**
> Please post the output of this command in terminal:

```
df -h
```

You may have space on your Windows disk but I'm assuming your wubi virtual drive is maxed out.

Hello.Same problem here and the output is as follows.

```
john@john-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                 972M     0  972M   0% /lib/init/rw
varrun                972M  104K  972M   1% /var/run
varlock               972M     0  972M   0% /var/lock
udev                  972M  164K  972M   1% /dev
tmpfs                 972M  472K  972M   1% /dev/shm
lrm                   972M  2.4M  970M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   20K 1004K   2% /tmp
/dev/sr0              234M  234M     0 100% /media/cdrom0
john@john-laptop:~$ 
```

Thank you.

---

### Post by nandemonai on 2009-06-08
> **jediknight64 said:**
> Hello.Same problem here and the output is as follows.

[CODE}john@john-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                 972M     0  972M   0% /lib/init/rw
varrun                972M  104K  972M   1% /var/run
varlock               972M     0  972M   0% /var/lock
udev                  972M  164K  972M   1% /dev
tmpfs                 972M  472K  972M   1% /dev/shm
lrm                   972M  2.4M  970M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   20K 1004K   2% /tmp
/dev/sr0              234M  234M     0 100% /media/cdrom0
john@john-laptop:~$ [CODE]

Thank you.

Looks like you have a real install. Your / partition is way too small (2.3G). Is this a dual boot machine? You'll need to resize your partition with partition editor on the live CD if possible. If you plan to do this I highly recommend doing a proper backup of everything on the drive (including windows if it's on the same disk) before attempting a partition resize.

---

### Post by jediknight64 on 2009-06-08
I have an Acer Aspire laptop. It is dual boot. I'll give it a try and again, I Thank you.

---

### Post by nandemonai on 2009-06-08
> **jediknight64 said:**
> I have an Acer Aspire laptop. It is dual boot. I'll give it a try and again, I Thank you.

In that case I suggest first and foremost backing up your important files. Then boot from the Live CD, fire up partition editor from System -> Admin and shrink your Windows partition while extending your Linux partition. Apply, make a coffee and sit back with your fingers crossed ;)

It's not common that partition resizing fails but it can happen. Defragging your Windows partition first is helpful I hear.

---

### Post by jediknight64 on 2009-06-09
> **nandemonai said:**
> In that case I suggest first and foremost backing up your important files. Then boot from the Live CD, fire up partition editor from System -> Admin and shrink your Windows partition while extending your Linux partition. Apply, make a coffee and sit back with your fingers crossed ;)

It's not common that partition resizing fails but it can happen. Defragging your Windows partition first is helpful I hear.

I'm defragging now. In all honesty ,I must confess to being a complete newb at Linux in general, but I am determined to learn and I am grateful for any and all advice. I am running Vista and Jaunty in my dual boot, 2GB DDR2, 250GB HDD(2 Internal Hard Drives). 

1)Is there anything else I need to do before I start the partition process?

2)Is there anything I need to be on the look-out for or is this fairly simple, or

3)Is this me biting off more than I can chew?

---

### Post by nandemonai on 2009-06-09
> **jediknight64 said:**
> I'm defragging now. In all honesty ,I must confess to being a complete newb at Linux in general, but I am determined to learn and I am grateful for any and all advice. I am running Vista and Jaunty in my dual boot, 2GB DDR2, 250GB HDD(2 Internal Hard Drives). 

1)Is there anything else I need to do before I start the partition process?

2)Is there anything I need to be on the look-out for or is this fairly simple, or

3)Is this me biting off more than I can chew?

1. Backup, like I said previously ;)

2. Not really, it's pretty straight forward. Once in partition editor on the Live CD make sure you select the correct disk! That's the main thing really. You don't want to resize the wrong disk.

3. I don't think so. It may seem complicated at first but once you've done it once or twice it'll make sense.

---

### Post by bg26892 on 2009-06-12
> **nandemonai said:**
> 1. Backup, like I said previously ;)

2. Not really, it's pretty straight forward. Once in partition editor on the Live CD make sure you select the correct disk! That's the main thing really. You don't want to resize the wrong disk.

3. I don't think so. It may seem complicated at first but once you've done it once or twice it'll make sense.

I'm having the same issues here with a windows dual boot machine - can you tell me what the "Live CD" is?

Thanks!

---

### Post by bacardiandwatermelon on 2009-06-12
The cd that you installed ubuntu off??? I hope they change the partition section on the karmic install. So many people installed jaunty on such tiny partitions, there must be an easier way... ......Easier than moving a slider bar :-P

---

