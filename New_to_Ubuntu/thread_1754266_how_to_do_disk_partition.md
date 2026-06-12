---
title: "how to do disk partition?"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by Matrix01 on 2011-05-09
I am in installation process with HP Mini.

so..
clicked ubuntu installation icon on screen, followed steps, set time zone,  pick keyboard type....then 
Partitioning....?
clicked specify partition manually,,,,
click forward..

and here's list: dev / sda 1,2, 3, 4.....
dev/sda 1, 2, 3 are windows  

click 4th one......what's next
change , quit , revert???

---

### Post by jtarin on 2011-05-09
Change will make your selection Ubuntu partition. Why didn't you partition your disk before install?

---

### Post by Matrix01 on 2011-05-09
I tried to install Gparted before installing ubuntu, that did not work.

---

### Post by Matrix01 on 2011-05-09
I am installing ubuntu on HP mini.

I picked dev/ sda 4, click change, picked 'swap area'
clicked new partition table....

and this popped up  'you have selected an entire device to partition.  if you proceed with creating new partition table on device all current partitions will be removed"

what does that mean?

---

### Post by Buntumatic on 2011-05-09
Means if you have your wedding pictures on that drive you better stop and back them up, they won't be there if you proceed.

---

### Post by Matrix01 on 2011-05-09
I like to save Window 7 starter and other things in hard drive.
how do i install ubuntu?

---

### Post by 73ckn797 on 2011-05-09
You should have an option to install alongside another OS and dual boot between either.

---

### Post by Not unique on 2011-05-09
Sounds like you are in the advanced install bit is this correct?

---

### Post by calerano on 2011-05-09
> **Matrix01 said:**
> I am installing ubuntu on HP mini.

I picked dev/ sda 4, click change, picked 'swap area'
clicked new partition table....

and this popped up  'you have selected an entire device to partition.  if you proceed with creating new partition table on device all current partitions will be removed"

what does that mean?

It means that it will wipe out your HD and use the whole drive for Ubuntu.

What you need to do is select the option of " Install alongside with other OS" and everything will be fine as it will preserve your windows starter and all that is in that partition.
As you can see, partition in ubuntu is actually automatic.

---

### Post by ThatCoolGuy220 on 2011-05-09
Hmmm.

One must be EXT4 or EXT3 and mount point: /

the other one Swap  wich usually is smaller like 2GB or less 

Also you could choose any of the other options depending of what you want

---

### Post by Hedgehog1 on 2011-05-09
most of the newer HP installs have all four of the primary partition taken.  Because we are only allow 4 primary partitions on a disk Windows can boot from, we have to sacrifice a partition.

Normally I suggest making two sets of 'Windows Recovery' DVDs, and then using the 'recovery' partition as a place to install Ubuntu.

Here is an example of this (graphics are from an Ubuntu 10.10 install, but this works with 10.04 and 11.04 just fine).

[SIZE="3"]When all four primary partitions are taken (the HP install)[/SIZE]

[SIZE="4"][COLOR="DarkOrange"]First how it looks in Windows:[/COLOR][/SIZE]
[IMG]http://img859.imageshack.us/img859/9104/hp4partitions01.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]What it looks like in gparted off the LiveCD:[/COLOR][/SIZE]
[IMG]http://img859.imageshack.us/img859/8806/hp4partitions02.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Right click on sda3 and select 'Delete':[/COLOR][/SIZE]
[IMG]http://img856.imageshack.us/img856/2164/hp4partitions03.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the 'check' mark button to really make the change:[/COLOR][/SIZE]
[IMG]http://img190.imageshack.us/img190/1732/hp4partitions04.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Right Click, on empty area, select new and create extended sda3 (Press that check mark button again...):[/COLOR][/SIZE]
[IMG]http://img69.imageshack.us/img69/5967/hp4partitions05.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create your sda5 Ubuntu partition, leave a little room for swap later (Format this ext4 - and press that check mark button again.):[/COLOR][/SIZE]
[IMG]http://img863.imageshack.us/img863/4839/hp4partitions06.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create sda6 and make it swap space:[/COLOR][/SIZE]
[IMG]http://img855.imageshack.us/img855/3999/hp4partitions07.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the check mark button again[/COLOR][/SIZE]

---

### Post by Hedgehog1 on 2011-05-09
[SIZE="4"][COLOR="DarkOrange"]You are ready to install Ubuntu:[/COLOR][/SIZE]
[IMG]http://img864.imageshack.us/img864/2449/hp4partitions08d.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Select this during the install:[/COLOR][/SIZE]
[IMG]http://img705.imageshack.us/img705/2588/hp4partitions09.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]And you will get to here:[/COLOR][/SIZE]
[IMG]http://img849.imageshack.us/img849/9937/hp4partitions10.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]We will add some extra data to sda5 and sda6.  With sda5 highlighted, press the [CHANGE] button:[/COLOR][/SIZE]
[IMG]http://img861.imageshack.us/img861/5274/hp4partitions11.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]These settings prepare the partition to be exdt4, '/'.[/COLOR][/SIZE]
[SIZE="4"][COLOR="DarkOrange"]Repeat the steps for the swap area (This usually set itself up OK) :[/COLOR][/SIZE]
[IMG]http://img26.imageshack.us/img26/4934/hp4partitions12.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]You are ready to install.  Press [Install Now].[/COLOR][/SIZE]
[IMG]http://img857.imageshack.us/img857/6342/hp4partitions13.png[/IMG] 
[SIZE="4"][COLOR="DarkOrange"]This is what the drive looks like in the 'Disk Utility' in Ubuntu after the load is complete:[/COLOR][/SIZE]
[IMG]http://img852.imageshack.us/img852/3987/hp4partitions14.png[/IMG]  

***The Hedge***

:KS

---

### Post by uRock on 2011-05-10
Duplicate threads merged. Please do no multiple threads on the same topic.

Thanks,
uRock

---

### Post by jtarin on 2011-05-10
Hedgehog......excellent work on demo and the fact of pointing out this anomaly of newer HP's.

---

### Post by Matrix01 on 2011-05-10
thank u, hedgehog...i'm making a little progress.
 
I am on Gparted.
 
can i partition any of these?
my sda3 has2.06gib of unsed space, sda1 has 132.41mib, sda2 has red flag, sda4 has 92.56mib, and unallocated...

---

### Post by Matrix01 on 2011-05-10
where can i see that option "install alongside with other os"

---

### Post by Hedgehog1 on 2011-05-10
> **Matrix01 said:**
> where can i see that option "install alongside with other os"

In 11.04 it is called 'Something Else':

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

In 10.01 & 10.04 it is called 'Specify Partition Manually':

[IMG]http://img829.imageshack.us/img829/4196/02specifypartitons.png[/IMG]

***The Hedge***

:KS

[IMG]http://img97.imageshack.us/img97/8240/deathparionshishdd.png[/IMG]

---

### Post by audiomick on 2011-05-10
> **jtarin said:**
> ... this anomaly of newer HP's.

Just for the record, it is not just HP machines. I don't know off hand who else does it, but there is a tendency to think that no one could possibly want to change the install, so why not use up all the partitions...

---

### Post by jtarin on 2011-05-10
> **audiomick said:**
> Just for the record, it is not just HP machines. I don't know off hand who else does it, but there is a tendency to think that no one could possibly want to change the install, so why not use up all the partitions...
I think the general thinking is that "Nobody could possibly know about this except a bunch of geeks....so who cares?". 
Now with Linux entering more mainstream desktops that is not the case anymore. More people are becoming computer savvy and liking it. The control is being returned to them.

---

### Post by thinkren on 2011-05-10
Huge kudos to Hedgehog for such a detailed exposition.  I'm trying to dual boot a Presario CQ62-225NR running Windows 7 and facing the same problem.  I'll throw my 2 cents in so others can avoid the same mistakes I made.  I've not suceeded in geting Ubuntu installed yet and it is due to one of several differences from Hedgehog's method.  Rather than using Gparted from the get go, I tried to do as much as possible from within Windows.  First defraging C:, then shrinking it with "Disk Management", then deleting the RECOVERY partition with "Recovery Manager".  
After this point, I fired up the Gparted liveCD and discovered problems.  After deleting the RECOVERY partition, I should have 3 remaining primary partitions.  However, Gparted shows an extra partition had appeared. The partition labels had all shifted.  Gparted didn't like any of them, flagging them all with one error or another.  Details at my own thread:
 [http://ubuntuforums.org/showthread.php?t=1755070](http://ubuntuforums.org/showthread.php?t=1755070)

Despite this grave revelation from Gparted, Windows works just fine with indication of any problems at all.  It acts as if everything is exactly as it should be.  Unless there is some way to figure out what happened, wrestle away one of the primary partitions, and fix the rest, I'll have to try restoring the Clonezilla image I made right before I started fiddling around with all this.  My concern is with how Hedgehog's approach would affect the way existing apps will run on the computer.  For example, HP_TOOLS contains a BIOS flasher that defaults to reading/writing files from that partition when updating the computer's firmware.  How will having a completely different partition in front of it affect the way it operates under the hood.  I'm curios to hear from those who've been successful how their boot process ended up being configured.  Was it necessary to modify the hidden SYSTEM boot partition to work with GRUB?  If so, how?

---

### Post by Matrix01 on 2011-05-11
Is window 7 starter able to be saved onto external hard drive?
I do not have window 7 disc, it was installed on HP Mini.

so I can use entire hard drive for ubuntu...

---

### Post by thinkren on 2011-05-11
I have no experience with the starter edition.  But I would guess HP has installed some kind of recovery manager along with the stuff they typically add to Windows.  You can use it to create a set of recovery discs that can be used to restore the contents of the hard drive to brand-new factory-shipped condition.  However, any installed programs and generated data put on the hard drive since you bought it would not be restored.  For that, your best option would be to get something like Clonezilla liveCD and create/save a disk image of whatever is on your hard drive this very minute.  That disk image you may keep safe on an external hard drive for the day you want to use windows 7 starter again on your HP Mini.

---

### Post by Matrix01 on 2011-05-15
when either sda 1, 2, 3, or 4 will be partitioned with Gparted, 
are anythings in Hard drive going to be saved?

---

### Post by 73ckn797 on 2011-05-15
> **Matrix01 said:**
> when either sda 1, 2, 3, or 4 will be partitioned with Gparted, 
are anythings in Hard drive going to be saved?

When you repartition, all existing data will be destroyed on that partition. Any inter-relationship between the other partitions (Windows program file drive with, possibly, a separate data partition) will be affected. In other words, if one partition is referencing another for data, that information will be lost and the OS could completely quit working.

---

### Post by Matrix01 on 2011-05-17
how do u save exisiting OS, and other things when installing Ubuntu?

---

### Post by 73ckn797 on 2011-05-19
> **Matrix01 said:**
> how do u save exisiting OS, and other things when installing Ubuntu?
There are options presented to install along side another OS which will not remove anything. If they are to be on the same HD the installer will resize the partitions to make everything fit. If you are installing to a separate HD you can manually set that one up with the 4th option.

---

### Post by Matrix01 on 2011-08-28
did u back up your exsiting os before delete HP Resotre partition?


> **Hedgehog1 said:**
> most of the newer HP installs have all four of the primary partition taken.  Because we are only allow 4 primary partitions on a disk Windows can boot from, we have to sacrifice a partition.

Normally I suggest making two sets of 'Windows Recovery' DVDs, and then using the 'recovery' partition as a place to install Ubuntu.

Here is an example of this (graphics are from an Ubuntu 10.10 install, but this works with 10.04 and 11.04 just fine).

[SIZE="3"]When all four primary partitions are taken (the HP install)[/SIZE]

[SIZE="4"][COLOR="DarkOrange"]First how it looks in Windows:[/COLOR][/SIZE]
[IMG]http://img859.imageshack.us/img859/9104/hp4partitions01.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]What it looks like in gparted off the LiveCD:[/COLOR][/SIZE]
[IMG]http://img859.imageshack.us/img859/8806/hp4partitions02.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Right click on sda3 and select 'Delete':[/COLOR][/SIZE]
[IMG]http://img856.imageshack.us/img856/2164/hp4partitions03.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the 'check' mark button to really make the change:[/COLOR][/SIZE]
[IMG]http://img190.imageshack.us/img190/1732/hp4partitions04.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Right Click, on empty area, select new and create extended sda3 (Press that check mark button again...):[/COLOR][/SIZE]
[IMG]http://img69.imageshack.us/img69/5967/hp4partitions05.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create your sda5 Ubuntu partition, leave a little room for swap later (Format this ext4 - and press that check mark button again.):[/COLOR][/SIZE]
[IMG]http://img863.imageshack.us/img863/4839/hp4partitions06.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create sda6 and make it swap space:[/COLOR][/SIZE]
[IMG]http://img855.imageshack.us/img855/3999/hp4partitions07.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the check mark button again[/COLOR][/SIZE]

---

