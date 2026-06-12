---
title: "A Good Program to Back-Up the System"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by kronomia on 2009-11-18
Dear Ubuntu User,

Hello! Please, What is the best way to back-up data under Ubuntu 9.04?

I am using now "Simple Backup Suite 0.10.4". It is always reliable right? or there are some other alternatives or advanced back-up programs that i can use?

Thanks and regards

---

### Post by Dapilot1 on 2009-11-18
Never used that, but I like back in time. Its the best IMHO and its in the repos.

---

### Post by ajgreeny on 2009-11-18
Depending on what files you want to backup and whether or not it needs to be incrementally backed up, I suggest you look at rsync, a terminal application already in ubuntu, and all linux distros, I think.  If you want a GUI for it there is grsync, not quite as many options as plain rsync, but good enough for back-ups.

I use it all the time without problem to backup my home to an external hard drive which I have formatted to ext3.  Bacups to a vfat drive with (g)rsync are not totally successful, because although most files will transfer safely, no permissions are retained, as fat32 does not recognise linux permissions.

---

### Post by Sir Jasper on 2009-11-18
Hi,

I found Grsync took about 7 times longer than Simple Backup which is a pity since generally I liked it. Though I was not aware of the tip to use EXT rather than FAT so I may try it again.

My regards

---

### Post by ajgreeny on 2009-11-18
> **Sir Jasper said:**
> Hi,

I found Grsync took about 7 times longer than Simple Backup which is a pity since generally I liked it. Though I was not aware of the tip to use EXT rather than FAT so I may try it again.

My regards
Perhaps the time difference was a result of SBU not doing incremental backups but just copying everything you ask it to, and keeping lots of versions of the same thing.  I did look at it a long time ago, but it was no good for my large home backup on the external drive I had, as there was only room for a max of 4 versions at any time.  Grsync checks each file and only transfers it if it has changed.

---

### Post by HermanAB on 2009-11-18
Hmm, on Linux, most backup utilities suck.  The problem is that backup utilities are usually written by newcomers to Linux who haven't discovered rsync yet...

So, read the rsync man page and do it yourself.  With rsync, making a backup is a one-liner.

---

### Post by DGortze380 on 2009-11-18
> **HermanAB said:**
> Hmm, on Linux, most backup utilities suck.  The problem is that backup utilities are usually written by newcomers to Linux who haven't discovered rsync yet...

So, read the rsync man page and do it yourself.  With rsync, making a backup is a one-liner.

x2

---

### Post by sgosnell on 2009-11-18
I like remastersys.  It will make a .iso of your system, which is easy to restore.  It's probably not the best for just doing an incremental backup of your user data, but if you want a full backup of the entire system, it's very good.

---

### Post by kronomia on 2009-11-18
Thanks a lot for all your help! Indeed, rsync is the one that i was searching for. It provides me with all the functionalities that i want in addition it is simple to use especially after reading the man page. Thanks for your help. :D

*remastersys is also a good choice i think, but i will stick with rsync for the moment. :KS

My Regards,

---

### Post by beardie on 2009-11-18
grsync is working well for me.

---

### Post by sgosnell on 2009-11-18
Again, it depends on what you want to do.  For a full backup of your entire system, remastersys is a good choice.  For a regular backup of your user data files, rsync is obviously better.  I use both, depending on what I want to do.  A hammer works for driving a screw, but a screwdriver is better.  The screwdriver is useless for nails, though.

---

### Post by spikyjt on 2009-11-18
dirvish is a wicked script that makes good use of rsync and does incremental backups. It's well easy to configure and comes with a search and restore utility. It's particularly good for backing up lots of machines to one backup server, as I do on my network.

---

### Post by benerivo on 2009-11-18
I've found luckybackup and flyback both easy to use.

---

