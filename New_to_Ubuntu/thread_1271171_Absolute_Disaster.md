---
title: "Absolute Disaster"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by babaji_mendez on 2009-09-20
Well I don't know what I have done wrong, but something hasn't worked right.

Just today I got the Linux Ubunto 9.04 CD put it into my laptop running windows vista and went ahead with the installer, 

I chose the option **demo and full installation**

The option  said I could try linux and dual boot to windows, if it wasn't for me,
so I did that, tried Ubuntu for a while, I liked it, but wanted to go back to windows
so I pressed Shutdown and restarted my computer...

Now when it restarted, whats happened? it doesn't give me the boot menu like before, it just goes straight into Ubuntu... :cry: Even if I press escape at startup, the only OS available is Ubuntu... **what can I do to get vista back?**

---

### Post by themusicalduck on 2009-09-20
First off, could you boot into Ubuntu, open a terminal from Applications > Accessories > Terminal. Type in ```
sudo fdisk -l
``` and post the results here.

---

### Post by Shazaam on 2009-09-20
It might still be there. Open terminal (Applications>Accessories>Terminal) and enter this...
```
sudo fdisk -lu
```
Fdisk will list all of your drives/partitions. When it asks for your password enter the one you chose during the Ubuntu installation and then press enter. You won't see any output as you type in your password so don't worry. Copy and paste the resulting text here.

---

### Post by babaji_mendez on 2009-09-20
Okay I will try that

---

### Post by babaji_mendez on 2009-09-20
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x60000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   476327249   238163593+  83  Linux
/dev/sda2       476327250   488392064     6032407+   5  Extended
/dev/sda5       476327313   488392064     6032376   82  Linux swap / Solaris
william@william-laptop:~$ 

That's the results... so, what can I do?

---

### Post by camper365 on 2009-09-20
When you went through the installer, did you select a guided disk partitioning or manual?
If you selected guided, did you select use entire disk or install side by side?
Were you able to choose Windows in the beginning?

---

### Post by babaji_mendez on 2009-09-20
I think it was guided, I don't know I didn't do anything on partitioning

Also I think I should mention, when I put in the vista install disk, it says not enough disk space, even though I have a 250GB hard drive

---

### Post by Shazaam on 2009-09-20
From looking at your fstab it seems as though Windows is gone. Try not to use the pc much longer as any recoverable Windows files may get overwritten.
There are a few tools out there you can try to use and there is also paid pc data recovery companies. The choice is yours. I don't have any experience with either so I will bow to others who may be able to help you.
If you don't have any critical files that you need recovered a fresh install of both Windows and Ubuntu might be in order.

---

### Post by babaji_mendez on 2009-09-20
Ok, no there isn't really any important files needing recovering, but when I try and install vista, it says there is no space... But I have way more than 405MB it says it requires

Also, I'm trying to run the vista setup with wine, is this right?

---

### Post by bobbob1016 on 2009-09-20
Stupid question, when you shutdown at first, you took out the CD, right?

Edit:  I should've read further than the first post before posting.  Boot back from the CD, and start GParted, press Alt+F2, then type "gksu gparted" without the quotes, delete every Linux partition it finds, and then Vista should be able to boot.

---

### Post by babaji_mendez on 2009-09-20
yes, it automatically ejected

---

### Post by babaji_mendez on 2009-09-20
sorry, I pressed ALT+F2 at startup it took me to some system maintanence screen, couldnt type anything in anywhere

---

### Post by Shazaam on 2009-09-20
I think bobbob1016 may be on to something. Put the Ubuntu livecd in and boot your pc with it. Then go to System>Administration>Partition Editor. When that opens see if the ext3 partitions equal the total size of the drive (roughly 250gigs).

---

### Post by babaji_mendez on 2009-09-20
I don't seem to have the partition editor, Also at startup, at what point do I press ALT+F2, at the dell logo, or when Ubuntu is loading?

---

### Post by babaji_mendez on 2009-09-20
right, I got the partitio editor, yes, the ext3 = 227GB altogether, 

What can I do now, do I delete the partition, or...? I need help with this, I have next to no experience with computers

---

### Post by lovinglinux on 2009-09-20
> **babaji_mendez said:**
> Also, I'm trying to run the vista setup with wine, is this right?

No, that's the problem. You can't do that.

You need to put the Vista DVD and restart the machine, to boot from the DVD.

---

### Post by piyushverma82 on 2009-09-20
you have to delete the linux partitions (ext3 partitions) for vista to read them,
vista cannot read the ext3 file system therefore its showing not enough disk space

---

### Post by babaji_mendez on 2009-09-20
That didn't work at all, I put the CD in, pressed restart, but it just went straight into ubuntu again,


Okay, It wont let me delete the ext3 partition

---

### Post by piyushverma82 on 2009-09-20
put the vista dvd in and restart

---

### Post by babaji_mendez on 2009-09-20
nothing happens if I do that, it just starts up ubuntu

So Vista CD will run if I delete ext3? But Gnome partition editor isnt letting me do that, It wont unmount

---

### Post by piyushverma82 on 2009-09-20
Ithink your BIOS is not set for boot from cd, change the boot order from BIOS to boot from cd first, then boot from ubuntu cd to delete the ext3 partitions

---

### Post by Paqman on 2009-09-20
> **babaji_mendez said:**
> Ok, no there isn't really any important files needing recovering, but when I try and install vista, it says there is no space... But I have way more than 405MB it says it requires


You'll need to create a partition to install Vista in. Boot up into your LiveCD, go to System > Admin > Partition Editor and use it to shrink your Ubuntu partition, leaving at least about 20GB of free space at the start of the disk. 

> 
Also, I'm trying to run the vista setup with wine, is this right?

No, you want to boot up into the Vista disk.

---

### Post by babaji_mendez on 2009-09-20
I'm in the partition editor, but I cant delete / move / resize anything...
it just wont let me

---

### Post by Shazaam on 2009-09-20
You need to make sure your pc will boot from cd/dvd first. When your pc first boots try holding down the delete key. If that doesn't work try either the F2 or F12 keys. You need to find the boot sequence (boot order) menu and change it so cd/dvd (or optical drive if it is listed as such) is first. Then find where it says "Save and Exit" and press enter. Put the Vista disk in and it should boot to that.

---

### Post by ubuntnoob512 on 2009-09-20
I have the same problem exept with Win xp 32 bit pro and ubuntu 8.04

i will try that

here is my post:

[http://ubuntuforums.org/showthread.php?p=7980579#post7980579](http://ubuntuforums.org/showthread.php?p=7980579#post7980579)

---

### Post by ubuntnoob512 on 2009-09-20
how do you make that back slash ish symbol?

it is a part of what i have to type in termonol

---

### Post by gradinaruvasile on 2009-09-20
> **babaji_mendez said:**
> I'm in the partition editor, but I cant delete / move / resize anything...
it just wont let me

Boot from the ubuntu live cd. And then launch gparted. Then delete the partitions.

---

### Post by Paqman on 2009-09-20
> **babaji_mendez said:**
> I'm in the partition editor, but I cant delete / move / resize anything...
it just wont let me

Are you using the LiveCD? Are the partitions locked with a little key symbol? If so, right click on your swap partition and "swapoff". You should then be able to alter your partitions.

By default the LiveCD looks for and mounts any available swap partitions (to improve performance) but if your swap is inside an extended partition it can have the effect of preventing the partition editor from making changes.

---

### Post by ubuntnoob512 on 2009-09-20
how do i make this symbol?

l

---

### Post by Liolikas on 2009-09-20
Depends on keyboard maybe for me it is: shift+\ and "~ #" painted on button. LoL. Just try shift + everything not letters.

---

### Post by piyushverma82 on 2009-09-20
like this"|" 
lol

sorry jokes apart press "shift + backslash"

---

### Post by ubuntnoob512 on 2009-09-20
What?

this is what I get after typig in termonol what it says on page 1 in this forum

[sudo] password for aaron: [sudo] password for aaron: [sudo] password for aaron: bash: u: command not found

---

### Post by piyushverma82 on 2009-09-20
its not "|" its  "l" as in little (small L)

---

### Post by ubuntnoob512 on 2009-09-20
well that helps

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe5cfe5c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13630   109482943+   7  HPFS/NTFS
/dev/sda2           13957       14593     5116702+   7  HPFS/NTFS
/dev/sda3           13631       13956     2618595    5  Extended
/dev/sda5           13631       13934     2441848+  83  Linux
/dev/sda6           13935       13956      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Shazaam on 2009-09-20
*types softly*
ubuntnoob512 please don't hijack babaji_mendez thread.

---

### Post by ubuntnoob512 on 2009-09-20
Wow, i dont know how to hijack a thread. Talk in english please. Do you mean like hack it?

---

### Post by Shazaam on 2009-09-20
We were trying to help babaji_mendez. You are here with another (different) problem from another thread. Someone there is trying to help you.

---

### Post by roger_1960 on 2009-09-20
Hi babaji_

As per an earlier post, possibly the problem is that your BIOS is not set to boot from DVD/CD first.  To check this, reboot and immediately press F2 or F8 (normally, but it depends upon the machine) and you should get a screen giving BIOS setup options.  The boot order should be set so that DVD/CD is first.  If this is done the MS install disc should work (and overwrite the whole hard drive) when in the drive before rebooting.

---

### Post by corncob on 2009-09-20
> **roger_1960 said:**
> Hi babaji_

As per an earlier post, possibly the problem is that your BIOS is not set to boot from DVD/CD first.  To check this, reboot and immediately press F2 or F8 (normally, but it depends upon the machine) and you should get a screen giving BIOS setup options.  The boot order should be set so that DVD/CD is first.  If this is done the MS install disc should work (and overwrite the whole hard drive) when in the drive before rebooting.

On my computers pressing ESC on bootup gives me the list of bootable devices which I can choose to boot from --- HDD0, HDD1, CD, USB Drive, etc.  I don't know exactly when to press it but holding it down when I hit the on switch seems to work.

---

### Post by roger_1960 on 2009-09-21
Hi again

Probably the "CD" device is the DVD/CD drive.  Try it, the setting can be changed back if wrong. (Make a note of what is first before you change it)

---

