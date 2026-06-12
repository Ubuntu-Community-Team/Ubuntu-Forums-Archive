---
title: "Resizing partitions on netbook"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by JamieWrites on 2010-12-17
Hi,

I've got an Asus netbook - **with no cd drive** - and am dual booting Ubuntu and Windows7. I want to resize my partitions because it seemed to just create them at random, and I really only need the absolute minimum for the Windows. 

But what little I can find online to explain how to do this is incomprehensible (to put it mildly). I tried downloading Gparted onto my netbook but couldn't find any way to actually bring up the interface; similarly, downloading Gparted onto a usb drive failed to do anything either.

Is there anywhere that has some clear, step-by-step and followable instructions on what to do? Alternatively, is there a way of changing the size of the partitions using the function already in Ubuntu? A screenshot of my disk space is attached.

---

### Post by akand074 on 2010-12-17
> **JamieWrites said:**
> I tried downloading Gparted onto my netbook but couldn't find any way to actually bring up the interface; similarly, downloading Gparted onto a usb drive failed to do anything either.

How did you download it? Go to Accessories > Terminal and run this:

```
sudo apt-get install gparted
```

Then it should come up in System > Administration > GParted Partition Editor

It's pretty straightforward from there. All you have to do is right click and edit each partition to whatever size you want it.

You never know what might happen, or if you make a mistake somehow. ALWAYS make a backup if you have anything your afraid to lose.

---

### Post by JamieWrites on 2010-12-18
Hi,

Okay, that's worked - but now I'm struggling to create a bootable USB  drive to be able to change anything useful. Screenshots attached of my  current drive statuses as well as my attempts at partitioning my USB.

If any knows a) what I need to do to make the USB work, that'd be great (again, all other instructions have been frustratingly useless) and b) how much memory I should allocate to each section - since I'm worried I've got 70GB I can't use - that'd be handy.

---

### Post by amjjawad on 2010-12-18
> **JamieWrites said:**
> a) what I need to do to make the USB work, that'd be great


[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

That's what you need. An Ubuntu's LiveUSB will do the needful.
You can't re-size unless you boot from a LiveCD/USB. Since you don't have a CD-Drive, then a LiveUSB.

> b) how much memory I should allocate to each section - since I'm worried I've got 70GB I can't use - that'd be handy.[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Edit:
You got unallocated space that you need to use and you also have sda2 which is not used as /home partition.
Try to read that link about Partitioning, hopefully you could come up with your own scheme ;)

---

### Post by JamieWrites on 2010-12-18
I'm a bit confused; I've got Ubuntu, and it works fine; all I want to do is move the currently unallocated space I've taken from the Windows section (since I'm dual-booting) to where I can use it.

Everything I've read tells me I can put a GParted .iso on my USB, boot from that, and then do the resizing I need to do.

---

### Post by amjjawad on 2010-12-18
> **JamieWrites said:**
> I'm a bit confused; I've got Ubuntu, and it works fine; all I want to do is move the currently unallocated space I've taken from the Windows section (since I'm dual-booting) to where I can use it.

You have some options. Either you format that unallocated space to NTFS and use it as a Data Partition so that both Windows and Ubuntu can access and use. If you're not using Windows and don't really care much about that idea so you could use that unallocated space as /home partition for Ubuntu. You still have 70GB unused. I know it's formatted to ext4 already but I don't think you're using it, right?

> 
Everything I've read tells me I can put a GParted .iso on my USB, boot from that, and then do the resizing I need to do.

You have two options: Either to use Ubuntu's LiveUSB because GParted is already there OR create a LiveUSB from that .iso for GParted which you downloaded.

---

### Post by JamieWrites on 2010-12-18
Well, I've tried putting the .iso of 10.04 on my USB (using PendriveLinux) and booting the netbook from that but it will not work. I've tried twice, doing everything that appears to be an option in the BIOS menu - and it just will not boot from the USB.

I can only assume there's a setting somewhere in the netbook that's not letting me boot from a removable device - despite my setting it as the no. 1 on the 'boot from' page - that I need to change.

Where else can those settings be controlled from?

---

### Post by candtalan on 2010-12-18
> **JamieWrites said:**
> I'm a bit confused; I've got Ubuntu, and it works fine; all I want to do is move the currently unallocated space I've taken from the Windows section (since I'm dual-booting) to where I can use it.

Everything I've read tells me I can put a GParted .iso on my USB, boot from that, and then do the resizing I need to do.
If you now also put a Ubuntu onto a bootable USB stick, and run your machine from it to get a live session of Ubuntu, then you will see that gparted is included in the live USB. System>Administration>partition editor gparted. And, because you are using full Ubuntu and not just gparted live, then you can see more if you wish. There is probably more support for Ubuntu live USB stick than there is for gparted live. There are other options. I tend to use parted magic live a lot, it also includes gparted, but I also use Ubuntu live too.

---

### Post by owiknowi on 2010-12-18
> **JamieWrites said:**
> Well, I've tried putting the .iso of 10.04 on my USB (using PendriveLinux) and booting the netbook from that but it will not work. I've tried twice, doing everything that appears to be an option in the BIOS menu - and it just will not boot from the USB.

I can only assume there's a setting somewhere in the netbook that's not letting me boot from a removable device - despite my setting it as the no. 1 on the 'boot from' page - that I need to change.

Where else can those settings be controlled from?

if your netbook is able to boot from usb it should be visible in its bios.

also try several usb ports. on my notebook i have the same problem with booting from USB sticks.
still don't know if it's a problem with the usb sticks or notebook.

---

### Post by amjjawad on 2010-12-18
> **JamieWrites said:**
> Well, I've tried putting the .iso of 10.04 on my USB (using PendriveLinux) and booting the netbook from that but it will not work. I've tried twice, doing everything that appears to be an option in the BIOS menu - and it just will not boot from the USB.

I can only assume there's a setting somewhere in the netbook that's not letting me boot from a removable device - despite my setting it as the no. 1 on the 'boot from' page - that I need to change.

Where else can those settings be controlled from?

Possible suggestions:

1) Check the manual for your machine to find out how to boot from USB

2) Check the md5sum for your .iso which you have downloaded. I assume that was your [first step]("http://www.facebook.com/note.php?note_id=152426241466147").

3) After that, format your USB Drive, create the Live USB from the iso file that you should have checked the md5sum for it and try to boot.

4) If nothing happened, try to use that USB on another machine just to double check.

5) Don't forget to backup your important data files before doing anything.


By the way, have you tried this: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

> **Burn your CD or create a USB drive**



It shows you in a very easy way how to create a Live USB.

---

