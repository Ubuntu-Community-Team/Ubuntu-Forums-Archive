---
title: "too many OS's - repartitioning question"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by benorner on 2009-05-04
Hi,
I upgraded to Jaunty about a week ago and everything has been great. However, I've since realized that I installed the 32bit version and even though I don't currently use any processor intensive applications, I want to have the ability to use the full potential of my machine (core2, 4G RAM) and it sounds like 64 is the only way to do so.

Long story short; I installed AMD64 this AM and I didn't set my partitons correctly. Now when I boot I have the option of the 64 or the 32 bit kernel or Vista and AMD64 has a rally small share of the disk space (~2GB). 

How can I repartition so that I get rid of the 32bit OS and minimize Vista's partition as much as possible.  

Also how could I have avoided this in the install process? I did the auto partition resizing. I'm obviously not clear on how to manually configure.

Thanks and sorry for the long post,
Ben

---

### Post by jbrown96 on 2009-05-04
Your problem is that the system is set to use the largest free space, meaning that it won't delete any data. Instead it resized your x86 partition. It should be trivially easy to fix. Boot from a liveCD. There is a partition editor in System--->Admin. Delete your x86 partition and then resize your AMD64 partition. You shouldn't have any problems because the partitions are adjacent. 

The only thing you need to watch out for is if the x86 partition is before the AMD64 partition. I doubt this would occur because the end of partition is usually free. If this is so, don't make any changes, and I can point you to the instructions to fix it.

---

### Post by Bartender on 2009-05-04
If it were me I'd download a copy of GParted LiveCD, burn the image to a CD, and use that tool for your partitioning work.  When it's set up the way you want, then go back to the install CD.
It takes a bit of time to get familiar with the GPArted GUI.  Most important thing - "apply" each change as you go.  Don't let several tasks stack up then do them all at once!
I'm not impressed with the partitioner that comes with the install CD.  It doesn't even distinguish between a primary and extended partition.  Well, maybe it does if you know how to ask nicely, but the default screen does not identify an extended partition.  That's just goofy.
GParted LiveCD is the way to go AFAIC
NOTE:  There's always a danger in resizing the existing Windows partition.  From what I've read on these forums, you're better off to resize the Vista partition using the Vista partitioner.  It's somewhere in Computer Management.  Resize Vista first, because once you wipe Ubuntu the MBR will be screwed up and you probably will not be able to get back into Vista until you 1) repair the MBR, or 2) reinstall Ubuntu, which will reinstall GRUB to the MBR.
How to avoid this in the future?  Practice with a spare HDD maybe.  Doing it a few times is the best teacher.  I would probably 1) resize Vista using the Vista partitioner, 2) use Gparted LiveCD to create an extended partition out of the rest of the HDD.  Inside that extended partition create a logical ext3 or ext4 partition for /, a logical partition for swap, and a logical ext3 or ext4 partition for /home.  In GParted, you create the swap partition as "swap", but you're not defining the / and /home partitions as such.  You're just making the partitions.

Then I'd start up the Ubuntu install CD, go into "Manual" on the partition page, and pick the first ext partition.  I'd edit that partition.  Tell the installer to "Format" the partition, and mount it as /.  The swap partition I'd leave alone.  I'd edit the second ext4 partition.  Mount the partition as /home.  Then finish the install.  you shouldn't have to format the /home partition, but if Ubuntu wants to let it format as ext3 or 4, whichever one you want.  Might as well go with 4, eh?

I'd end up with the Ubuntu OS installed to the / partition.  All of my personal data, everything in "Home" folder, will be stored on the separate /home partition.  This makes it easier to update the OS six months from now.  

One thing to watch out for - if you wipe the OS partition and reinstall with the latest version of Ubuntu later on, be sure to use the same username and password as before.  And be sure to mount /home to the correct partition again.  And be sure to tell the installer NOT to format the /home partition.  If you use a different username, Ubuntu will create a second /home folder inside the / partition, which defeats the whole purpose of creating the separate /home partition in the first place.  If you don't make sure to tell the installer NOT to format when you mount the partition as /home, it'll wipe your personal data.

---

### Post by benorner on 2009-05-04
[Here's]("http://co114w.col114.mail.live.com/att/GetAttachment.aspx?tnail=0&messageId=401e76ab-8706-455b-8b13-c69aa6a88fdf&Aux=14|0|8CB9ADFE1FFAA20|") a screen shot of the live disk partition editor. 

I think I will try to edit the Vista partition first and then download GParted as recommended - can I just find that image file in the repos? 

Any advice on how to find Vista partition editor? 

Thanks for the rapid responses.

Ben

---

### Post by jbrown96 on 2009-05-04
I couldn't get that screenshot to work. It directed me to Windows Live login page. 

You will need to download the Gparted image from [here]("http://gparted.sourceforge.net/livecd.php") then burn it to a disk or install on a flash drive. 

I don't have any idea about the Vista tool. If you decide to resize Vista from Gparted, you should defrag with Vista first.

A screenshot from gparted and the output of ```
sudo fdisk -l
``` would really help determine exactly what you need to do. You should be able to add the screen shot using the add file option when you are typing a post.

---

### Post by egalvan on 2009-05-04
> **Bartender said:**
> ...download ... GParted LiveCD, burn to CD, and use ...for your partitioning work.
 When it's set up the way you want, go back to the install CD.
It takes a bit of time to get familiar with the GPArted GUI.
  Most important thing - "apply" each change as you go.  Don't let several tasks stack up then do them all at once!

**I'm not impressed with the partitioner that comes with the install CD.**
 ** It doesn't even distinguish between a primary and extended partition.**
 Well, maybe it does **if you know how to ask nicely**, but the default screen does not identify an extended partition.  That's just goofy.
GParted LiveCD is the way to go AFAIC{/quote]


Well, I agree partially with this...

I also use, and recommend, a separate partitioning tool.
GParted LiveCD is nice.
I use PartedMagic LiveCD, a rather full-featured distro in it's own right.

But these all use the  same gparted engine.
The only difference (if there is one) is the exact version used.
Distros (such as Ubuntu) tend to have slightly older versions.
The partitioning-specific tools tend to have the most up-to-date versions.

As for  not distinguishing between primary and secondary partitions,
I have never had this problem,
going back to whatever gparted version Feisty used...
Primary and extended had different colors...
And I never changed any settings (or asked nicely) to get this... :)

> 
NOTE:  There's always a danger in resizing the existing Windows partition. , **you're better off to resize the Vista partition using the Vista partitioner.**  It's somewhere in Computer Management.  Resize Vista first, because once you wipe Ubuntu the MBR will be screwed up and you probably will not be able to get back into Vista until you 1) repair the MBR, or 2) reinstall Ubuntu, which will reinstall GRUB to the MBR.

Again agree... use Vista's own tools to do Vista partition work.

But there is no need to re-install Ubuntu to re-install GRUB.
GRUB can  be installed/re-installed by itself.

meifera and caljohnsmith have excellent guides to this.

> 
How to avoid this in the future?  Practice with a spare HDD maybe.
**Doing it a few times is the best teacher.**

Excellent advice!

>   I would probably
 1) resize Vista using the Vista partitioner,
 2) use Gparted LiveCD to create an extended partition out of the rest of the HDD.
  Inside that extended partition create a logical ext3 or ext4 partition for /, a logical partition for swap, and a logical ext3 or ext4 partition for /home.
  In GParted, you create the swap partition as "swap", but you're not defining the / and /home partitions as such.  You're just making the partitions.

Then I'd start up the Ubuntu install CD, go into "Manual" on the partition page, and pick the first ext partition.  I'd edit that partition.  Tell the installer to "Format" the partition, and mount it as /.  The swap partition I'd leave alone.  I'd edit the second ext4 partition.  Mount the partition as /home.  Then finish the install.  you shouldn't have to format the /home partition, but if Ubuntu wants to let it format as ext3 or 4, whichever one you want.  Might as well go with 4, eh?

I'd end up with the Ubuntu OS installed to the / partition.  All of my personal data, everything in "Home" folder, will be stored on the separate /home partition.  This makes it easier to update the OS six months from now.  

One thing to watch out for - if you wipe the OS partition and reinstall with the latest version of Ubuntu later on, be sure to use the same username and password as before.  And be sure to mount /home to the correct partition again.  And be sure to tell the installer NOT to format the /home partition.  If you use a different username, Ubuntu will create a second /home folder inside the / partition, which defeats the whole purpose of creating the separate /home partition in the first place.  If you don't make sure to tell the installer NOT to format when you mount the partition as /home, it'll wipe your personal data.

---

### Post by benorner on 2009-05-04
Thanks for all of the advice.

Unfortunately things have taken a turn for the worse...

When I tried to reboot into vista to investigate the partition tool I got a huge ERROR across the screen and was told that 'Windows could not access recovery information. I forced a restart and tried to boot into Jaunty and I get the message, 'GRUB loading, please wait... Error 17.' So I'm currently running off the live CD. 

I've tried to attach the screen shot from the live CD partition tool again, hopefully it'll work.

---

### Post by benorner on 2009-05-04
attached is a shot of the output from fdisk -lu and fdisk -d

(how do I copy and paste code into my posts?)

---

### Post by benorner on 2009-05-04
update:

got past the GRUB error 17 and am now able to boot into Jaunty (weeee). I'll read up a little more about GParted before screwing anything else up.

---

### Post by jbrown96 on 2009-05-04
To paste code, there is a # symbol on the toolbar above where you type. Just put the code in between the two ```
 
``` tags.


I hope I understand this right. The 64-bit version is the small partition right? And that's what you want to make bigger? 
If so, do the following:

1) Boot the live cd
2) Backup any important documents just to be safe. Vista partition looks like a good location.
2) Go into the partition editor. 
3) Delete /dev/sda6 and apply the change.
4) Highlight /dev/sda7 and you should get an option to resize the partition. Make it occupy all the preceding space and apply.
5) Once that finishes, we can clean up your swap. You have two swap partitions, which isn't necessary.

You have two options with swap. You can some of it to your ext3 partition (64-bit) or you can combine them to make one large swap file. 

Either way do the following.
1) ```
sudo swapoff -a
```
2) You will probably have to reload the partition editor, so it sees that they are unmounted (no keys next to the partitions).
3) Resize the partition however you want. You can either resize the ext3 or swap, depending on how you want to use your disk space. 

The first enlargement is going to take a while. If you think about changing it all to one big partition, then the data is going to be in the middle (actually towards the end since they have such different sizes). However, it will move all that data to the beginning of the partition. The consequence is that you will need to read ~2GB from the middle and save that same ~2GB at the beginning. I imagine about 20-30 minutes.

---

### Post by benorner on 2009-05-05
Right, AMD64 is the small partition (sda7). 
So sda6 is 32-bit jaunty and that's what you're suggesting I delete and resize sda7 to take up that space, correct? 

Sounds good so far. Remaining questions before I do so: 
You refered to ext3 as my 64-bit jaunty - is ext3 the same as sda7 in my case? 

Also concerning cleaning up the swap - is there any particular reason why I'd want a larger swap. What function does swap serve exactly. I've heard the argument that swap is less crucial on newer machines with more storage.

---

### Post by Bartender on 2009-05-05
ben - 
ext3 refers to the underlying file system.  I don't really understand file systems, but old Windows operating systems used FAT16, then FAT32, then Microsoft moved on to NTFS in Windows 2000.
Linux has also adopted new file systems over the years.  We're in the process of moving away from ext3 and adopting ext4.

So I don't want you to get confused.  ext3 refers to a file system.

sda7 refers to a place.  sda7 refers to a partition on your HDD.  sda7 is Linux terminology.  Linux would call that partition sda7 whether it was FAT, NTFS, or ext.  

I've kind of gotten mixed up on who's told you what to do.  As jbrown said, you don't need two swaps.

Before I say anymore, do you know what sda5 is?  it's formatted NTFS, so it's probably some sort of utility that was installed by the PC manufacturer.
Also, sda1 is a primary NTFS partition.  Have you burned your Windows recovery discs?  You really should instead of relying on the recovery partition.  Some recovery utilities will wipe the recovery partition after you use the recovery discs.  That frees up the space on the HDD.

If you don't mind reinstalling the 64 bit AMD version, I'd suggest using a GParted LiveCD to delete sda 6, 7, 8, and 9.  You don't need a swap bigger than about 2GB.  After deleting all those, I would create a 2GB partition and format it as swap.  I'd use the GParted CD to do that.  The Ubuntu installer will recognize the swap partition and leave it alone.  Well, it does if you use the "Manual" option.  Probably overwrites it if you use Guided.
Then you could either get out of GPArted and pop in your Ubuntu disc or continue using GParted to create specific partitions as we talked about earlier.

EDIT: Swap is the same as virtual memory in Windows.  If you overwhelm your physical RAM Linux will use swap.  Some folks say that with 2GB or more of RAM it's unlikely you'll ever use swap.  On the other hand, your average HDD is so huge these days who's gonna notice 2 GB?  I always set aside 2 GB for RAM even if it's a waste.

---

### Post by benorner on 2009-05-05
Thanks for the many clarifications, Bartender. Seems like removing sda's 6 and up and doing a clean install might be best. 

And you're saying that I should create my swap while I'm in GParted? - Could I not just do that in the install process?  

I think I'm ready to tackle this, but not tonight. Maybe in the morning. I haven't tried to boot into vista to shrink that partition yet - is there a minimum amount of space I should leave to windows? I plan to use it as little as is necessary.

---

### Post by maclarke on 2009-06-11
I hope I'm not too late. I want to shrink my XP partition and make the extra space available to Ubuntu.
Can I do this in XP's Disk administration, or, follow a variation of the directions posted here:
Back up files in both partitions. and
Use GParted to resize the Ubuntu partitions.

---

