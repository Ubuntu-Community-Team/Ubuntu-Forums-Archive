---
title: "Grub does not load properly, gives black screen with command prompt instead"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by Space-Wolf on 2009-11-24
I'm using wubi to install, and I've already tried uninstalling it and reinstalling, but the same problem continues to happen.  I select ubuntu in Windows Boot Manager, then instead of grub popping up and letting me choose ubuntu, it just has a black screen that says "Grub GNU 1.97 beta" or something of the like, and a box that says [Minila BASH-like.....] something and then I can enter commands.  I can't get it to boot properly though.  Can anyone help?

I'm using an acer netbook if that makes a difference...

---

### Post by Sealbhach on 2009-11-24
Hi, the first thing to try I think would be to reinstall Grub. The problem is you need a Live CD for that, which you probably don't have if you used Wubi. These are the instructions on how to do it, if you can get a Live CD:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Just one question, at the command line you get, what does it say before the prompt, is it your username or is it  *"grub-rescue>" *or is it "grub>" ?


.

---

### Post by Space-Wolf on 2009-11-24
My netbook doesn't have a disc drive, so is there any way to use a usb drive or something to install it?  And I believe it says grub.edit before the command thing.  This is trange because the exact same version of wubi worked perfectly on my Sony Vaio laptop, but it won't work on this netbook.

---

### Post by Sealbhach on 2009-11-24
> **Space-Wolf said:**
> My netbook doesn't have a disc drive, so is there any way to use a usb drive or something to install it?  And I believe it says grub.edit before the command thing.  This is trange because the exact same version of wubi worked perfectly on my Sony Vaio laptop, but it won't work on this netbook.

Yes, you can use Unetbootin to make a bootable USB drive: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You can get the Live CD iso here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by teward on 2009-11-24
> **Space-Wolf said:**
> My netbook doesn't have a disc drive, so is there any way to use a usb drive or something to install it?  And I believe it says grub.edit before the command thing.  This is trange because the exact same version of wubi worked perfectly on my Sony Vaio laptop, but it won't work on this netbook.

download netbook remix and burn it to a flash drive with another computer.

---

### Post by Space-Wolf on 2009-11-24
I haven't tried the usb thing yet, but for what it's worth I selected netbook remix in wubi and tried reinstalling again, but it still didn't work.  If I get this on the usb drive, what should I do with it?

---

### Post by Sealbhach on 2009-11-24
> **Space-Wolf said:**
> I haven't tried the usb thing yet, but for what it's worth I selected netbook remix in wubi and tried reinstalling again, but it still didn't work.  If I get this on the usb drive, what should I do with it?

Boot up from the USB (you may have to change the boot order in the bios). When you get to the desktop, open up a terminal and follow the instruction here: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

It's not really that difficult, just make sure you get the sda# number right. Hopefully this will install Grub properly.

.

---

### Post by Space-Wolf on 2009-11-24
Okay, and how do I do the sda things?  How do I find out which is the correct one?

---

### Post by Sealbhach on 2009-11-24
> **Space-Wolf said:**
> Okay, and how do I do the sda things?  How do I find out which is the correct one?

Once you're in the Live CD session, do as suggested and run

sudo fdisk -l

This will display a list of your partitions with their names and formats. Your windows partition will be formatted to NTFS so it's not that one. Your Linux partition will be formatted to ext4, so pick that one.

.

---

### Post by Space-Wolf on 2009-11-26
Okay now the thing is, I'm planning to install Ubuntu using Wubi, meaning there is no partition currently set aside for Ubuntu.  Is this going to effect what I have to do?

---

