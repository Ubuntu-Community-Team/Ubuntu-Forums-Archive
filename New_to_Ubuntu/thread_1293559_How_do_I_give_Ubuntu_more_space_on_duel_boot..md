---
title: "How do I give Ubuntu more space on duel boot."
date: 2009-10-17
forum: New to Ubuntu
---

### Post by pirate paul on 2009-10-17
Hi, I have duel boot windows and Ubuntu, I need to install updates but it says I do not have enough disc space. How do I give windows less and Ubuntu more space.

---

### Post by philinux on 2009-10-17
Open a terminal, Apps>Accessories>Terminal then use the command.

```
df -h
```

Post the results back here.

---

### Post by pirate paul on 2009-10-17
A ha... its you again .. hows it goin... ?
I took your advice and got a duel boot, I can now top up my vodafone.
Thanx.

It says.....
paul@paul-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             2.3G  2.2G     0 100% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  104K  497M   1% /var/run
varlock               497M  4.0K  497M   1% /var/lock
udev                  497M  164K  497M   1% /dev
tmpfs                 497M  120K  497M   1% /dev/shm
lrm                   497M  2.4M  495M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
paul@paul-laptop:~$ 

Not the foggiest.....?

---

### Post by Paqman on 2009-10-17
Easiest way is to boot up into your LiveCD, go to System > Admin > Partition Editor, make sure everything is unmounted (including swap, right click and "swapoff" if required). Then shrink one partition and expand the next.

This can be a very slow operation, and require other partitions to be shifted about. Take a backup of your data before messing about with partitions, just in case.

---

### Post by pirate paul on 2009-10-17
I do not understand.

I went system>admin there is no partition editor... 

Do you mean I use the Ubuntu start up disc, not the installed version?

Thanx.

---

### Post by philinux on 2009-10-17
```
paul@paul-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             2.3G  2.2G     0 100% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  104K  497M   1% /var/run
varlock               497M  4.0K  497M   1% /var/lock
udev                  497M  164K  497M   1% /dev
tmpfs                 497M  120K  497M   1% /dev/shm
lrm                   497M  2.4M  495M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
paul@paul-laptop:~$ 
```

You didn't give ubuntu enough space 2.3gig is way too small. I would say 6 minimum. Some would say 12gig is about ok.

---

### Post by Gone fishing on 2009-10-17
Yep he means start up on the live installation disk then go to System > Admin > Partition Editor you could also download a gparted live cd iso and use that.

But do back up your data and it will take time, I'd also defrag windows first. If you are using Vista you can shrink the Windows partition from within Vista that might be quicker.

---

### Post by Paqman on 2009-10-17
> **pirate paul said:**
> 
Do you mean I use the Ubuntu start up disc, not the installed version?


Yes. You can't modify any partition which is in use. So if you boot up into the LiveCD, you're running completely off the CD, not your hard drive and are free to modify it.

The LiveCD has the partition editor installed in the menu I mentioned.

Make sure you do that backup first though.

---

### Post by philinux on 2009-10-17
> **Gone fishing said:**
> Yep he means start up on the live installation disk then go to System > Admin > Partition Editor you could also download a gparted live cd iso and use that.

But do back up your data and it will take time, I'd also defrag windows first. If you are using Vista you can shrink the Windows partition from within Vista that might be quicker.

+1.

Shrinking windows partition with vista is pretty darn quick. I've done this twice on a lappy.

---

### Post by tpjk on 2009-10-17
if you want more information on partitioning and gparted (a/k/a Partition Editor) you should check out this link:

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by pirate paul on 2009-10-17
I am happy to defrag and shrink vista ultimate but when I tried to change the partition size last time I had problems and could not change the size of the partitions. 
Can I shrink vista with out reinstalling it?
The problem with reinstalling is I cannot go on line to ask how to solve problems until I have installed. 

How do I change the partitions in vista?

I am not too good with computers, simple instructions would be appreciated.

I have got to go .... I will be back in a couple of hours.

Thanx.

---

### Post by philinux on 2009-10-17
> **pirate paul said:**
> I am happy to defrag and shrink vista ultimate but when I tried to change the partition size last time I had problems and could not change the size of the partitions. 
Can I shrink vista with out reinstalling it?
The problem with reinstalling is I cannot go on line to ask how to solve problems until I have installed. 

How do I change the partitions in vista?

I am not too good with computers, simple instructions would be appreciated.

I have got to go .... I will be back in a couple of hours.

Thanx.

[http://www.mydigitallife.info/2006/11/27/change-or-resize-partition-ntfs-fat-or-fat32-size-in-windows-vista/](http://www.mydigitallife.info/2006/11/27/change-or-resize-partition-ntfs-fat-or-fat32-size-in-windows-vista/)

Have fun. ;)

---

### Post by ikisham on 2009-10-17
Just for you to know. It wasn't your fault. It seems there is (or was) a bug in the Ubuntu installer that would give it only that amount of space when set to do the dual-boot automatically.
The minimum recommended space is 6 GB.

---

