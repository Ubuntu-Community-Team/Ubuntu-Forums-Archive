---
title: "32gb USB thumb drive"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by ariascarlos1990 on 2009-11-17
Hey every one I have this 32gb thumb drive that I had working I tried to add a 7gb file to it on XP and I got an error saying that something about the file I tried to add was lost or something. anyways I recently tried to format it to NTFS from XP hopping to fix it. but, it said it was unable to format it. So I decided to just switch it back to FAT32 and I got the same error. 

Now im here trying to format this usb thumb drive through ubuntu with no luck I've been searching for the past 4 hours and can't seem to figure it out. It comes up in gparted but, at unallocated...I am completely stump. I would greatly appreciate you're guys-es help on this one.

Thanks. 

P.S. I also tried Gnome format but, it freezes up after I press the are you sure you want to format button.

---

### Post by NickJones on 2009-11-18
Try going System, Administration and Disk Utility.

---

### Post by ariascarlos1990 on 2009-11-18
ok now what?

---

### Post by ariascarlos1990 on 2009-11-18
bump. this is giving me a headache.

---

### Post by NickJones on 2009-11-18
Click on your drive, click un-mount (if mounted) and then check the file system or erase it.

---

### Post by ariascarlos1990 on 2009-11-18
I clicked erase and nothing seemed to happen. It doesn't show unmount or mount.

now what?

---

### Post by ariascarlos1990 on 2009-11-18
bump.

---

### Post by RandomP on 2009-11-18
If you can view what's in it in Ubuntu, then you have it mounted. 
Right click on the device, and select unmount volume.

---

### Post by ariascarlos1990 on 2009-11-18
Its not showing up on the desktop. but, it does come up in disk utility, gparted, and gnome format. But, it seems that every thing I do to it in disk utility does nothing. gparted does the same thing. and gnome format freezes.

I really need it working for tomorrow.

---

### Post by ariascarlos1990 on 2009-11-18
bump.

---

### Post by wilee-nilee on 2009-11-18
Have you tried to in XP click on computer then right click on the drive and click format.

---

### Post by ariascarlos1990 on 2009-11-18
yes. It says it was unable to format.

---

### Post by 3rdalbum on 2009-11-18
What about if you try using "cfdisk" on the command-line? You might have more luck there.

A Fat32 filesystem cannot hold any files bigger than 4GiB, that's why your 7 GiB file wouldn't copy.

---

### Post by emigrant on 2009-11-18
Hey,
I had a similar issue with a 64 gb kingston. And finally i had to throw it since it was not 'genuine' and thus couldnt claim warranty.  Is that same with u?

---

### Post by ariascarlos1990 on 2009-11-18
> **3rdalbum said:**
> What about if you try using "cfdisk" on the command-line? You might have more luck there.

A Fat32 filesystem cannot hold any files bigger than 4GiB, that's why your 7 GiB file wouldn't copy.

tried the "cfdisk" heres what came up....

FATAL ERROR: Cannot open disk drive
                          Press any key to exit cfdisk

what file system can hold more than 7 GIB then?

Thanks.

---

### Post by ariascarlos1990 on 2009-11-18
> **emigrant said:**
> Hey,
I had a similar issue with a 64 gb kingston. And finally i had to throw it since it was not 'genuine' and thus couldnt claim warranty.  Is that same with u?

This ones a 32GB. And I don't have a warranty so I can't chuck it. lol

---

### Post by 3rdalbum on 2009-11-18
> **ariascarlos1990 said:**
> tried the "cfdisk" heres what came up....

FATAL ERROR: Cannot open disk drive
                          Press any key to exit cfdisk

Sorry, I should have specified: cfdisk as root. (sudo cfdisk)

> what file system can hold more than 7 GIB then?

Pretty much every other filesystem available can store files bigger than 4 GiB. If you need to interoperate with Windows computers, then NTFS is your only choice. If you're only using the drive with Linux, then Ext3 is your best bet. If you're going to interoperate with BSD, then Ext2 is the way to go.

---

### Post by ariascarlos1990 on 2009-11-18
[LEFT]heres what happend when I typed "sudo cfdisk"
[/LEFT]
 
cfdisk (util-linux-ng 2.16)

[CENTER]                               Disk Drive: /dev/sda
                        Size: 80060424192 bytes, 80.0 GB
              Heads: 255   Sectors per Track: 63   Cylinders: 9733

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sda1        Boot        Primary   Linux ext3                       79308.15
    sda5                    Logical   Linux swap / Solaris               748.51










     [ Bootable ]  [  Delete  ]  [   Help   ]  [ Maximize ]  [  Print   ]
     [   Quit   ]  [   Type   ]  [  Units   ]  [  Write   ]

                 Toggle bootable flag of the current partition
[/CENTER]
 




And When I try to use the disk utility to format it to NTFS I get this error:

Error creating file system: helper exited with exit code 1: cannot spawn 'mkntfs -f /dev/sdb': Failed to execute child process "mkntfs" (No such file or directory)

---

### Post by ariascarlos1990 on 2009-11-18
To the top.

---

### Post by ariascarlos1990 on 2009-11-18
bump.

---

### Post by Sir Jasper on 2009-11-18
Hi,

The answers here are given by volunteer helpers. They are not your servants and it is considered rude to bump more than once a day.

Since you are in a hurry,  you could try the forum of your pen drive developer where there are probably help stickies and you can ask there as well

Alternatively, do you have the Ubuntu installation CD. If so use that to access Gparted and click apply when you have made your choice (probably NTFS).

My regards

---

### Post by ariascarlos1990 on 2009-11-18
Wow didn't mean to come across rude. I was just really frustrated with this. I'm sorry if I made anybody feel like a servant.

Anyways....

I do have the ubuntu installation cd but, its the 9.04 version. would that matter? and how do I access gparted from the installation cd? 

Thank you.

---

### Post by Sir Jasper on 2009-11-18
Hi again,

Which CD version is of no importance.

When loaded I anticipate you will soon find Gparted (it may be called Partition Editor), but if not come back as soon as you like.

We´re all allowed to communicate with questions, answers and views.

My regards

---

### Post by emigrant on 2009-11-18
boot from the live ubuntu cd, and go to system>admin>partion editor

---

### Post by blur xc on 2009-11-18
Did you ever verify if the drive was mounted?

Enter "mount" ad the command line and it will list all mounted file systems- /media/disk is where my flash drives always end up.

sudo umount -f /media/disk (if that's where it's mounted) to unmount it (the -f is to force the unmount, which could corrupt data on it, but since you are formatting anyway...).  Then try formatting.

If nothing works- turn the computer off- remove drive, turn computer on, re-insert drive and start over.  I've had goofy things happen w/ usb devices that I've only been able to solve by rebooting.  Linux doesn't seem to handle USB devices as well as Windows, in my experience.

BM

---

### Post by ariascarlos1990 on 2009-11-18
ok I don't get what jasper and emigrant are saying about booting it. from my desktop or from F1 in the initial startup? 

but, blur xc I typed in mount in the terminal and this came up. I'm really dumb when it comes to this stuff.

matt@matt-desktop:~$ mount
/dev/sda1 on / type ext3 (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/matt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matt)




The usb drive is in the computer. im going to now restart it and try it again.

---

### Post by emigrant on 2009-11-18
what i was saying is how to go the gparted through the live cd. i will tell you again in a clear manner:

go to BIOS setup and make sure that the first boot device is set to CDrom.
then insert the ubuntu cd (which you used to install)
select the first option when prompted
when you are taken to the desktop go to system>administration>partition editor.

hope thats clear :)

---

### Post by ariascarlos1990 on 2009-11-18
ok I booted from the live ubuntu cd and went to system/admin/partition editor and then gparted came up I selected my device. Its still unallocated.

Now what?

---

### Post by ariascarlos1990 on 2009-11-18
figured I'd post this as well:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a691a69

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9642    77449333+  83  Linux
/dev/sda2            9643        9733      730957+   5  Extended
/dev/sda5            9643        9733      730926   82  Linux swap / Solaris

Disk /dev/sdb: 33.5 GB, 33554432000 bytes
64 heads, 32 sectors/track, 32000 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0xffffffff

Disk /dev/sdb doesn't contain a valid partition table

---

### Post by blur xc on 2009-11-18
> **ariascarlos1990 said:**
> ok I booted from the live ubuntu cd and went to system/admin/partition editor and then gparted came up I selected my device. Its still unallocated.

Now what?

I've only used gparted once or twice, but as far as I can remember, it's pretty easy to figure out.  I think you can right click on the unallocated space and select something to make it some kind of file system, or from a pull down menu.  Pick what you want, and then commit or apply or whatever to make your changes stick.  Then sit back and wait for it to finish...

BM

---

### Post by benj1 on 2009-11-18
theres a walkthrough for gparted here
[http://www.howtoforge.com/partitioning_with_gparted]("http://www.howtoforge.com/partitioning_with_gparted")

---

### Post by ariascarlos1990 on 2009-11-18
ok when I try to right click on the grey unallocated 31.25 GiB I have the options of (new) & (information)

when I click new a window comes up with the name of (create partition table on /dev/sdb) I can click  >advanced and a drop down menu appears that read select new partition table type: I than have the option to click msdos, aix, amiga, bsd, dvh, gpt, mac. pc98, sun, and loop. 

p.s. None of these seem to wrok.

---

### Post by Sir Jasper on 2009-11-18
Hi,

With your flash drive chosen in Gparted, right click on the slim horizontal line.

Then choose New and your choices should then be obvious.

When you have chosen, click on the green Apply icon (it may look like a tick).

My regards

---

### Post by ariascarlos1990 on 2009-11-18
Are the talking about the slim line on the right I don't have that option when I click on my device.

---

### Post by ariascarlos1990 on 2009-11-18
I even tried to make a usb startup disk. it asked me to format the usb flash disk so I click format. 

it gave me this error:

Unable to format device:
Error: /dev/sdb: unrecognised disk label

---

### Post by Sir Jasper on 2009-11-18
Hi,

After you click on New you should see something like the picture below:

[[img]http://i.imagehost.org/t/0112/Screenshot-Create_new_Partition.jpg[/img]](http://i.imagehost.org/view/0112/Screenshot-Create_new_Partition)

I have to go now so I hope someone will pick up this ball if that does not help.

My regards

---

### Post by ariascarlos1990 on 2009-11-18
heres a picture of gparted when I first start it up:

[IMG]http://i125.photobucket.com/albums/p51/scooter_dude442/Screenshot-3.png[/IMG]

Then after I click on my device:
[IMG]http://i125.photobucket.com/albums/p51/scooter_dude442/Screenshot-1-1.png[/IMG]

And when I click new:

[IMG]http://i125.photobucket.com/albums/p51/scooter_dude442/Screenshot-2-1.png[/IMG]

---

### Post by emigrant on 2009-11-18
Hit create button

---

### Post by Sir Jasper on 2009-11-18
Hi,

Your picture is of your hard drive. 

Click on the V near the top right of the screen and choose you flash drive.

I have a few more minutes if you still have a problem.

My regards

---

### Post by ariascarlos1990 on 2009-11-18
> **emigrant said:**
> Hit create button

it doesn't seem to do anything....

> **Sir Jasper said:**
> Hi,

Your picture is of your hard drive. 

Click on the V near the top right of the screen and choose you flash drive.

I have a few more minutes if you still have a problem.

My regards

The first picture is of my hard drive the others are from the usb device...

It was to compare the two differences in options...( Slim bar with hard drive - No slim bar with device.)

---

### Post by Sylslay on 2009-11-18
got 2 x 16GB, from freind of mine,
both formated with fat32, and never working agin, cheap staff,,

I tried this: (from history)
  312  sudo mkfs -t vfat /dev/sdb1
  313  sudo mkfs -t ext3 /dev/sdb1
  314  su root
  315  sudo apt-get install gparted
  316  su root
  317  sudo apt-get install mbr
  318  fdisk -l
  319  su root
  320  apt-get install qpart
  321  sudo apt-get install qpart

Nothing work, but thouse drive show as 8MB fat, and can't change partition table. And one of this command says : inctrl error!!!!!!!!!!!1

Found that I may flash this pendrive with MPTool in win, but have to open pendrive and see what IC is inside and reprogram controller like in factory does.

broken=dump

---

### Post by ariascarlos1990 on 2009-11-18
> **Sylslay said:**
> got 2 x 16GB, from freind of mine,
both formated with fat32, and never working agin, cheap staff,,

I tried this: (from history)
  312  sudo mkfs -t vfat /dev/sdb1
  313  sudo mkfs -t ext3 /dev/sdb1
  314  su root
  315  sudo apt-get install gparted
  316  su root
  317  sudo apt-get install mbr
  318  fdisk -l
  319  su root
  320  apt-get install qpart
  321  sudo apt-get install qpart

Nothing work, but thouse drive show as 8MB fat, and can't change partition table. And one of this command says : inctrl error!!!!!!!!!!!1

Found that I may flash this pendrive with MPTool in win, but have to open pendrive and see what IC is inside and reprogram controller like in factory does.

broken=dump


So did you get it working????

---

### Post by JBAlaska on 2009-11-18
> **ariascarlos1990 said:**
> 
And when I click new:

[IMG]http://i125.photobucket.com/albums/p51/scooter_dude442/Screenshot-2-1.png[/IMG]

Hit create button, that will create a msdos partition table (what you want) and click the green check (Apply) in the gparted toolbar.

Then right click in blank space, new, create new partition, format with NTFS, add a label USB_STICK or something and click the green check (Apply) in the gparted toolbar.

I have not tried this as my biggest thumb drive is 4GB and fat32 is the way to go on that size stick.

Hope it helps.

---

### Post by ariascarlos1990 on 2009-11-18
> **JBAlaska said:**
> Hit create button, that will create a msdos partition table (what you want) and click the green check (Apply) in the gparted toolbar.

Then right click in blank space, new, create new partition, format with NTFS, add a label USB_STICK or something and click the green check (Apply) in the gparted toolbar.

I have not tried this as my biggest thumb drive is 4GB and fat32 is the way to go on that size stick.

Hope it helps.

The green check isent available to click on before of after I press the create button.

---

### Post by efflandt on 2009-11-18
Go ahead and "create msdos partition table".  That does not create any partitions yet, just the partition table (still unallocated).  You can then create whatever type of partition(s) you want to after that by right clicking on that unallocated line and then selecting New.

The problem is that you apparently have no recognizable partition table at all, so you cannot create partitions until you have a partition table.

---

### Post by ariascarlos1990 on 2009-11-18
> **efflandt said:**
> Go ahead and "create msdos partition table".  That does not create any partitions yet, just the partition table (still unallocated).  You can then create whatever type of partition(s) you want to after that by right clicking on that unallocated line and then selecting New.

The problem is that you apparently have no recognizable partition table at all, so you cannot create partitions until you have a partition table.

So How do I get partitions on my device table?

---

### Post by JBAlaska on 2009-11-18
I guess the apply check was not needed for partition table creation.

> right click in blank space, new, create new partition, format with NTFS, add a label USB_STICK or something and click the green check (Apply) in the gparted toolbar.

---

### Post by ariascarlos1990 on 2009-11-18
> **JBAlaska said:**
> I guess the apply check was not needed for partition table creation.

I guess. lol

---

### Post by ariascarlos1990 on 2009-11-18
You guys aren't my servants.

bump.

---

### Post by emigrant on 2009-11-18
now you at what stage?

---

### Post by ariascarlos1990 on 2009-11-18
> **emigrant said:**
> now you at what stage?

trying to get partitions on my partition table....

I think.

---

### Post by emigrant on 2009-11-18
ok, im starting from the last screenshot you posted:


[LIST=1]
[*]hit the create button
[*]select 'unallocated' and hit 'new'
[*]again do the step 2
[*]from the window 'create new partition' which just appears, select 'fat32' from the filesystem dropdown menu
[*]hit add
[*]click apply
[*]click again apply
[/LIST]

---

### Post by ariascarlos1990 on 2009-11-18
when ever I click new it keeps popping up the create a partition table.

---

### Post by teward on 2009-11-18
Wow, you killed your partition table.  Make a new partition table as MSDOS, then follow these steps: 


[LIST=1]
[*]hit the create button
[*]select 'unallocated' and hit 'new'
[*]again do the step 2
[*]from the window 'create new partition' which just appears, select 'fat32' from the filesystem dropdown menu
[*]hit add
[*]click apply
[*]click again apply
[/LIST]

---

### Post by ariascarlos1990 on 2009-11-18
> **TrekCaptainUSA said:**
> Wow, you killed your partition table.  Make a new partition table as MSDOS, then follow these steps: 


[LIST=1]
[*]hit the create button
[*]select 'unallocated' and hit 'new'
[*]again do the step 2
[*]from the window 'create new partition' which just appears, select 'fat32' from the filesystem dropdown menu
[*]hit add
[*]click apply
[*]click again apply
[/LIST]


In step 4 you say to select "fat32" from the file system drop down menu....

FAT32 does not appear in there... and every time I click "new" a create partition table comes up....... and it asked me what type of table I want thats when I click msdos.....then create....so what after that? click new again? and bring up another "create partition table"? its going nowhere.

---

### Post by Cheesemill on 2009-11-18
This is beginning to sound more and more like a hardware failure.
Where did you get the drive from?

---

### Post by emigrant on 2009-11-18
its seems a black market pendrive same as what i had.

---

### Post by ariascarlos1990 on 2009-11-18
> **Cheesemill said:**
> This is beginning to sound more and more like a hardware failure.
Where did you get the drive from?

I got it off craigslist. the guy owns his computer business. I would think he has quality stuff.???

Idk. But, this is really ticking me off. It was working fine the other day. until I decided to format it to NTFS

---

### Post by emigrant on 2009-11-18
the guaranty period is over or he didn't give you guarantee?

---

### Post by ariascarlos1990 on 2009-11-18
He showed me it worked right on his laptop. I also had it working I put a movie on it from my friends pc (xp) and brought the card back home inserted it into my computer (ubunto) and simply drag and dropped it off and onto my desktop. with no problems... but, the next day after that I tried to put a 7GiB iso file onto and it failed at about %99 I'm gueessing the file was to large for FAT32. So I got to reading on the net (searching every post on this sight) and learned that it has to be formated to NTFS for it to transfer that big of a file. So I then decided to format the 32GiB usb memory stick to NTFS (on his computer XP) and it failed sp then I tried to switch it back to FAT32 and that failed. Now it wont foramt to any type of file system.

The End.

Hope maybe you guys can help me figure this out.

Thanks!!!!

---

### Post by emigrant on 2009-11-18
> **ariascarlos1990 said:**
> 
The End.

Hope maybe you guys can help me figure this out.

Thanks!!!!

always go for a genuine one \\:D/

---

### Post by ariascarlos1990 on 2009-11-18
> **emigrant said:**
> always go for a genuine one \\:D/

Ok, so is this like the end to the help process? :-({|=

---

### Post by emigrant on 2009-11-18
sorry man i feel i can't help you any more.
i want you too to ditch you 32GB like how i did my 64GB.
:D
(just joking, may be some others can help???)

---

### Post by ariascarlos1990 on 2009-11-18
> **emigrant said:**
> sorry man i feel i can't help you any more.
i want you too to ditch you 32GB like how i did my 64GB.
:D
(just joking, may be some others can help???)

ok.

We'll I appreciate all you're help.

I hope someone else will chime in on this one...

---

### Post by ariascarlos1990 on 2009-11-19
So who can help me?

---

### Post by ariascarlos1990 on 2009-11-19
> **grace12 said:**
> Try going System, Administration and Disk Utility.

already tried that. 

anything else?

---

### Post by lotharmat on 2009-11-19
I think it may be time to stamp on it!

Or get the shop that sold it to you to format it for you.

---

### Post by ariascarlos1990 on 2009-11-19
I'll call the guy tomorrow.

Thanks everyone for the help.

---

### Post by emigrant on 2009-11-19
i bet he won't answer, go directly meet him :D

---

### Post by ariascarlos1990 on 2009-11-19
He gave me his business card with all his references and all the stuff he knows about computers. I know where he lives also.. lol I don't think he's gonna scam me. He'll at least give me my money back.. I can guaranty that.  :mrgreen:

I'll let you guys know what happened.

---

### Post by turbostd on 2009-11-19
Surprised no one said to zero the drive the file system and partition table is corrupt. do dd if=/dev/zero of=/dev/sdX bs=1M Where sdX is put the letter of the drive. make sure you pick the right letter or it will wipe out you hard drive. Learned that one the hard way lol.

---

### Post by ariascarlos1990 on 2009-11-19
> **turbostd said:**
> Surprised no one said to zero the drive the file system and partition table is corrupt. do dd if=/dev/zero of=/dev/sdX bs=1M Where sdX is put the letter of the drive. make sure you pick the right letter or it will wipe out you hard drive. Learned that one the hard way lol.

ok so I entered dd if=/dev/zero of=/dev/sdb bs=1M 

in the terminal and this came back...

matt@matt-desktop:~$ dd if=/dev/zero of=/dev/sdb bs=1M
dd: opening `/dev/sdb': Permission denied

---

### Post by emigrant on 2009-11-19
if you get permission denied for something,
insert sudo at the front.

---

### Post by Sir Jasper on 2009-11-19
Hi,

[COLOR="Red"]If the pen drive is basically sound then I can as good as guarantee this will work.[/COLOR]

Clone from a hard drive (or another pen drive) 32 GB (or less, since it could be resized afterwards) of anything (programs and/or data) in fat32, NTFS, or ext3 format.

That will clone the format as well as up to the first 32 GB of data from the Source drive to your Target pen drive. 

Once it is readable by Gparted you should then, if desired, be able to resize, reformat, name it, rename it  or even partition it.

My regards

If you do not have a cloning program then seek advice or get your seller friend to do it for you (if he has no quicker or better method of fixing).

---

### Post by ariascarlos1990 on 2009-11-19
I put sudo in front of the command and its still running. Should it be taking this long? its been about 15mins.

---

### Post by turbostd on 2009-11-19
ya it will take a while last one i did took 45 min.

---

### Post by ariascarlos1990 on 2009-11-19
> **Sir Jasper said:**
> Hi,

[COLOR=Red]If the pen drive is basically sound then I can as good as guarantee this will work.[/COLOR]

Clone from a hard drive (or another pen drive) 32 GB (or less, since it could be resized afterwards) of anything (programs and/or data) in fat32, NTFS, or ext3 format.

That will clone the format as well as up to the first 32 GB of data from the Source drive to your Target pen drive. 

Once it is readable by Gparted you should then, if desired, be able to resize, reformat, name it, rename it  or even partition it.

My regards

If you do not have a cloning program then seek advice or get your seller friend to do it for you (if he has no quicker or better method of fixing).

Ok where can I get a cloning program that is able to do this? Maybe I'll hold off on calling him. I like to figure things out myself. (we'll with the help of ubuntu forums) ;)

---

### Post by ariascarlos1990 on 2009-11-19
> **turbostd said:**
> ya it will take a while last one i did took 45 min.

Sweet I'll keep it running then.

---

### Post by Sir Jasper on 2009-11-19
Hi for the last time,

Here are my tips:

(1) Use a cloning program and possibly a backup program as well. When you make progress and get things as you like you can just clone back or restore.

Google and/or use the search facility above. That should avoid your needing to open a separate thread here. 

(2) Download the Free PDF book (see the first sticky above). Skip read it, then use the Index when you need it. It has the first 18 pages in Roman numerals - so e.g. if you want to read page 40, use GOTO page 58. Alternatively, type your keyword into the PDF search box.

My regards

PS Your current task may take a lot longer than 45 minutes (as the time taken will vary with the size of the pen drive).

---

### Post by ariascarlos1990 on 2009-11-19
Ok I left it running all night night and woke up this morning with this is my terminal:

matt@matt-desktop:~$ sudo dd if=/dev/zero of=/dev/sdb bs=1M 
[sudo] password for matt: 
dd: writing `/dev/sdb': No space left on device
32001+0 records in
32000+0 records out
33554432000 bytes (34 GB) copied, 1952.84 s, 17.2 MB/s

---

### Post by ariascarlos1990 on 2009-11-19
Whats the next step after this? I don't want to mess anything up.

---

### Post by blur xc on 2009-11-19
I'd assume to fire up gparted again and try creating a partition table again, and then an actual file system...

BM

---

### Post by ariascarlos1990 on 2009-11-19
heres my 
devkit-disks --dump
Showing information for /org/freedesktop/DeviceKit/Disks/devices/sdb
  native-path:                 /sys/devices/pci0000:00/0000:00:03.3/usb1/1-8/1-8:1.0/host4/target4:0:0/4:0:0:0/block/sdb
  device:                      8:16
  device-file:                 /dev/sdb
    by-id:                     /dev/disk/by-id/usb-Generic_Flash_Disk_2.0-0:0
    by-path:                   /dev/disk/by-path/pci-0000:00:03.3-usb-0:8:1.0-scsi-0:0:0:0
  detected at:                 Thu 19 Nov 2009 04:29:44 AM PST
  system internal:             0
  removable:                   1
  has media:                   1 (detected at Thu 19 Nov 2009 04:29:44 AM PST)
    detects change:            1
    detection by polling:      1
    detection inhibitable:     1
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        33554432000
  block size:                  512
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  drive:
    vendor:                    Generic
    model:                     Flash Disk 2.0
    revision:                  2.40
    serial:                    
    detachable:                1
    can spindown:              0
    rotational media:          1
    ejectable:                 0
    media:                     
      compat:                 
    interface:                 usb
    if speed:                  480000000 bits/s
    ATA SMART:                 not available





Its showing up as blocked...

---

### Post by turbostd on 2009-11-19
unplug it re-plug it and try partitioning it with gparted again. Wait blocked? Does that drive happen to have a write protect switch on it?

---

### Post by ariascarlos1990 on 2009-11-19
heres this to. Its saying that it doesn't contain a valid partition table....

matt@matt-desktop:~$ sudo fdisk -l
[sudo] password for matt: 

Disk /dev/sda: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a691a69

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9642    77449333+  83  Linux
/dev/sda2            9643        9733      730957+   5  Extended
/dev/sda5            9643        9733      730926   82  Linux swap / Solaris

Disk /dev/sdb: 33.6 GB, 33554432000 bytes
64 heads, 32 sectors/track, 32000 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

---

### Post by ariascarlos1990 on 2009-11-19
> **turbostd said:**
> unplug it re-plug it and try partitioning it with gparted again. Wait blocked? Does that drive happen to have a write protect switch on it?

none that I can see.

---

### Post by blur xc on 2009-11-19
> **ariascarlos1990 said:**
> heres this to. Its saying that it doesn't contain a valid partition table....

matt@matt-desktop:~$ sudo fdisk -l
[sudo] password for matt: 

Disk /dev/sda: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a691a69

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9642    77449333+  83  Linux
/dev/sda2            9643        9733      730957+   5  Extended
/dev/sda5            9643        9733      730926   82  Linux swap / Solaris

Disk /dev/sdb: 33.6 GB, 33554432000 bytes
64 heads, 32 sectors/track, 32000 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Of course it doesn't have a valid partition table.  You just dd'd the whole drive w/ a bunch of zeros.  It's as blank as a blank disk can get.

BM

---

### Post by ariascarlos1990 on 2009-11-19
> **blur xc said:**
> Of course it doesn't have a valid partition table.  You just dd'd the whole drive w/ a bunch of zeros.  It's as blank as a blank disk can get.

BM

duh. lol Its still not letting me make a partition table.

---

### Post by turbostd on 2009-11-19
gparted still cant partition? Thats odd I dont think ive ever had one do that.

---

### Post by running_rabbit07 on 2009-11-19
I don't think I have ever seen someone bump their thread so many times in 48 hours. Demanding help in a volunteer community is not very polite.

---

### Post by ariascarlos1990 on 2009-11-19
> **running_rabbit07 said:**
> I don't think I have ever seen someone bump their thread so many times in 48 hours. Demanding help in a volunteer community is not very polite.

that was already discussed I'm sorry for that. I was just getting frustrated with it. No ones my servant.

anyways. 

I got to reading again came upon this command.

sudo mkfs.msdos -F 32 /dev/sda1

I changed the sda1 to sdb so its like mine.  and entered it into the terminal.

heres what came back:

matt@matt-desktop:~$ sudo mkfs.msdos -F 32 /dev/sdb
mkfs.msdos 3.0.3 (18 May 2009)
mkfs.msdos: Device partition expected, not making filesystem on entire device '/dev/sdb' (use -I to override)


where do I instert the "-I" so I can override it?

Thanks for all the people that have taken there time to help so far!

---

### Post by turbostd on 2009-11-19
you cant format a device like that you need a partition.

---

### Post by ariascarlos1990 on 2009-11-19
and the only way to add a partition is through gparted?

---

### Post by turbostd on 2009-11-19
you could try cfdisk do cfdisk /dev/sdb dont know if thats installed by default any more.

---

### Post by Xamiga on 2009-11-19
[QUOTE=ariascarlos1990;8344366]it doesn't seem to do anything....

go to this point again, then wait.  you may think nothing is happening.  go have a cup of coffee, beer, watch a movie.  let me know if nothing has happened after an hour.

---

### Post by ariascarlos1990 on 2009-11-19
> **turbostd said:**
> you could try cfdisk do cfdisk /dev/sdb dont know if thats installed by default any more.

i'll look into that.

thanks.

> **Xamiga said:**
> [quote=ariascarlos1990;8344366]it doesn't seem to do anything....

go to this point again, then wait.  you may think nothing is happening.  go have a cup of coffee, beer, watch a movie.  let me know if nothing has happened after an hour.


That to.

I kept reading and found this command:

sudo shred -vn 1 /dev/sdb

the guy was having the same problems I was.

We'll see what happens I guess.

---

### Post by ariascarlos1990 on 2009-11-20
well nothing seemed to work. So I called up the guy that I bought the thumb drive from. He said to bring it over. He couldn't figure it out either.

Anyways I got my $30 back.

---

### Post by running_rabbit07 on 2009-11-20
> **ariascarlos1990 said:**
> Anyways I got my $30 back.

That's good. Sux that you couldn't get it to work though.

---

### Post by ariascarlos1990 on 2009-11-20
> **running_rabbit07 said:**
> That's good. Sux that you couldn't get it to work though.

I know. We'll coming from the pros. What in you're opinion is the best usb thumb drive to transfer about 9GB files back and forth from ubuntu to XP?

---

### Post by running_rabbit07 on 2009-11-20
> **ariascarlos1990 said:**
> I know. We'll coming from the pros. What in you're opinion is the best usb thumb drive to transfer about 9GB files back and forth from ubuntu to XP?

I can't answer that. I have never tried to move that large of a file. Though it would be interesting to find out if were to ever need to copy my Virtual Machine files.

---

### Post by ariascarlos1990 on 2009-11-20
> **running_rabbit07 said:**
> I can't answer that. I have never tried to move that large of a file. Though it would be interesting to find out if were to ever need to copy my Virtual Machine files.

We'll thanks for you're honest opinion. 

Maybe someone will provide with an answer.?.

---

### Post by lavinog on 2009-11-20
fat32 has a 4g file size limitation.  You might be better off compressing your file into smaller split archives.

---

### Post by byStanderone on 2009-11-20
hi guys...
had come across bout this issue with usb drives, try using your usb drive alone, without any other device on any usb ports...except that usb drive that you are trying to format.

...your usb is a bit of a store, perhaps you should format it as ext3 or higher.

---

### Post by emigrant on 2009-11-20
whatever you buy, don't forget to get a warranty.

---

### Post by ariascarlos1990 on 2009-11-20
> **lavinog said:**
> fat32 has a 4g file size limitation.  You might be better off compressing your file into smaller split archives.

I know. when I tried to format the thumb drive to NTFS it some how corrupted the drive. lol The guy I bought this from had an extra 16GB thumb drive and was gonna sell it to me for $20 I was like if you can format it NTFS ill take it. So he was like yah ok. He went to format it and boom same thing that happened to me. So now he has a 16GB and a 32GB that neither of them work now. I don't know what it is with NTFS and these thumb drives.....?

> **byStanderone said:**
> hi guys...
had come across bout this issue with usb drives, try using your usb drive alone, without any other device on any usb ports...except that usb drive that you are trying to format.

...your usb is a bit of a store, perhaps you should format it as ext3 or higher.

I could format it ext3 but then I wouldn't be able to transfer files from XP to ubuntu....

> **emigrant said:**
> whatever you buy, don't forget to get a warranty.


True! I'm gonna go to the store next time I buy a thumb drive. not craigslist. ;)

---

### Post by ariascarlos1990 on 2009-11-20
we'll what do you guys think about using my 30gb Zune to transfer the files? I've been reading and came upon a program called virtualbox..anybody familiar with this program??

---

### Post by enumoran on 2009-11-20
Make sure it has a warranty for thumb drive.

---

### Post by Bunnybugs on 2009-11-20
> **ariascarlos1990 said:**
> we'll what do you guys think about using my 30gb Zune to transfer the files? I've been reading and came upon a program called virtualbox..anybody familiar with this program??

Virtualbox slows your computer down!

Is the system dualbooted??

Because you can add the files to a folder on the HDD from windows, and copy/paste them to your ubuntu filesystem...

Even, if you have vista, you can import you user folder to ubuntu

---

### Post by ariascarlos1990 on 2009-11-20
> **Bunnybugs said:**
> Virtualbox slows your computer down!

Is the system dualbooted??

Because you can add the files to a folder on the HDD from windows, and copy/paste them to your ubuntu filesystem...

Even, if you have vista, you can import you user folder to ubuntu

Its not dualbooted. thanks for the advice though.

Is there any other way to get a large file from one computer (xp) to another (ubuntu)?

---

### Post by emigrant on 2009-11-20
U can write the file into a 10gb dvd.

---

### Post by dunkar70 on 2009-11-20
1. Make sure your thumb drive is a standard flash drive. Some thumb drives have logic built into the drive for encryption or other functionality that may be causing a problem. U3 drives have some of this type of logic that has caused me headaches. 

2. Plug in your drive and identify the device name:
[LIST]
[*]In this example, the 256MB drive (red label) is assigned to /dev/sdc.
[/LIST]```
$ sudo fdisk -l
[sudo] password for user: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
... (details removed for brevity)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
... (details removed for brevity)

[COLOR="Red"]Disk /dev/sdc: 257 MB,[/COLOR] 257949696 bytes
16 heads, 32 sectors/track, 984 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x9fe47ffa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         983      251632    b  W95 FAT32
```

3. Use gparted to delete the partitions already on the drive. 
[LIST]
[*]Make sure you apply the changes.
[*]Avoid the Disk Utility in Ubuntu 9.10. I have found it unreliable and even dangerous. It affected partitions I was not changing.
[/LIST]
4. Create a new partition with EXT2 if you plan to only use this on *NIX operating systems. 
[LIST]
[*]EXT3 includes journaling for data protection, but it slows down the drive. You should backup your thumb drives to another location if you are using it regularly.
[*]Do not create an NTFS partition with gparted.
[*]If you need to access the drive with Windows and store files over 4GB, reboot to Windows and use the disk manager to create an NTFS partition.
[/LIST]

Some of these steps may not be necessary, but each step provides a point of failure to focus on.

---

### Post by dunkar70 on 2009-11-20
If this is a one-time file transfer, get WinSCP (There is a portable version at [http://www.portableapps.com](http://www.portableapps.com)) and push the file from Windows to Ubuntu. WinSCP uses an SSH connection and does not require you to install or configure an FTP server.

This assumes you can SSH into your Ubuntu box now.

---

### Post by Don1500 on 2009-11-20
I have run ito this problem because there is a low level format on some USB thumb drives. I found a utility from PQi called Ur-Smart ([http://www.pqi.com.tw/download.asp?frm=1#main](http://www.pqi.com.tw/download.asp?frm=1#main)) that will resurect a dead thumb drive. I have used it on PQi drives and some others and it worked. (This is a Windows .exe program)

I have a Sandisk 8 gig I am using now and it has a Fricked up mini "CD" ?Partition? that I can't get rid of (It doesn't show up on g-parted). It is formated to FAT32 and has ubuntu 9.10 installed. It works fine but it says I have only 4 meg left on the drive (I can see over 6gig on g-parted but I can't access it.) I think I may have to try reformating and using the PQi program to rebuild the file system. I am not sure this will work and it may kill this drive, but I may not have a choice but to try.

---

### Post by lavinog on 2009-11-20
> **ariascarlos1990 said:**
> 
Is there any other way to get a large file from one computer (xp) to another (ubuntu)?

The way I mentioned before, split the file into multiple files.
Rar and 7z can both do this and both archives are recognized by both operating systems.

---

### Post by lavinog on 2009-11-20
I noticed that the graphical archiver doesn't give you an option to control the level of compression so the commandline would be quicker.
```

7z a -mx=0 -v2g archivename.7z largefile

```
-v2g means split into 2g files
-mx=0 means no compression (fastest method)

---

### Post by ariascarlos1990 on 2009-11-20
> **emigrant said:**
> U can write the file into a 10gb dvd.

The XP computer Doesn't burn dvd or cd's so thats out of the question. Thanks anyways through. 

> **dunkar70 said:**
> 1. Make sure your thumb drive is a standard flash drive. Some thumb drives have logic built into the drive for encryption or other functionality that may be causing a problem. U3 drives have some of this type of logic that has caused me headaches. 

2. Plug in your drive and identify the device name:
[LIST]
[*]In this example, the 256MB drive (red label) is assigned to /dev/sdc.
[/LIST]
```
$ sudo fdisk -l
[sudo] password for user: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
... (details removed for brevity)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
... (details removed for brevity)

[COLOR=Red]Disk /dev/sdc: 257 MB,[/COLOR] 257949696 bytes
16 heads, 32 sectors/track, 984 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x9fe47ffa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         983      251632    b  W95 FAT32
```3. Use gparted to delete the partitions already on the drive. 
[LIST]
[*]Make sure you apply the changes.
[*]Avoid the Disk Utility in Ubuntu 9.10. I have found it unreliable and even dangerous. It affected partitions I was not changing.
[/LIST]
4. Create a new partition with EXT2 if you plan to only use this on *NIX operating systems. 
[LIST]
[*]EXT3 includes journaling for data protection, but it slows down the drive. You should backup your thumb drives to another location if you are using it regularly.
[*]Do not create an NTFS partition with gparted.
[*]If you need to access the drive with Windows and store files over 4GB, reboot to Windows and use the disk manager to create an NTFS partition.
[/LIST]

Some of these steps may not be necessary, but each step provides a point of failure to focus on.

> **dunkar70 said:**
> If this is a one-time file transfer, get WinSCP (There is a portable version at [http://www.portableapps.com](http://www.portableapps.com)) and push the file from Windows to Ubuntu. WinSCP uses an SSH connection and does not require you to install or configure an FTP server.

This assumes you can SSH into your Ubuntu box now.

I tried running that U3 program through it also with no luck it wouldn't even pick it up.

Thanks.


> **Don1500 said:**
> I have run ito this problem because there is a low level format on some USB thumb drives. I found a utility from PQi called Ur-Smart ([http://www.pqi.com.tw/download.asp?frm=1#main](http://www.pqi.com.tw/download.asp?frm=1#main)) that will resurect a dead thumb drive. I have used it on PQi drives and some others and it worked. (This is a Windows .exe program)

I have a Sandisk 8 gig I am using now and it has a Fricked up mini "CD" ?Partition? that I can't get rid of (It doesn't show up on g-parted). It is formated to FAT32 and has ubuntu 9.10 installed. It works fine but it says I have only 4 meg left on the drive (I can see over 6gig on g-parted but I can't access it.) I think I may have to try reformating and using the PQi program to rebuild the file system. I am not sure this will work and it may kill this drive, but I may not have a choice but to try.

I'll try that next time thanks!

> **lavinog said:**
> The way I mentioned before, split the file into multiple files.
Rar and 7z can both do this and both archives are recognized by both operating systems.

I can't slit the files or compress them they will corrupt. These files are really picky..;)

> **lavinog said:**
> I noticed that the graphical archiver doesn't give you an option to control the level of compression so the commandline would be quicker.
```

7z a -mx=0 -v2g archivename.7z largefile

```-v2g means split into 2g files
-mx=0 means no compression (fastest method)

hmm. we'll I can't compress these files but, that seems like it would work.

Thanks. 


What do you guys think about using Samba to transfer the file from the xp computer to the other computer (ubuntu)?

---

### Post by lavinog on 2009-11-20
> **ariascarlos1990 said:**
> 

hmm. we'll I can't compress these files but, that seems like it would work.
Thanks. 

If compressing a file leads to corruption could you file a bug report. It shouldn't be that way.
also on windows 7z is a free program: [7-zip.org](7-zip.org)

> 
What do you guys think about using Samba to transfer the file from the xp computer to the other computer (ubuntu)?

Samba should be the easiest method.

---

### Post by papuccino1 on 2009-11-20
Have you tried using fdisk in the windows dos mode?

---

### Post by ariascarlos1990 on 2009-11-21
> **lavinog said:**
> If compressing a file leads to corruption could you file a bug report. It shouldn't be that way.
also on windows 7z is a free program: [7-zip.org]("http://7-zip.org")



Samba should be the easiest method.

these .iso files are really stubborn. 

I'm gonna have to go with samba..

> **papuccino1 said:**
> Have you tried using fdisk in the windows dos mode?

I don't have the thumb drive anymore but, I'll look into that next time.

---

### Post by Sylslay on 2009-12-02
I flash my broken 16gg usb drive with that softwere:
Ameco_MW6208E_8208_1.2.0.8_20090724
popular call as udftool_1.2.XX ver from 2009

Only one key has been fix, second had fake 4GB chip instead 16 and not possyble to fix

No ordinary format help, either in linux or win xp had show 8mb capacity of broken usb.
Tried: fdisk, gparted, Hp_tool, and other, alway had  IO error,

after flashed with udftool, can formated again in any program

---

### Post by jmundinger on 2009-12-02
I don't have an Ubuntu solution but have one suggestion that you might try in xp.  Open up disk management with the thumb drive installed.  The drive should show up.  Select it and then delete the partition.  Then try to format it.

---

