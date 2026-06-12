---
title: "losing ground"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by protpisys on 2010-08-22
hmmm...the problem, it appears, is a result of doing my initial Ubuntu install with my Toshiba Satellite laptop connected to the My Book Essential 650GB external drive I generally have plugged in. Now my computer won't work without the external dive attached which is problematic and contrary to the main advantage of the laptop in general. What happens is I get the grub error prompt at boot and never get to the windows/ubuntu choice screen. Ok, so I do some research and find that there's a synaptic function that will create a file of all the changes you've made, as far as packages go, and will then revert your system back to current state after a reinstall. So I do that and save that file and my home folder to a thumb drive and proceed to reinstall from the live disk. But, the install hung at the harddrive partition screen. I chose the recommended side by side settings hit go and nothing at all happened...never got to 1%. just sat there a good 5 minutes or so. They disk has, obviously, been partitioned as I already had Ubuntu running. I can't be the first person to reinstall, so what am I missing? Someday I will look back on this weekend and laugh...this, alas, is not that day. Help.

---

### Post by Zimmer on 2010-08-22
Insufficient info to diagnose... and ignoring the changes file for the moment..

Where did you install Ubuntu? On the USB drive? On the laptop?  
And where did you install GRUB ? 
Did you use the 'Advanced' button on the install GUI ?

Best Guess :
1) You installed to the Laptop and wrote GRUB to the MBR of the internal disk and it may have stalled looking for the (now disconnected) USB drive.

The straightforward answer to that should be to remove USB drive, boot with LiveCD and update or reinstall  GRUB.

---

### Post by protpisys on 2010-08-22
I installed it on my computer, it appears the the instalation program placed vital files on the usb drive as my computer no longer works if it's not attached. My best guess at a solution was to detach the usb drive and just start again, which would, for lack if an alternative, place all the necessary files on my c drive so that my computer would work in an untethered state.  How can I go about reinstalling grub?

---

### Post by protpisys on 2010-08-22
I just installed grub version 2 and my problem remains, I can't boot my computer without the external drive attached

---

### Post by -kg- on 2010-08-22
When you got to the Partitioning part of the installation, how did you elect to install?  Did you choose "Side by Side"? "Install to the largest contiguous free space"?  "Manual Partitioning"?  You didn't mention whether you still had Windows on it...did you install with "Use the whole disk"?

The reason I'm asking these questions is that you have to make absolutely sure during this portion of the installation that you have the correct disk selected.  With a laptop with a USB drive connected, that shouldn't be an issue (unless you selected manual partitioning and confused the drives), but that's no guarantee.

My desktop has two PATA drives and a SATA.  It boots to the Master PATA drive, but Ubuntu insists on calling the SATA drive sda and the two PATA drives sdb and sdc.  If I do an installation on my Master PATA drive (sdb), I have to manually select that drive in the last step of the installation, because default is sda and that's where BIOS looks for the bootloader in the MBR.

Please boot into Ubuntu (with the USB drive connected, of course), pull up a terminal, and type or copy and paste the following command:

```
sudo fdisk -l
```
(That's a lower case "-L")

Paste the results here in your next post.  That will tell us what partitions you have where, then we can go from there.

---

### Post by protpisys on 2010-08-22
Hey, I am running side by side with vista both times I installed, once sucessfully, I chose the automatic settings. I didn't select anything at all. There is definitely something going on with the usb drive as it's gone from 650 to 298 GBs since I installed Ubuntu..I created a live disk for gparted but was trying to get the bugger working w/out the usb 1st. Regardless the info you requested is, thanks for the help

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf99b3d64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       30402   242661376    7  HPFS/NTFS

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38965   312982218    7  HPFS/NTFS
/dev/sdc2           38965       77826   312147969    5  Extended
/dev/sdc5           38965       76744   303461376   83  Linux
/dev/sdc6           76744       77826     8685568   82  Linux swap / Solaris

---

### Post by protpisys on 2010-08-22
also, when I go to unmount the usb drive from the desk top, I get the "one or more partitions are busy on /dev/sdc" message

---

### Post by -kg- on 2010-08-22
No sir.  You installed Ubuntu on your USB drive.  "fdisk -l" tells the story:

> Device Boot Start End Blocks Id System
/dev/sda1 1 192 1536000 27 Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2 * 192 30402 242661376 7 HPFS/NTFS

"sda" is the drive in your laptop.  You'll notice that there is only two partitions on the drive.  "sda1" is your Vista Recovery partition and sda2 is your actual Vista partition.

> Device Boot Start End Blocks Id System
/dev/sdc1 1 38965 312982218 7 HPFS/NTFS
/dev/sdc2 38965 77826 312147969 5 Extended
/dev/sdc5 38965 76744 303461376 83 Linux
/dev/sdc6 76744 77826 8685568 82 Linux swap / Solaris

While I don't know what happened to sdb (sdb seems to be absent)_sdc seems to be your external USB hard drive.  As you said:

> There is definitely something going on with the usb drive as it's gone from 650 to 298 GBs since I installed Ubuntu..

You are going to have some work to do to correct all this.  You obviously want to install Ubuntu side by side on your laptop's internal hard drive, since you want to be able to boot Ubuntu without the external connected.  I'm sure you found that you can't even boot Vista without it.

This is because, while the GRUB bootloader is installed to the MBR of your laptop's internal drive, it is just a small part of the boot loader.  This points to subsequent stages of GRUB contained in the "/boot" directory of your Ubuntu installation, which obviously is on the external drive.  No drive...no subsequent stages of GRUB...no boot.

> also, when I go to unmount the usb drive from the desk top, I get the "one or more partitions are busy on /dev/sdc" message 

That is because Ubuntu is installed to and running from the external drive.  You can't unmount the partitions that Ubuntu are running from or using.

There have been problems with using GParted to shrink Vista partitions (I don't know about Windows 7) and it is suggested that you use Vista's Disk Management tool to shrink its partition.  You will want to defrag the partition first, again, using Vista's own defragmentation tool.  Hopefully you'll be able to free up ***at least*** 15 or 20 GB...as much as you can, but if you can't free up at least, say, 10 GB, then you might need to move some extraneous files from the main Vista partition.  Shrink Vista as much as possible.

Shrink it as much as you can (I'm not real happy with Vista's partition usage...you can't shrink it as much as you want because of system files that disallow it) then install to the free space you're left with using the "Install to largest contiguous free space" selection when you come to the partitioning step.

If your plans are to use NTFS only on the external, I would unplug it during the installation procedure.  That will minimize the possibility of any "accidents".  If you plan on using Linux partitions on it as well (or even leave the installation on your external and change the boot loader to the MBR of the external.  This will then make the external bootable by selection in BIOS.

Do this step first, and make ***_sure_*** you have sda selected (if you haven't unplugged it).  By your fdisk output, that should be the only disk that has any free space available, but make sure anyway.  You should be able to tell which disk you have selected, because sda won't have any ext4 or swap partitions, and sdc will.

This will install Ubuntu on your internal hard drive and the GRUB bootloader will point to that.  Any further considerations, just post back.  Read at the link in my signature block for further information on basic partitioning operations.

Proceed with the installation and it should install fine.  Just make sure you're installing it to sda.

---

### Post by protpisys on 2010-08-22
vista wouldn't let me resize the partitions, can I use gparted on it?

---

### Post by protpisys on 2010-08-22
I'm just sooo frustrated here. Vista won't let me resize and gparted won't let me unmout it in order to shrink the computer c drive...aaarrrgggghhhh...any hints on what to do next...I've been cleaning out Vista and have close to 100 GBs free on my C drive which I defragged last night in anticipation. I should be able to shrink it down to give Ubuntu like 30GBs or so right? There's gotta be a way, but I've gotta step away for a while before the expensive stuff starts flying. Thanks

---

### Post by -kg- on 2010-08-22
I've been thinking and thinking, and can't come up with a reason that you can't shrink Vista's partition with Vista's Disk Management.

I have one more request of you.  Please launch Ubuntu from the Live CD and launch GParted from the Live CD desktop.  It will be under "System/Administration/GParted".

Please take a snapshot of GParted looking at your sda drive and post it here.  The "fdisk" command will only list partitions, not free space, and though doing the math from fdisk doesn't show any free space available, it just doesn't make sense that you can't shrink the Vista partition unless it has already been shrunk and we just don't know it.

GParted will show the entire drive, free space and all.  It may show that you already have free space from previous operations.

There are a (very) few other options we might explore before I tell you to try shrinking Vista with GParted.  As I said, there have been problems in the past using GParted to shrink Vista partitions, and I don't want to chance bollixing up your Vista installation before we explore those, as well.

For instance, there are times that you might need to perform more than one defragging session.  Also, considering that I don't have much use for the default defragger in Windows in general, I usually use Executive Software Diskeeper, on which the default Windows defragger is based.  Yes, I know it's a "payfer," but it really works well.  There may be other "free" ones that I don't know about.

Anyway, let's see what your sda drive looks like.

---

### Post by protpisys on 2010-08-22
it doesn't look like there's any open space at all, Vista takes it all



[IMG]file:///tmp/moz-screenshot-3.png[/IMG][IMG]file:///tmp/moz-screenshot-4.png[/IMG][IMG]file:///tmp/moz-screenshot-5.png[/IMG][IMG]file:///tmp/moz-screenshot-6.png[/IMG][IMG]file:///tmp/moz-screenshot-7.png[/IMG][IMG]file:///tmp/moz-screenshot-8.png[/IMG][IMG]file:///tmp/moz-screenshot-9.png[/IMG][IMG]file:///tmp/moz-screenshot-10.png[/IMG][IMG]file:///tmp/moz-screenshot-11.png[/IMG][IMG]file:///tmp/moz-screenshot-12.png[/IMG][IMG]file:///tmp/moz-screenshot-13.png[/IMG][IMG]file:///tmp/moz-screenshot-14.png[/IMG][IMG]file:///tmp/moz-screenshot-15.png[/IMG]/home/ubuntu/Desktop/Screenshot--dev-sda - GParted.png

[IMG]file:///home/ubuntu/Desktop/Screenshot.png[/IMG]
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG][IMG]file:///tmp/moz-screenshot-2.png[/IMG][IMG]file:///home/ubuntu/Desktop/Screenshot.png[/IMG]

---

### Post by protpisys on 2010-08-22
man this just isn't my  day...the save to clipboard function on the save screenshot screen does nothing and copying and pasting the image file produces the above

---

### Post by uRock on 2010-08-22
Save screenshots to the desktop, then add them to the post using the Paperclip icon.

---

### Post by protpisys on 2010-08-22
ok thanks, I've just been using the quick reply deal that doesn't have the paper clip, this is actually from my desktop not the live cd if that matters. let me know

---

### Post by -kg- on 2010-08-22
> **protpisys said:**
> ok thanks, I've just been using the quick reply deal that doesn't have the paper clip, this is actually from my desktop not the live cd if that matters. let me know

No, doesn't matter.  I was going to suggest it if you had it installed.  All we're doing is looking at the partitions at this point.

OK, I see you have a warning indicator (the yellow triangle with the exclamation point) on the line for sda2.  I can't remember exactly how to pull up the warning information, but it's either by double clicking on the triangle or right clicking on either the graphic representation of the affected partition or the line that it's on below and select either "Check" or "Information" from the menu (I think it's "Information").

Let us know what the pop-up window tells you the problem is.

<Edit> - When you take a snapshot, usually it is better to select "Grab the current window" (the second radio button).  This saves room and makes the image easier to see and read.

---

### Post by Zimmer on 2010-08-22
Vista will not play nice with shrinking the partition if Pagefile is enabled and snapshotting. This will leave system files in the middle of the partition and it will resist attempts to resize.

Switch off pagefile and snapshots and defrag.

Even then Vista will hog at least 70gb of the partition (if not more, speaking from personal experience) then use Vista's Disk management tool to resize as best you can.

There are long stories here as to the why
[http://www.multibooters.co.uk/](http://www.multibooters.co.uk/)

And explicit instructions here for How
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)

---

### Post by PhilGil on 2010-08-22
Also, are you sure NTFS file system support is installed?  To verify, on the gparted menu, click on *View-->File System Support.*  You should see a window similar to the screenshot I've attached.  If every column in the NTFS row isn't checked, you can install NTFS support by opening a terminal and entering:

```
$ sudo apt-get install ntfsprogs
```

---

### Post by protpisys on 2010-08-22
first of all, thanks to everyone for all the help, I'm in so far over my head now its ridiculous. attached is the warning screen from the triangle icon

---

### Post by protpisys on 2010-08-22
ok, now here's the other thing...how can I copy copy the image from above and paste it to my desktop to compare?

---

### Post by protpisys on 2010-08-22
both file system supports seem the same except that mine has white X's in the red circles

---

### Post by PhilGil on 2010-08-23
Your file system support is fine.  It looks to me like you have some file system or disk errors on your NTFS drive.  Boot to Vista and run Chkdsk, then defrag.

After the disk check and defrag try again using gparted.  If you're still getting errors  take a look at the link Zimmer posted, which describes how to use Vista's partitioner to shrink your NTFS partition.

---

### Post by -kg- on 2010-08-23
> **Zimmer said:**
> Vista will not play nice with shrinking the partition if Pagefile is enabled and snapshotting. This will leave system files in the middle of the partition and it will resist attempts to resize.

Switch off pagefile and snapshots and defrag.

Even then Vista will hog at least 70gb of the partition (if not more, speaking from personal experience) then use Vista's Disk management tool to resize as best you can.

There are long stories here as to the why
[http://www.multibooters.co.uk/](http://www.multibooters.co.uk/)

And explicit instructions here for How
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)

Zimmer has a very good point, and one that I'd forgotten, since it's been so long since I've had to deal with the issue.  As a matter of fact, I shrank my Vista partition originally to divide my HDs into 5 separate partitions, putting my paging file on a partition on the secondary hard drive to speed up access, in effect turning the paging file off on my primary OS drive.  Even then I couldn't shrink it as much as I thought I should be able to and would have been able to with XP.

> Switch off pagefile and snapshots and defrag.

And then try Vista's partitioner again.

That is what I would try before using GParted.  Using GParted on a Vista partition is the last step I would advise you to take, considering the problems it has caused in the past, like rendering Vista completely unbootable.  It can probably be recovered, but not without a lot of work.

You really want to try to shrink Vista's partition with Vista's tool before trying something else.  More information on reducing the files in Vista (including snapshot files) can be found [on this page.]("http://www.mydigitallife.info/2008/02/26/how-to-fix-shrinking-disk-space-in-vista/")

> Your file system support is fine. It looks to me like you have some file system or disk errors on your NTFS drive. Boot to Vista and run Chkdsk, then defrag.

There are circumstances (and some messages in GParted will tell you this) that when you run CHKDSK, that you should reboot into Vista twice.  This is usually when Vista shuts down wrong, without completely unmounting the partition.  It wouldn't hurt to reboot into Vista twice after running the CHKDSK in this case, either.

Sorry it took me a bit to get back to you, but I was sick yesterday (still am, a little) and I really passed out yesterday afternoon and evening.

With all the above said...

I don't know what you have on your Vista partition, or how important it is to you, or what software you have that is paid for and can't be easily replaced, but the absolute easiest way to decrease the size of your Vista partition is with an installation disk.  In this way, you can delete your Vista partition, recreate it at the size you want it to be, create another "placeholder partition" where you want the free space for your Ubuntu partitions, and then install into the first Primary partition you created.

In most of my recent (I'm talking 1995 through present) desktop computers, this is the method I've always used to install Windows, so as to have space for other partitions.  Of course, those computers I either had special built or built myself so I had exactly the specs I wanted or required.  My present desktop I built myself from the ground up, and the one previous I might as well have.

If you don't have irreplaceable software and/or data, that would be a way to get as much space as you want while still having Vista available.  I almost never use Windows anymore, except for a couple of pieces of software that I just can't replace in Linux, and will not run under Wine (for instance, MS Flight Simulator X).

---

### Post by PhilGil on 2010-08-23
I'll defer to [-kg-]("http://ubuntuforums.org/member.php?u=662712")'s experience - take his advice and use the Vista partitioner instead of gparted.  Don't forget to run the disk check and defrag first, though.

---

### Post by protpisys on 2010-08-24
progress has been made, thanks to all this help...as suggested I ran disk check and the defragged w/the windows defragging deal. After that I was able to run gparted off the live disc and create a 30 GB +/- partition on my laptop's drive and vist still works. I seriously underestimated the time it would take, and today's a workday so I will attempt the reinstall when I get back tonight. All looks good thanks again.

---

### Post by protpisys on 2010-08-24
One more, I hope it's only 1 more...at least for this issue, queston. When I get to the disk partition screen during the install should I manually partition or let the system find the unused partition on it's own...it did a pretty good job of grabbing 1/2+ of my usb drive wouldn't it just assume the now open partition w/out any intervention from me? I feel the less I do the better things go. These are the things I think of on my AM commute. Thanks...

---

### Post by -kg- on 2010-08-24
You can use manual partitioning...read the "How To Partition" link in my signature block before you do so.  It's a good learning experience (if you want it at this point).

If you don't want to go through all that, when you get to the partitioning section of the installation, just choose "Install to largest contiguous free space" when you come to it, and as I said before, ***make _sure_*** you have it pointed to sda.  Since you don't have any free space on your USB drive, I don't think it will be a problem, though.  It will then automatically create the requisite partitions and install Ubuntu to the free space you created.

I personally *always* use manual partitioning, but then I have quite a bit of experience with partitioning (I substantially wrote the pages at the link in my signature block).  I do a lot of experimentation with various OSes and partitioning schemes, and currently have Fedora and OpenSUSE on my laptop, in addition to Ubuntu and Vista on this laptop.

I also have an autonomous Ubuntu installation on my external drive, bootable from that drive (as long as the target computer will boot to a USB device).

---

### Post by protpisys on 2010-08-24
If I have the usb drive unplugged, I shouldn't need to point anything anywhere as there'll be 1 option and 1 option only? I'm not taking any chances and have already, talk about anal, unplugged the external drive so as to avoid any further kerfufles

---

### Post by -kg- on 2010-08-24
That's right, unless you have another internal hard drive.  Of course, if you had another hard drive, it would have shown up long ago, with the "fdisk -l" command.

When you plug an external USB hard drive into the port, any partitions will automatically be mounted.  The mount point will automatically be under "Removable Drives", and you don't have to mark them at installation time. If that was necessary, you would need to go through Manual partitioning and manually mark the mount points of the partitions.

So you're safe if you remove the USB drive during installation.

---

### Post by protpisys on 2010-08-24
Success! It works without the usb drive mounted. My laptop is a laptop once again...I can't thank you enough for all the help. If you ever make it to Boston I'll buy you a beer. Thanks again

---

### Post by -kg- on 2010-08-25
You're welcome!  Glad I could help.

:smile:

---

### Post by Zimmer on 2010-08-25
Zimmer's Tip.... now you have a Laptop again :)

Right click on your Gnome Panel.. Add To Panel...  select the Disk Mounter.

Attached Disks / Partitions will then appear on the panel as icons and can be mounted/ unmounted from there...

---

### Post by protpisys on 2010-08-25
cool, thanks again for bailing me out...if you ever need the pion of someone who knows bupkus about it all look no farther.

---

