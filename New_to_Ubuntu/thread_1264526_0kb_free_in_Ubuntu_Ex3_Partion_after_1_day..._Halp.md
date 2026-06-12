---
title: "0kb free in Ubuntu Ex3 Partion after 1 day... Halp Plz!"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by Rossta on 2009-09-12
Hi guise.

I am a complete Linux n00b and installed Ubuntu for the first time 2 days ago.

everything was going swimmingly until yesterday when I tried to download some updates and was told that there was not enough free space to complete the installation.

I realise now that when I installed it to start with I should have adjusted the size of the Ex3 partition so that there was more space on it.

I then attempted to use GParted to change the size of my partitions, created the Live CD and booted from that which caused my old Puter to boot the program successfully but my monitor then displayed the message "VGA Mode not supported" and so I had to abandon the use of that.

I have tried to clear all space I can by uninstalling all non essential programs that were packaged with Ubuntu and still the disk is telling me that there is 0kB free.

What I now want to do is to find a way to manually adjust the size of the Ex3 partition, as it is installed on a 120GB hard drive with 30GB of free space on it (Defraged in Windows recently), without using GParted and also this needs to be in a format that will work on Windows XP as I have been forced to go back to my old crappy slow system to even post this question (Not enough room to store cookies even :( )

Any help gratefully appreciated...  Tnx in advance.

Ross.

---

### Post by jrothwell97 on 2009-09-12
I suggest you use the Ubuntu installation CD, as that also has gparted (it's under System/Administration/Partition Editor). You can use that to increase the size of your Ubuntu partition.

---

### Post by Rossta on 2009-09-12
> **jrothwell97 said:**
> I suggest you use the Ubuntu installation CD, as that also has gparted (it's under System/Administration/Partition Editor). You can use that to increase the size of your Ubuntu partition.

Thanks...

I will give that a go now and report back in a minute as to whether or not it worked.

---

### Post by Rossta on 2009-09-12
Ok then...  Finally got access to the Ubuntu installation CD again and that location you pointed me to does not exist on the disc.

When I view the disc I see "casper"+"dists"+"install"+"isolinux"+"pics"+"pool"+"preseed"+"ubuntu"  as the only file folders.

I Still need to find if there are any bootable programs that could be downloaded in WinXP that would allow me to adjust the size of Ex3 partitions.

so lets try again.

---

### Post by XCan on 2009-09-12
Don't view the disk, boot from it. :) Insert the disc, restart your computer, (set bios to start from your optical drive),  once the disc starts and you get a menu, select "try out Ubuntu without any changes".

---

### Post by ottosykora on 2009-09-12
> **Rossta said:**
> Ok then...  Finally got access to the Ubuntu installation CD again and that location you pointed me to does not exist on the disc.

When I view the disc I see "casper"+"dists"+"install"+"isolinux"+"pics"+"pool"+"preseed"+"ubuntu"  as the only file folders.

I Still need to find if there are any bootable programs that could be downloaded in WinXP that would allow me to adjust the size of Ex3 partitions.

so lets try again.

yes, but you are supposed to boot from that CD and select live ubuntu and from there you can run gparted (partition editor)

You can also download gparted CD or parted magic CD (google for)
, Those come in .iso and you can burn them to CD and boot from that.


very informative is also:

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by mike555 on 2009-09-12
You don't want to view the disc ... you want to restart your computer with the cd in and hopefully it will start ubuntu live session off the cd  .......

---

### Post by Rossta on 2009-09-12
oops...

like I said I'm a first time usr and so there are going to be some silly mistakes like that I will make.

I previously booted from that CD but did not relise that the "Try Ubuntu without any changes" option would alow me to do that.

Thanks.

Ok, Try the third...  Here goes

---

### Post by Rossta on 2009-09-12
Thanks for your help guys.

That worked!  :D  I was able to resize my partitions eventually.

Unfortunately I have now come across a new problem as I was unable to grow the size of the partition I wanted...  :(

see [http://ubuntuforums.org/showthread.php?t=1264797](http://ubuntuforums.org/showthread.php?t=1264797) for more info.

Thanks again.  You solved the problem that was in front of me...  Lets find that light at the end now.

Ross.

---

