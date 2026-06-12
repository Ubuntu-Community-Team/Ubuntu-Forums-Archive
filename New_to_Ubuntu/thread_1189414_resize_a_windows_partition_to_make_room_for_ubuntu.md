---
title: "resize a windows partition to make room for ubuntu?"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by arikshtiv on 2009-06-16
Hello,
My windows computer has been infected by a horrible virus, something that makes  it look like a blue screen.

The problem is that my hard drive is completely partitioned and only 1gb are free.

the partitions are like:
100gb - 60gb free
50gb - 20gb free

is there a way to make room for a ubuntu partition that will allow me to transfer batches of files and then resize the ubuntu partition as more space gets free without deleting those files?

Thanks

---

### Post by Shibblet on 2009-06-16
> **arikshtiv said:**
> Hello,
My windows computer has been infected by a horrible virus, something that makes  it look like a blue screen.

The problem is that my hard drive is completely partitioned and only 1gb are free.

the partitions are like:
100gb - 60gb free
50gb - 20gb free

is there a way to make room for a ubuntu partition that will allow me to transfer batches of files and then resize the ubuntu partition as more space gets free without deleting those files?

Thanks

Hey!  I actually helped a friend do this to his Windows machine the other day.  Drop in a LiveCD version of Ubuntu, run "Try Ubuntu without any changes to my computer".  Get into your Desktop environment, then backup all of the files you need to backup.

After you've backed everything up, re-install Windows with a newly formatted HD.  Go into windows and set your partitions, then give a little extra space for a Ubuntu install.  Run the CD again, and install to your new partition.  You've just created a dual-boot machine!

---

### Post by swisstone198 on 2009-06-16
Vista or XP?

---

### Post by arikshtiv on 2009-06-16
I don't have anything to backup to and not in the near future.

and I'm using windows XP ntfs.

---

### Post by Shibblet on 2009-06-16
> **arikshtiv said:**
> I don't have anything to backup to and not in the near future.

and I'm using windows XP ntfs.

Then just clean wipe the HDD.  You can do this from booting off of your Windows XP CD.  

If you want to run Ubuntu exclusively, you can do the same off of a LiveCD as well.

---

### Post by arikshtiv on 2009-06-16
But I said I wan't to keep all my data.

---

### Post by jniebles on 2009-06-16
I think you are saying you don't have an extra disk where to place your backed up data?

---

### Post by arikshtiv on 2009-06-16
yes, I searched for my question and all I could find is suggestions to resize an ntfs partition to make room for an ubuntu one.

and I don't know how.

---

### Post by Shibblet on 2009-06-16
> **arikshtiv said:**
> I don't have anything to backup to and not in the near future.

and I'm using windows XP ntfs.

I'm confused.  You don't have anything to backup, but still need space to back stuff up.

---

### Post by abhiroopb on 2009-06-16
What he's saying is that he doesn't want to "backup" but he does want to keep his data. More simply, he does not have any space to backup to.

I'm a little confused by your partitions.

Whats on each partition? Which one has windows and which one has data?

---

### Post by arikshtiv on 2009-06-16
the smaller one has windows, but both have data.

---

### Post by abhiroopb on 2009-06-16
Here is what I suggest...

1. Boot into Ubuntu with a LiveCD
2. Open up your two partitions (they should be visible on the desktop)
3. Copy the data from your smaller partition to the larger one. Don't bother with the windows files, just copy the data you want to save.
4. Make sure that the small partition contains NOTHING that you want.
5. Go to: system>administration>partition editor
6. Select the small partition
7. Click DELETE
8. Click Apply

Now your smaller partition will be blank and you can install ubuntu on it.

NB1: be careful when copying your data, make sure you copy over all of it.
NB2: this will delete your windows installation completely, and everything you have in the small partition.

BE CAREFUL!

I'm off to bed, but let me know how it works out!

---

### Post by arikshtiv on 2009-06-16
The partitions don't show up on desktop, and when I try to go into one of them I get "Cannot mount volume":

> $LogFile indicated unclean shutdown (0,0) Faild to mount '/dev/sda2': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: if you have windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown windows cleanly. Choice 2: if you don't have Windows then you can use the 'force' option for your own responsibility. For exmple type on the command line: mount -t ntfs-3g /dev/sda2 /media/disk -o force OR add the option to the relevant row in the /etc/fstab file: /dev/sda2 /media/disk ntfs-3g force 0 0

and good night.

---

### Post by Sathallrin on 2009-06-16
use the force option like the error message suggests.

---

### Post by abhiroopb on 2009-06-17
in a terminal put in:

sudo mount -t ntfs-3g /dev/sda2 /media/disk -o force

to mount the partition.

---

### Post by super kim on 2009-06-17
if you have 5 gb spare then [http://wubi-installer.org/](http://wubi-installer.org/) install ubuntu with wubi...
then boot up ubuntu, copy all your files over to the big partition...
then check this site [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) follow the instructions to make or resize a partition to make room for ubuntu ubuntu

---

### Post by abhiroopb on 2009-06-17
> **super kim said:**
> if you have 5 gb spare then [http://wubi-installer.org/](http://wubi-installer.org/) install ubuntu with wubi...
then boot up ubuntu, copy all your files over to the big partition...
then check this site [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) follow the instructions to make or resize a partition to make room for ubuntu ubuntu

Not to be rude, but from what I understand the OP cannot actually boot into Windows, so WUBI (as far as I know) would be useless.

---

### Post by super kim on 2009-06-17
> **abhiroopb said:**
> Not to be rude, but from what I understand the OP cannot actually boot into Windows, so WUBI (as far as I know) would be useless.

no no your quite right to point that out. i'm not sure but i thought wubi was on the CD, still tho i dont think it will work without windows.

---

### Post by Bölvaður on 2009-06-17
> **abhiroopb said:**
> Not to be rude, but from what I understand the OP cannot actually boot into Windows, so WUBI (as far as I know) would be useless.

Actually that is not a bad idea to use WUBI. The OP does not state that Windows is utterly unusable so logging into Windows and install Ubuntu with wubi could be the magic trick. As he will keep all his files without doing anything and he will be able to use Ubuntu.

If that does not work then you are kind of screwed. I would not recommend anyone not experienced with partitions to partition their harddisk with out backing their data first. But if you must, then here is...

**...WHAT YOU SHOULD DO:**

1. Free up the smaller partition of all personal data.
From the live cd move all the data from the small one to the big one.
To do that you need to mount them (Places &#8594; Removable Media &#8594; your partitions*) as you already have (might need to be forced if your Windows was incorrectly shut down while connected to it).
If the unlikely event that you do not have permissions to move the files:
Press Alt+F2 and type : **gksu nautilus **and click the partitions you mounted on the left of the window that will pop up. Now you will have all the permissions to move any data from anyplace to anywhere.

[SIZE=1]*note that between Places and Removable Media and your partition in my text there are supposed to be arrows that cannot be seen without up to date operating systems using unicode[/SIZE]

2. Make partitions for Ubuntu
You will need atleast 2 partitions. 1 that Ubuntu is placed on, and 1 for swap (for swapping/paging... like the page file in windows).
Go: System &#8594; Administration &#8594; Partition Manager
Delete the small partition and create a small swap partition, if you got a laptop then it should be equal in size to your ram. If you have a desktop computer then 500mb should be way more than enough. The file system for that partition is named swap.
The rest will be Ubuntu and the file system should be either ext3 or ext4.

3. Installing Ubuntu
When installing you will be asked about your partitions, make sure to click MANUAL or else all your data might be destroyed.
Then you will need to link your new partition to where Ubuntu will be installed. So you double click or right click the small ext3 partition and set mount point to / (found in the drop down list) and make sure the file system is set to ext3 or ext4. I assume it doesnt matter if you click format or not.
You also might need to connect to your data partition (see part 4 for results of each option). You can choose not to do anything and manually mount it when you need. Or you can make Ubuntu auto mount it by setting the mount point to something like /data (you will need to create that one your self, it is not in the dropdown list as... it isn't part of the system). But **BE CAREFUL**, make sure not to select the wrong file system, it has to be the same one as before and **DO NOT CLICK FORMAT**.


4. Accessing your data
Now you got Ubuntu installed and need your data.
If you did not make a mount point you will find your data partition under Places and be named after the size of your partition. Just click it to mount it and then click the icon that will appear on your desktop. You might need to insert your password to be allowed to mount it.

If you made a mount point open the file manager and browse your way to /data (go to top level and then find the directory named data) there is all your stuff.
You might want to bookmark this place for ease of use.

---

### Post by arikshtiv on 2009-06-19
Thanks to all, especially to abhiroopb.

And actually I deleted the bigger partition(moved all needed data) most of it had only windows games and programs.

And I tried using WUBI but all of widows was corrupted.

---

### Post by dyess002 on 2009-06-19
You have to use Gparted and then you will have to create a 60 gig partition then use the 60 gig to back up your data, You will still have your c:. after you backup your data format c: and then reinstall windows and then move the data back on your computer. After you move everything back to your c: then reformat the 60 Gig to a EXT4 and then you will have a partition for your Ubuntu. You do need to consider a SWAP Partition, at least 2 gig.

---

### Post by abhiroopb on 2009-06-19
> **arikshtiv said:**
> Thanks to all, especially to abhiroopb.

And actually I deleted the bigger partition(moved all needed data) most of it had only windows games and programs.

And I tried using WUBI but all of widows was corrupted.

Glad to be of help

---

