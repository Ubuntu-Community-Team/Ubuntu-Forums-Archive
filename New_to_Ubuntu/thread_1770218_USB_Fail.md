---
title: "USB Fail?"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by samms94 on 2011-05-28
So I'm completely new to ubuntu and non-windows computers...I have an old laptop (circa 2005?) with 2GB RAM, core duo but a failed hard drive. By failed hard drive I mean it seems completely corrupted or whatever the proper term is: the computer responds the same way regardless of whether or not it is even present. It doesn't boot. I am using Ubuntu because I have hopes of being able to use the laptop. I can't partition this hard drive and run it here because this is my only computer that definitely works (can't risk messing it up). 

I followed the steps to download 11.04 to a USB drive, I am able to get to the screen on the old laptop which gives me the option of running from USB, installing, etc. All options eventually lead me to the same conclusion: two lines of code then it says Uncompression error -- system halted. Is this due to my lack of a hard drive or a botched USB attempt? 

Any insight is appreciated

Just in case I wasn't clear, the laptop I'm hoping to install ubuntu on has no current OS or working hard drive.

---

### Post by wildmanne39 on 2011-05-28
> **samms94 said:**
> So I'm completely new to ubuntu and non-windows computers...I have an old laptop (circa 2005?) with 2GB RAM, core duo but a failed hard drive. By failed hard drive I mean it seems completely corrupted or whatever the proper term is: the computer responds the same way regardless of whether or not it is even present. It doesn't boot. I am using Ubuntu because I have hopes of being able to use the laptop. I can't partition this hard drive and run it here because this is my only computer that definitely works (can't risk messing it up). 

I followed the steps to download 11.04 to a USB drive, I am able to get to the screen on the old laptop which gives me the option of running from USB, installing, etc. All options eventually lead me to the same conclusion: two lines of code then it says Uncompression error -- system halted. Is this due to my lack of a hard drive or a botched USB attempt? 

Any insight is appreciated

Just in case I wasn't clear, the laptop I'm hoping to install ubuntu on has no current OS or working hard drive.
Hi, you can not install it because of the hard drive, but if you have the live version you can run it from the usb I think.

---

### Post by samms94 on 2011-05-28
> **wildmanne39 said:**
> Hi, you can not install it because of the hard drive, but if you have the live version you can run it from the usb I think.

how do I go about getting the live version, and is that 8GB USB drive still usable? The goal for me is to have the USB drive act as my hard drive. I only use my laptop for web surfing, so I don't mind not having 400GB of storage.

---

### Post by wildmanne39 on 2011-05-28
> **samms94 said:**
> how do I go about getting the live version, and is that 8GB USB drive still usable? The goal for me is to have the USB drive act as my hard drive. I only use my laptop for web surfing, so I don't mind not having 400GB of storage.
Hi, if you downloaded it from ubuntu's home page then it should be a live usb edition. Have you checked in your bios to see if it is set to let you boot from a usb device? Some bios do not allow you to boot from a usb. I did not know if 8 gigs is large enough for a full ubnutu edition or not.

---

### Post by samms94 on 2011-05-28
> **wildmanne39 said:**
> Hi, if you downloaded it from ubuntu's home page then it should be a live usb edition. Have you checked in your bios to see if it is set to let you boot from a usb device? Some bios do not allow you to boot from a usb. I did not know if 8 gigs is large enough for a full ubnutu edition or not.

It gives me an option to boot from USB, and that is my primary boot (#1 in boot order). Also, when I downloaded it, it was only 685 MB, so the 8GB should have been fine. What should I do?

---

### Post by samms94 on 2011-05-29
Here's the exact message I get when I run Ubuntu from USB:

Loading /casper/vmlinuz......
Loading /casper/initrd.lz...................ready

uncompression error

-- System halted

My goal is to have no internal hard drive use on the laptop. To accomplish this, do I need to partition my USB key? I'm at a loss as to what I need to do here in order to boot ubuntu

---

### Post by samms94 on 2011-05-29
:guitar:bump

---

### Post by oldfred on 2011-05-29
If you have an 8GB drive and want to use it as a full install, it would be better to do a full install. It sounds like your download is not correct or not copied correctly. I would do the mdsum.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I have a full install on a 16GB flash with the install in 8GB and the other 8GB set up as a data partition.

It does not have to be encrypted:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)

Install to a flash drive is like a second drive, but with some settings to reduce writes (above).
Installing Ubuntu in Hard Disk Two (or more) Maverick 10.10
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by samms94 on 2011-05-30
> **oldfred said:**
> If you have an 8GB drive and want to use it as a full install, it would be better to do a full install. It sounds like your download is not correct or not copied correctly. I would do the mdsum.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I have a full install on a 16GB flash with the install in 8GB and the other 8GB set up as a data partition.

It does not have to be encrypted:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)

Install to a flash drive is like a second drive, but with some settings to reduce writes (above).
Installing Ubuntu in Hard Disk Two (or more) Maverick 10.10
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

I don't really understand your post. I appreciate your efforts, but I just don't understand what I have to do. I re-downloaded 11.04 to the USB, and it successfully booted on a different device. I'm interested in how you were able to partition your USB to act as a storage; I think if I can do that it might boot. 

Here's a step by step of what I have done that hasn't been working. 

1: Download 11.04 to a USB by following the steps on ubuntu.com
I know I did this correctly because I was able to boot it on a different machine.
2: Insert USB into the desired laptop.
3: I get to the screen where it offers me 5 options, and I select Boot from USB disk.
4: It runs two lines of code, then says 'uncompression error -- system halted'.

Any insight is greatly appreciated

---

### Post by oldfred on 2011-05-30
I was suggesting doing a full install, not the version intended for 1 or 2GB flash drives that is the equalivalent to a LiveCD and used just for installing to a hard drive. You can add persistence to a liveCD version to get some data saved, but it is not a full install.

Pros & cons of persistent install over direct install to flashdrives 
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by samms94 on 2011-05-30
> **oldfred said:**
> I was suggesting doing a full install, not the version intended for 1 or 2GB flash drives that is the equalivalent to a LiveCD and used just for installing to a hard drive. You can add persistence to a liveCD version to get some data saved, but it is not a full install.

Pros & cons of persistent install over direct install to flashdrives 
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

So in other words, right now my USB drive is a LiveCD, which is different from a full install. You suggest I make it a full install. Am I correct so far? How can I get a full install onto my flash drive? Is there something to look for so I can differentiate between the two (liveCD vs. full install)?

---

### Post by oldfred on 2011-05-31
My post above has a link to Herman's site where he installs to a SSD or Flash drive. Settings are the same to reduce writes, just a SSD is a lot faster.

Flash install works as I have one. But USB port is not as fast as SATA and writes to Flash are slow. System is functional but not fast.

Herman has screen shots and an install to a flash is just like any install to a second drive, except you want to add a few settings to reduce writes.

Also see this post by C.S.Cameron nice list of commands to do:
[http://ubuntuforums.org/showthread.php?t=1771324](http://ubuntuforums.org/showthread.php?t=1771324)

This is just an install to a second drive.
Installing Ubuntu in Hard Disk Two (or more) Maverick 10.10
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

If you do not disconnect hard drive, then you have to use manual install or "Something Else" to get the option to install the grub2 boot loader to the MBR of the flash drive. Otherwise it installs the boot loader to the sda hard drive and you will have to have the flash installed to boot you hard drive.

---

### Post by cash1981 on 2012-08-26
I have the exact same problem.

The Live CD works on another computer but not the one that has failed.
I really need to backup the harddrive, and I only want to take it out and make it an external harddrive only if I have to.

I didn't really understand the alternative.
Did you fix the problem?

---

