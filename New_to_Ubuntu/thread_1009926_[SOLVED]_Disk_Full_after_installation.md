---
title: "[SOLVED] Disk Full after installation"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by CageUK on 2008-12-13
Hi

I've just installed 8.10. After I installed Ubuntu onto a 20gb partions (dual boot with vista on a new laptop) my available diskspace read as 1gb. about 10mins later the disk had no space on it. All I had done was to browse the operating system and activated the proprietory graphics driver. The df results are here.

mark@mark-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             20157308  19291928         0 100% /
tmpfs                  1553708         0   1553708   0% /lib/init/rw
varrun                 1553708       104   1553604   1% /var/run
varlock                1553708         0   1553708   0% /var/lock
udev                   1553708      2840   1550868   1% /dev
tmpfs                  1553708       104   1553604   1% /dev/shm
lrm                    1553708      2000   1551708   1% /lib/modules/2.6.27-7-generic/volatile
overflow                  1024        52       972   6% /tmp
mark@mark-laptop:~$ 

I have run the empty trash command and have turned on the trash icon which shows as empty. 
I have also run the install localepurge but this couldn't write something due to lack of space. 
I have also ran the sudo apt-get clean/autoclean/autoremove commands etc 

I have searched and read that Ubunto should only take about 3-4gb so I'm wondering what I have done wrong. 

I don't have a swap partition as I have 3gb memory. I can't run firefox due to either permissions or disk full so it's a real pain to flit from Ubunto to Vista to investigate these problems so any help would be very gladly appreciated.

Thanks and it's a great forum!

---

### Post by ugm6hr on 2008-12-13
Honestly, I don't know what has happened.

But I'd suggest you just reinstall.

Check the CD for errors first though.

And use a 6-700MB swap.

---

### Post by Paqman on 2008-12-13
That's pretty bizarre. If you open the disk usage analyser with:
```
gksu baobab
```

It should show where all the storage has gone. Something might jump out at you.

---

### Post by CageUK on 2008-12-14
That's strange I thought I'd already replied to this. Hmmm.

Anyways, the info you gave me Paqman lead me to spot that the home directory was almost the size of the whole installation. I then discovered that Ubuntu had imported stuff from my user folder in my Vista installation (music, downloaded files etc). I know I saw an import something option when I installed Ubuntu but I thought that was mail settings. Once I'd established that the stuff in the home directory was a copy I shift-deleted it and all is fine and dandy again.

Thanks Paqman!

---

