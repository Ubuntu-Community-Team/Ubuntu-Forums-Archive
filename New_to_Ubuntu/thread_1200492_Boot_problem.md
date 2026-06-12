---
title: "Boot problem"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by samfoster on 2009-06-30
Hi guys, very new to Ubuntu, literally never used it before.  Here's the problem:

I installed Ubuntu to my laptop with the intention of dual booting Vista and it, with Ubuntu for everyday stuff and Vista predominantly for music production.  Installation itself went fine, but when I was attempting to set up my bootloader of preference, I inadvertently restored Vista's bootloader. 

The effect of this was to disable GRUB before I had copied the menu.lst info for Ubuntu.  Thus, now I can't boot Ubuntu at startup by selecting anything.

Is there another way to launch Ubuntu?  

My friend recommended Vmware, which apparently would allow me to run Ubuntu, get the file, and then fix my problem.  This raises a further problem though, I don't know how to use Vmware, or if it's even freeware and if there are multiple versions of it.

If I can fix this problem, I am pretty much set.  I'd really appreciate anyone's help.

---

### Post by Paqman on 2009-06-30
Check out EasyBCD for Vista, it'll allow you to set the Windows bootloader to chainload Grub, and therefore your Ubuntu system.

---

### Post by samfoster on 2009-06-30
That's what I was trying to configure, or rather, why I needed the menu.lst file in Ubuntu.  I need the Linux boot options to configure NeoGrub's own menu.lst in order to make it work.

To clarify, I was following this tutorial: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4)

---

### Post by Paqman on 2009-06-30
So you need the contents of a menu.lst file that will work on your machine?

You'll need to know a couple of things things: 

[list]
[*]what partition your Ubuntu install is on
[*]what kernel you need to boot
[*]UUID of the correct partition
[/list]

Boot up into a LiveCD/USB of Ubuntu and navigate to /boot on the Ubuntu partition to find out the kernel you've got. Then run:
```

blkid

```
to find out the UUID of the right partition. Copy those values into your new menu.lst and place it in /boot/grub.

---

### Post by samfoster on 2009-06-30
The Ubuntu install is on the Vista partition.  I know that, because the tutorial lead me through the process to shrink it so that Ubuntu would occur the spare space.

When you say to boot from the LiveCD, what option should I select from the menu to boot from my hard drive?

---

### Post by Paqman on 2009-06-30
> **samfoster said:**
> The Ubuntu install is on the Vista partition.  I know that, because the tutorial lead me through the process to shrink it so that Ubuntu would occur the spare space.


Sorry, I don't quite understand. If Ubuntu was on the Vista partition, that means you used the Wubi installer, which involves no shrinking of partitions. If you did shrink your Vista partition, then Ubuntu will be on a new partition created in the space you created.

Just let the LiveCD boot into a live session, it's the default option, which IIRC is something like "Try Ubuntu without altering my system"

---

### Post by samfoster on 2009-06-30
Okay, I think you are correct in your assumption and that my understanding is faulty, because my new information supports what you just said.

So, I used the install section of the LiveCD to work out the partition that it's installed too.  I got this "/dev/sda3".  So, thus, I assume SDA3 is the name of the partition.

Booted into a live session, the kernel is "2.6.28-11-generic".

Now, I ran into some problems with the UUID.  If it is indeed installed on partition sda3, the UUID is "121C4C471C4C2855".  However, this doesn't bear any resemblance to the form of the UUID on the tutorial I followed, while two other partitions did.

SDA5: ba407772-4f23-492e-bae7-5c87e559a8ec
SDA6: 2d284a86-e921-45f0-be37-7fcca6eede4a

Can you shed any light on this?  If you can determine which I should use, I can substitute them into the code for EasyBCD.

---

### Post by -kg- on 2009-06-30
Believe Paqman...you have an Ubuntu partition (two, actually...a "/" (root) partition and a swap partition).  That's what the partitioner on the Live CD does.  Once you have shrunk the Vista partition and created the free space, the partitioner, upon having selected "Use Largest Contiguous Free Space," creates your Ubuntu partitions in that free space.

Boot to your Live CD, Open the terminal (under "Applications/Accessories") and run the command:

```
sudo fdisk -l
```

(That's a lower-case "L", not a one)

This will list all the partitions on your hard drive(s).  You will notice that you have an sda1 (or hda1, as the case may be) that will be ntfs (that will be your Vista partition or, depending on whether you have a recovery partition, it might be s- or hda2) and the next partitions will be ext3 and swap.  You might have an Extended partition...it depends.

You can find out more about partitions by reading at the link in my signature block.

---

### Post by -kg- on 2009-06-30
OK, I just read your newest post.  Is sda3 an ext3 partition or is it an Extended partition?

---

### Post by samfoster on 2009-06-30
Okay, this may have solved the problem:

sda1 - unknown
sda2 - hpfs/ntfs (so presumably, main vista partition)
sda3 - hidden hpfs/ntfs
sda4 - extended
sda5 - linux
sda6 - linux swap/solaris

So, I'm assuming that sda5/6 are the two Ubuntu partitions, and that sda5 is the root.  Would that be correct?

---

### Post by -kg- on 2009-06-30
Yep, that's the one.  You're on your way.

I have to go to work now, but someone will undoubtedly be along to help you further if you need it.

---

### Post by samfoster on 2009-06-30
I appreciate your help, thank you so much.

Can anyone confirm if adding this to the EasyBCD Neogrub menu.lst will solve my problems:

```
    title                  Ubuntu 9.04, kernel 2.6.28-11-generic
  uuid                 ba407772-4f23-492e-bae7-5c87e559a8ec
  kernel              /boot/vmlinuz-2.6.28-11-generic root=UUID= ba407772-4f23-492e-bae7-5c87e559a8ec ro xforcevesa quiet splash
  initrd                /boot/initrd.img-2.6.28-11-generic
   
  title                  Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
  uuid                 ba407772-4f23-492e-bae7-5c87e559a8ec
  kernel              /boot/vmlinuz-2.6.28-11-generic root=UUID= ba407772-4f23-492e-bae7-5c87e559a8ec ro xforcevesa single
  initrd                /boot/initrd.img-2.6.28-11-generic
   
  title                  Ubuntu 9.04, memtest86+
  uuid                 ba407772-4f23-492e-bae7-5c87e559a8ec
  kernel              /boot/memtest86+.bin
  quiet 
  
```

EDIT:

I just tried that code and got an Error 17: File not found message.  I believe that something is iffy with the kernel, or perhaps the location from which it is trying to boot.  I will try the other Linux partition and see if it works.

I don't understand why the above doesn't work, though.  It was copied directly from the menu.lst in Ubuntu itself when I loaded it from the LiveCD, I copied it onto a flash drive and just inserted it into EasyBCD.

---

### Post by Paqman on 2009-06-30
> **samfoster said:**
> 
I don't understand why the above doesn't work, though.  It was copied directly from the menu.lst in Ubuntu itself when I loaded it from the LiveCD, I copied it onto a flash drive and just inserted it into EasyBCD.

Could well be that the kernel the LiveCD is booting and the one your installed copy is booting are different maybe? When you're in the LiveCD, navigate to the actual partion on the disk (through the places menu, it'll just show up as what size it is) then into the filesystem /boot menu to check what kernel you've got.

That xforcevesa option on your boot line looks a bit iffy, too. I think that's a safe graphics mode.

---

### Post by samfoster on 2009-06-30
I've been running it always in a safe graphics mode, because otherwise I just end up with a black screen.

That kernel was gained the way you just suggested I try, so I'm not sure what else I can do.

Any thoughts?

EDIT: I tried removing the "xforcevesa" option in the boot line to see if it did anything, but no luck.  I'll try changing the UUID to the other Linux partition and cross my fingers.

---

### Post by Paqman on 2009-06-30
> **samfoster said:**
> 
Any thoughts?

Double-check your UUIDs? If that's not it i'd probably reinstall Grub from scratch, just to be sure. [Super Grub Disk]("http://www.supergrubdisk.org/") is worth having a copy of for stuff like this.

---

### Post by samfoster on 2009-06-30
UUID's are okay, just double checked them.  Switching the UUID in the boot line didn't make any difference.

I can reinstall Grub without having to reinstall Ubuntu completely, right?  If I make a Super Grub Disk, can I install it on Windows to override the Vista bootloader and access either Ubuntu or Vista again?

EDIT:

Well, I tried using Auto Super Grub Disk and it began okay, but at one point when it was running a command it appeared to simply cease any kind of actual function.  The computer showed no hard drive activity, so I restarted it without completion.  Perhaps it just takes a long time, and I will need to leave it on overnight, but I wouldn't imagine this to be the case.

Can anyone clarify?

---

### Post by samfoster on 2009-06-30
Okay, well, I left Auto Super Grub Disk on all night and it just locked up running a boot command again.

Using the LiveCD, can I uninstall Ubuntu completely from the system?  If I reinstall from scratch, none of this will be an issue.

Really, I just need to restore GRUB and it's proving so difficult that I might as well just reinstall if I can.

---

### Post by -kg- on 2009-06-30
Oh, what a day!

Looks like you've had further trouble.  My idea would be to just reinstall GRUB, which it looks like you've been trying to do.  The following guide might be a help:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

It has multiple methods on reinstalling GRUB after overwriting it with the Windows Bootloader, including specifics on the Auto SuperGrub disk, with links to other resources at the bottom of the page.

Frankly, unless you just want to play around with loading Ubuntu with EasyBCD and the Vista bootloader, I would leave GRUB in the MBR.  That's what I did with this laptop (and my desktop) and it works perfectly well.  It is completely customizable (especially by loading "Startup Manager" from the repositories...launch Synaptics and look for "startupmanager" and install it) and will launch Vista as well as Ubuntu just fine.  You won't have mouse support (does Easy BCD and the Vista Bootloader?  I never even tried it) but it works fine.

---

### Post by -kg- on 2009-06-30
OK, you posted while I was writing! :lolflag:

Yes, I was going to suggest that, but I thought you might be experimenting, and I always encourage experimentation as a way to learn. ;)

Yes, absolutely you can get rid of the current installation and reinstall.  Just launch the Live CD to the desktop, select "System/Administration/Partition Editor," and when your disk comes up, delete all the partitions that are associated with Ubuntu (sda5 and sda6, then sda4...you will need to do it in this order, since you can't delete an Extended partition until all the Logical partitions inside it are deleted).  Apply the operations with the appropriate button at the top of the GPartEd screen and, once the operations are complete, close GPartEd and start the installation.

If you are interested in just what you are doing with GPartEd, read some at the link in my signature block.

---

### Post by samfoster on 2009-07-01
Well, I just tried to reinstall GRUB by overwriting the Windows Boot Loader.  Despite it looking successful, and according to Ubuntu it being successfully reinstalled, upon rebooting my machine there was no joy, only Windows complaining that there had been a problem during start-up and no option for Ubuntu.

This has become very frustrating.

If I erase the Ubuntu partitions, the contents of the other partitions won't be affected, right?

EDIT:

Also, GpartEd?  Is this the partition editor in Ubuntu, or other software I must download?

---

### Post by -kg- on 2009-07-01
Yes, Partition Editor in Ubuntu is GPartEd (Gnome Partition Editor).  And yes, as long as you select the correct partitions for deletion, it will leave the other partitions alone.  Just make sure you select the correct partitions.

That is why you have the "Apply" button at the top of the GPartEd Screen.  When you set a (or some) partition operation(s), they will not be immediately applied.  This is to give you a chance to make sure that you've set the operations properly, and on the proper partitions, before you start these operations.

You can set up a series of them (like deleting all the partitions at the same time) or one at a time, clicking the "Apply" button after setting each one up.  In the case of simply deleting the selected partitions (one of the easiest, safest operations a partition editor can perform), multiple operations are OK, but you might want to do them one at a time if for nothing else, so you can see how GPartEd works for future reference.

Read the information at the link in my signature block.  It will show you what you're doing when you perform these operations and is good knowledge to have for further types of operations you may need or want to perform.

---

