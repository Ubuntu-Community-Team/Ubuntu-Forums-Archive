---
title: "Just upgraded to 9.04 - did it delete all my stuff??"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by Bakhman on 2009-06-18
Just an hour ago I installed the newest version via CD image (I had my reasons) from 8.10. However now I'm freaking out because I assumed all my documents/music/history would still be accessible! The menus and programs are still intact - but my actual files themselves seem to be gone.

I checked my HD space and it says it's 134 GB.. and it's a 160 GB HD so I'm assuming it has to on my internal somewhere. Anyone have any idea how to access it...? Eternally grateful.. especially for my Firefox history..:(

---

### Post by QIII on 2009-06-18
If you selected "Install" from the LiveCD and did not take care with your partitions, you may have installed over your important files.

What do you mean by "The menus and programs are still intact"?  Did you have particular programs you had installed that were not the standard fare?

---

### Post by lisati on 2009-06-18
There is a difference between doing a fresh install from CD (which can wipe out your data if you're not careful) and doing an upgrade (either from the command line, or from System->Administration->update manager, which usually leaves your data intact)

Are you able to locate your original folders via the "Places" menu?


edit: if you can't see your files in the specific folder under "places", have a look in Places->computer

---

### Post by QIII on 2009-06-18
And don't despair just yet.  There are tools for recovering lost partitions and the data in them.

I've used a couple of them to get data from other people's disks.  But, admittedly, I did so by plugging their disks into my network and using the tools from a working version of Ubuntu.

I am told that you can do similar things from the LiveCD on the drives on the computer it is running on.

lisati may have to carry you from here.

I'm off to slumberland.

---

### Post by Michael.Godawski on 2009-06-18
hi,

could you please post the output of these terminal commands:

```
df -h
sudo fdisk -l
```

Let's check what partitions you still have.

---

### Post by Bakhman on 2009-06-18
Absolutely -
for the first one:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G  2.4G  135G   2% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  104K  497M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  140K  497M   1% /dev
tmpfs                 497M   76K  497M   1% /dev/shm
lrm                   497M  2.4M  495M   1% /lib/modules/2.6.28-11-generic/volatile

--2nd one--

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19086   153308263+  83  Linux
/dev/sda2           19087       19457     2980057+   5  Extended
/dev/sda5           19087       19457     2980026   82  Linux swap / Solaris

---

The thing is, I did the liveCD install because the laptop froze during the upgrade, and had to turn it off manually. Since I thought 8.10 was "messed up" now (since it wasn't booting anymore) I forego the partitioning. *** What I mean by "menus intact" is that when I go to "places" and whatnot, the way I organized the tabs/folders are still the way they were before.

If it helps, I checked how much space is available, it says "Total: 144GB, Free: 142GB, Available: 132GB" which is strange because I coulda sworn I had a 160GB HD...

---

### Post by theozzlives on 2009-06-18
You don't have a seperate [/home partition]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") which is what you need to save your stuff during a fresh install. Do you have backups?

---

### Post by Bakhman on 2009-06-18
I did back up 90% of my docs/music, but didn't back up other stuff such as my Firefox history. I guess this means I'm screwed...? Based on how much HD space I have left it seems like some of it could be there but I did a search and found nothing.

---

