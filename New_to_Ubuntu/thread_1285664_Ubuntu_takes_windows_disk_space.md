---
title: "Ubuntu takes windows disk space"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by blackshadeV on 2009-10-08
Hello i have a problem, I am new and I don't know what to do.
I have a notebook installed with Windows vista (first) and Ubuntu 9.04 (Second)
Everything went alright but when ubuntu updated, I have got an extra linux in my grub boot screen (kernal0.4-11... and kernal04-15...) 15 is the new one, but when I check my windows disk space I miss more the 10GB on my disk. 

Now i have installed some things on Ubuntu (the kernal-15) and all the things i habe installed is despairing from my windows disk. 

I have installed Windows first, shrunk the patition so i had 30GB for Ubuntu and installed Ubuntu (with the "Use all the free space.. etc" option (the third option from above)
Also I have tried the option "install Ubuntu next to windows and made 20 GB free, but with the update it looks like he install Linux on my windows disk.

Can someone please help me please?

---

### Post by mapes12 on 2009-10-08
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by nhasian on 2009-10-08
if ubuntu is using your windows disk space, you must have installed it inside windows (using wubi) instead of installing it to a separate partition.  in ubuntu can you give us the output of the following terminal commands:

```
sudo fdisk -l
```

```
df -h
```

---

### Post by 3rdalbum on 2009-10-08
When your Linux kernel updates, it adds the new kernel to the boot menu alongside the old kernel. The new kernel takes up around 50mb of space on your Ubuntu partition, or 50mb of space on the Ubuntu image if you installed using Wubi.

In other words, the missing 10gb on the Windows partition is more likely to be caused by making a mistake when partitioning, or maybe a Windows program hasn't deleted its temporary files.

---

### Post by random turnip on 2009-10-08
10GB suddenly disappearing is nothing special in Vista.  So many temporary files.

Anyway, to me it sounds like you installed a dual boot, so when it loads you will see Ubuntu (numerous times for multiple kernels) then Vista and recovery at the bottom, right?

When you make a dual boot and you chose the partitions, whatever you give to Ubuntu it has to take away from Vista.

---

### Post by blackshadeV on 2009-10-08
> **nhasian said:**
> if ubuntu is using your windows disk space, you must have installed it inside windows (using wubi) instead of installing it to a separate partition.  in ubuntu can you give us the output of the following terminal commands:

```
sudo fdisk -l
``````
df -h
```
I am dutch so i hope you can you can get the information you need from the next copies:


first one:
```
Schijf /dev/sda: 160.0 GB, 160041885696 bytes
255 koppen, 63 sectoren/spoor, 19457 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0xc206c206

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1       15588   125202428    7  HPFS/NTFS
/dev/sda2           15589       19457    31077742+   5  Uitgebreid
/dev/sda5           15589       19292    29752348+  83  Linux
/dev/sda6           19293       19457     1325331   82  Linux wisselgeheugen

```second:
```
Bestandssysteem            Grtte   Gebr Besch Geb% Aangekoppeld op
/dev/sda5              28G  3,4G   24G  13% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  100K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  156K 1007M   1% /dev
tmpfs                1007M  480K 1006M   1% /dev/shm
lrm                  1007M  2,2M 1005M   1% /lib/modules/2.6.28-15-generic/volatile

```
Then, is it really a good idea to install Ubuntu while on windows? And would that clear this problem? If thats the case, where can I get that Wubby installer and what else do I need? any tutorials yoe recommand?

(I installed this version also with a tutorial.. well more then one because the most are the same, so i didn expact these kind of problems..)

I see my vista at the bottom yes, and 6 times Linux, (2x Linux kernal , recoversy en mem test)

Temp files of (was 10g..) now 20gb.. On a just installed computer.. Nah no chance.

And yes i think it is a patitioning failt. I think he don't saw Ubuntu on the C: when he started to update and made a other patition on the C:/ 
But i can't find anywhere where I can config the place he check updates and install them

thanks,
Blackshade

---

### Post by XCan on 2009-10-08
From what I can see only /dev/sda5 would be written to when you update your kernel, and not your Vista partition.

Your problem thus lies with Vista and its so called shadow copies, or whatever they decided to call it. These Vista backups will by default take up 15% of all every drive. [http://en.wikipedia.org/wiki/Shadow_Copy](http://en.wikipedia.org/wiki/Shadow_Copy)

---

### Post by blackshadeV on 2009-10-08
But the /dev/sda1 is a NTFS, is that correct?

And if the problem is that shadow copy thingy, how to shut it down? Because its just really annoying that every time i install something on Ubuntu it goes of my C: disk space.

Edit:
well i have turned it off but I just can't believe it took 10GB of space when i updated Ubuntu on a other patition.

Anyone other suggestions what it could be? (and how i get my 10GB back (the amount is token back to 10gb of missing space so the shadow copie was part of al that)

---

### Post by XCan on 2009-10-08
The reason why you can't believe it is because it didn't happen. If your Vista disk isn't mounted on Ubuntu, it can't be written to. You'll have to pull some serious stunt to manage that. :p 

I dunno about the shadow copy, but I wonder if it really cleans out the old shadow copies when you turn it off. You may have to go to some hidden folder in Vista and get rid of them manually.

---

### Post by lisati on 2009-10-08
> **random turnip said:**
> 10GB suddenly disappearing is nothing special in Vista.  So many temporary files.
Stranger things have happened. I recently installed some new software on my Vista partition, and several gigabytes of disk spaces were mysteriously freed up. I'd never had any version of that particular software installed on that machine before, so a newer version taking up less room than an old version isn't a valid explanation.

---

### Post by The Cog on 2009-10-08
I'll just weigh in and support what others are saying. You are not mounting the NTFS partition into Ubuntu so there is no way it can use disk space on that partition. If 10G of space has disappeared from your Vista partition, it is coincidence that it happened at around the time that you did an Ubuntu update. And it is entirely a Vista issue.

It might help you to find out where it's gone if you mount the NTFS partition into Ubuntu and run a disk space analysis on it, but unless you know what to expect then you won't be able to spot anything odd that way. You might be better off using windows utilities (I presume such utilities exist) to find out where it's gone.

---

### Post by Zoot7 on 2009-10-08
Try running the disk clean-up in Vista. Vista has been known to randomly gobble up large chunks of your hard drive without your consent.
Chances are the problem isn't any fault of Ubuntu. :)

---

### Post by blackshadeV on 2009-10-09
Okey, and now that shadow clone is out of the way Windows doesn't lose anymore space when i install things on Ubunbtu.

So i think my problem is solved, (expect for the 10gb but i can life with that if it space isn' t going to grow)

Thanks for helping everyone

---

