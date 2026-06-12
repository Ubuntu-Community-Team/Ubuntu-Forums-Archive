---
title: "Ubuntu Installer Doesn't Detect Hard Drive"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by conkermaniac on 2011-08-23
Hi everyone,

I'm new to Ubuntu. I recently got Windows 7 up and running on a new computer, and I'm interested in dual booting Windows and Ubuntu. I would like to get both operating systems on my SSD, but for some reason the Ubuntu installer defaults to my HDD, which I would like to keep for storage. Is there any way I can get Ubuntu to detect my SSD short of detaching the HDD while I install?

(By the way, I did try searching the forums, but I wasn't quite sure how to search and thus didn't find anyone who had asked a similar question before.)

Thanks!

---

### Post by llamabr on 2011-08-23
Sorry for the stupid question, but what's SSD and what's HDD?

Also, you mention disconnecting HDD during install.  That's what I'd suggest.  Why don't you want to consider that?  Then, just update /etc/fstab after your install to recognize HDD.

---

### Post by oldfred on 2011-08-23
You should just be able to select either drive. Have you used all 4 primary partitions? Did you leave space for Ubuntu on the SSD?

to see your partitions & drives post this:
sudo fdisk -lu

---

### Post by conkermaniac on 2011-08-24
Sorry, should have been more clear:
SSD = solid state drive
HDD = hard (disk) drive

I would like to run both OS on the SSD for performance reasons.

Oldfred: There is plenty of space on the SSD for Ubuntu, although I haven't made a separate partition for it. I could, but I was under the impression that the Ubuntu installer would detect Windows and take care of the partitioning?

I'm not at home right now, but I will check out the partitions when I get home.

Thanks again for all your help!

---

### Post by Mark Phelps on 2011-08-24
You probably won't need it -- but better to be safe rather than sorry ... So, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  That will come in handy later should you need to repair or restore the Win7 Boot Loader and your current MBR.

Also, I would disconnect the HDD when installing Ubuntu.  This will prevent the Ubuntu installer from writing GRUB to the wrong drive.

---

### Post by conkermaniac on 2011-08-24
Thanks for the advice. I will disconnect the hard drive before installing Ubuntu. My other question was: should I carve out a partition to install Windows on, or am I right in thinking that the Ubuntu installer will partition the disk for me?

---

### Post by oldfred on 2011-08-24
Automatic install just creates / (root) & swap. I always partition in advance so I can control the sizes of partitions. If you are planning windows it would be best to install it first. Windows has to have a primary partition formated NTFS with the boot flag or unallocated space with a primary partition available.

Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by conkermaniac on 2011-08-27
After shrinking the size of the Windows partition and detaching the hard drive, the Ubuntu installer *still* wouldn't detect my SSD. I found an old thread ([http://ubuntuforums.org/showthread.php?t=1608255](http://ubuntuforums.org/showthread.php?t=1608255)) that suggested that I use the alternate install, with acpi=off. That seemed to work, but....

The first time, I was able to partition the disks as you suggested (thanks!) and start the installer, but it froze at "Installing core components." The next couple of tries, I've had problems even loading the partitioner. I've checked the MD5 and the integrity of the CD files, and it all seems to be fine. Any ideas what else could be going on here?

---

### Post by oldfred on 2011-08-27
Are you booting with BIOS or UEFI? UEFI is for new computers & win7 will work with gpt partitions and UEFI. Grub is still a work in progress with UEFI. Some have issues, others get it to work.

If CD is good, then it could be some other BIOS setting? Not sure what else to check.

---

### Post by conkermaniac on 2011-08-27
Yes, I'm booting with BIOS.

I managed to get back to the installer (it turned out that the partitioner just takes a very long time to load), but again it freezes when it gets to "Installing Core Components" (31%). Actually I saw a thread last night where someone had a similar problem, but I can't seem to find it anymore....

Also, I ran the CD's own checker, and everything checked out. That should mean that the CD is fine, right?

---

### Post by oldfred on 2011-08-27
CD seems like it must be ok.

My gparted is slow and was a lot slower until I ran chkdsk on my NTFS partition. You could try chkdsk on all NTFS partitions to see if that makes a difference. (note that I am grasping at straws, as I do not have a good answer).

---

### Post by conkermaniac on 2011-08-27
Aha, waited long enough and finally an error shows up:

Debootstrap warning

Warning: Failure trying to run: chroot /target dpkg --force-depends --install
/var/cache/apt/archives/base-files_5.0.Oubuntu28_amd64.deb
/var/cache/apt/archives/base-passwd_3.5.22_amd64.deb

When I press "Continue", I get:

Base system installation error

The debootstrap program exited with an error (return value 1). 

Check /var/log/syslog or see virtual console 4 for the details

---

### Post by conkermaniac on 2011-08-27
This thread looks like it might be relevant:

[http://ubuntuforums.org/showthread.php?t=1136329](http://ubuntuforums.org/showthread.php?t=1136329)

I'm going to try the suggestions: unplugging the network, use ext3 instead of ext4

---

### Post by conkermaniac on 2011-08-27
Okay, the following settings seem to have gotten me passed the base installer, at least:

- acip=off
- noapic
- unplugging the network and configuring manually
- using ext3 instead of ext4 file system

Not sure which of those did the trick -- didn't have the patience to try them one by one :P

Now the installer hangs at 50% trying to install GRUB. I found other people who had similar problems here ([http://ubuntuforums.org/showthread.php?t=11017](http://ubuntuforums.org/showthread.php?t=11017)). It seems that creating a separate boot partition worked for them. Any suggestions on how to do this? How big should it be?

---

### Post by oldfred on 2011-08-27
It was only really old system that had a 137GB boot limit in BIOS that needed the /boot. We have seen some large hard drives 500GB or more where having just a large / (root) partition seemed to give the same error. Some worked when they made / smaller others just reinstalled or just reinstalled grub2's boot loader. Do you have a very large root? I think it is a BIOS setting or there is  a grub issue with some systems when boot files are  over 1TB on drive.

If you do a /boot it can be anything from 200mb to 500mb, but if smaller you may have to regularly house clean out older kernels, which I prefer to do anyway. And if you create a /boot make it near the beginning of the drive.

---

### Post by conkermaniac on 2011-08-27
My / (root) partition was 15 GB, which is within the range you recommended. That doesn't seem particularly big to me, or is it?

Okay, it seems that I've really messed things up now....I cleared all the partitions and tried to repartition the drives with a smaller / (root). Now the disk partitioner is stopping me with the errors:

end of file while reading Invalid argument
Invalid argument during seek for read on /dev/sda
Invalid argument during seek for write on /dev/sda
No space left on device during write on /dev/sda
Failed to create a swap space

It sounds like time to start over, beginning with reinstalling Windows? (The disk partitioner doesn't even detect the file systems on the Windows partitions as ntfs anymore.)

---

### Post by oldfred on 2011-08-27
I typically recommend 10 to 20GB for /. 

Have you checked hard drive with disk Utilitly and looked at Smart Status? It sounds like you may have hard drive issues if everything stops working at once. Other wise Windows chkdsk on ntfs partitions and Linux e2fsck on ext type partitions, but you should not be having all these issues.

---

### Post by conkermaniac on 2011-08-28
*Never mind what I wrote before. I didn't realize that Windows allows you to modify the partitions when you install. I'm re-installing Windows now.

By the way, thank you oldfred for your patience. You have been tremendously helpful, and as frustrating as this all has been, I have also learned a lot from the experience.

---

### Post by conkermaniac on 2011-08-28
Okay, I re-installed Windows and Ubuntu (it turns out it was the ext4 file system that had been causing the installer to freeze at "Install core packages" earlier), and when it asked whether I wanted to install GRUB, I opted out.

Now when I start up the computer, I get "No operating system detected." Huh? If I didn't install GRUB, nothing should have happened to the Master Boot Record, right?

(One thing I should mention is that when I partitioned the disks in the Ubuntu installer, I chose to make /(root) bootable. Was this a mistake?)

---

### Post by oldfred on 2011-08-28
That may be why windows does not boot. Window MBR code looks at the partition table for the active partition which in Linux we see as the boot flag. Windows then jumps to that partition boot sector to continue to boot. If Ubuntu is in a primary partition and you installed grub2's boot loader to the partition I have seen windows boot grub from the partition. 
But windows will not directly boot from a logical partition.

I suggest keeping boot flag on NTFS partition that has Windows. Grub does not need it. A few BIOS (mostly Intel motherboards) want to see a boot flag and will not let you boot at all without a boot flag on an active partition even though grub does not care.

If you want the details of where everything is installed:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by conkermaniac on 2011-08-28
Thanks. Unfortunately, I have no way of using the Boot Info Script, as the Live CD version of Ubuntu does not detect my SSD. Ubuntu is installed, but I don't know how to get to it.

Right now the boot flag is on an Ubuntu primary partition, which I suppose is the problem because I didn't install Grub yet. Is there any way I can change the boot flag without going through the hassle of re-installing Windows and Ubuntu?

---

### Post by oldfred on 2011-08-28
You can use gparted, Disk Utility, command line or windows to set boot/active partition. But you have to have a windows repairCD or Ubuntu liveCD that can see drive.

---

### Post by conkermaniac on 2011-08-28
Okay, I think I've installed everything successfully. Here's what I ended up doing:

Set the Windows 100 MB System Reserved partition to active.
Installed Ubuntu 11.04 with a 256 MB /boot partition.
Installed Grub to /boot.
Installed EasyBCD which allows me to dual-boot.

So here's what works so far: I turn on the computer, I see the Windows Boot Manager asking me whether I want Windows 7 or Ubuntu; if I choose Windows 7, Windows loads just fine, if I choose Ubuntu, I am taken to the Grub menu.

Unfortunately, when I select Ubuntu from the Grub menu, all I get is a blank screen with the crimson background. There is no cursor. This is before I've had the chance to log in or anything. Loading Ubuntu in recovery mode takes me to the shell, where I get the following error which seems relevant:

Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)

I would like to run Boot Info Script, but I would need to install and run it from the shell, which I'm not sure how to do.

I should also mention: I initially installed Grub to the wrong partition (the root partition). I followed the instructions [here](http://superuser.com/questions/104921/ubuntu-9-10-grub2-installed-on-the-wrong-partition-no-booting-macbook) (the first method suggested by the answerer) to reinstall it to the /boot partition, but perhaps this was a mistake?

Grrr...I feel so close to getting this to work. It shouldn't be long now, and I can't wait to actually start playing around with Ubuntu.

---

### Post by glitter_gulch on 2011-08-28
You have an SSD you might not have the space. I would also try gparted to split the drive the windows partition maker is not the greatest. 

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by oldfred on 2011-08-29
You can run boot info script from Ubuntu liveCD and many other Linux repair CDs.

I do not know much about EasyBCD. A few here with Win7 do use it and seem to think it is pretty good. I still have XP and only rarely boot XP now anyway.

---

### Post by Mark Phelps on 2011-08-29
EasyBCD is constantly changing -- and is now into Beta version 2.1.1 build 148.  So, solutions that would (or would not) work six months ago could get completely different results today.

Thus, if you have questions about what settings to use in easyBCD, you should go to the NeoSmart Technology forums and post there.

---

### Post by conkermaniac on 2011-08-29
It's not an EasyBCD problem. It gets me into Grub2 just fine. What happens is that when I try to load Ubuntu from Grub2, all I get is a blank red screen. No log in or anything.

It seems that everyone recommends diagnosing with the Live CD. I can't do that because the Live CD doesn't detect my SSD, and I installed Ubuntu from the alternate install with the option acpi=off. I partitioned my drive (200 MB /boot, 15 GB / (root), 33.3 GB /home, 8.6 GB swap), and followed all the instructions, installing GRUB to the boot partition. The installation seemed to go through fine. Yet I still can't seem to load Ubuntu.

Is there some configuration step that I'm missing here? I would like to run something like Boot Info Script to post here, but I can't because Live CD doesn't work for me.

---

### Post by oldfred on 2011-08-29
If you now get grub's menu, you probably are past boot issues and boot script may not tell much.

Next issue many have is video related. What video card do you have. I have nVidia and on first boot I have to add nomodeset to linux line in grub menu. Then after loading the nVidea driver it works without issue.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by conkermaniac on 2011-09-02
Still no luck. I think the Linux kernel isn't booting. I took a look at the boot options and I apparently have:

```
acpi=off  quiet splash vt.handoff=7
```

I have tried removing acpi=off and adding nomodeset. (I have a GeForce 400 Series GTS450 graphics card, by the way.) When I add --verbose text as suggested by the first thread recommended by oldfred, the only message I get that remotely resembles an error message is:

```

Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/9a50d971-1242-4899-beb5-02f0277bcc7d does not exist. Dropping to a shell!

```

Then I am taken into BusyBox. Can anyone else make sense of this? :(

---

### Post by oldfred on 2011-09-02
Run the boot script anyway as suggested in post #20. It still seems that grub and as you mentioned the liveCD, are having issues with correctly seeing your SSD. I just want to see what boot script shows.

Did you ever have RAID installed on SSD or used gpt not MBR for partitioning? Left over bits on hard drive can cause issues. We saw one brand new hard drive that had RAID data on it and once that was removed then it worked.

---

### Post by conkermaniac on 2011-09-04
> **oldfred said:**
> Run the boot script anyway as suggested in post #20. It still seems that grub and as you mentioned the liveCD, are having issues with correctly seeing your SSD. I just want to see what boot script shows.
Could you give me a pointer on how to install and run the boot script entirely from the shell?

> 
Did you ever have RAID installed on SSD or used gpt not MBR for partitioning? Left over bits on hard drive can cause issues. We saw one brand new hard drive that had RAID data on it and once that was removed then it worked.
Not to my knowledge. The SSD is new, and I ran DBAN on it, which should have wiped out any RAID data, right?

---

### Post by oldfred on 2011-09-05
The boot script is a bash script and has to be run from a terminal. I do not think it works from boot shell.

Yes I also think dban would have totally erased drive.

---

