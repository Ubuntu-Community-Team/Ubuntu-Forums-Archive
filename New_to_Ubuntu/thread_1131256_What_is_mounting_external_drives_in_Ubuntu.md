---
title: "What is mounting external drives in Ubuntu"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by nowhere@cox.net on 2009-04-20
Hi,

Which package is mounting external drives when I plug them in while running in ubuntu desktop? How does it all work? I've poked around a little and I see things like fuse, gnome-mount etc.

What is actually doing the mounting when I click on the drive in nautilus and why does it do it without superuser privileges while I cannot mount stuff without?

Thanks!

---

### Post by steve101101 on 2009-04-20
mounting is connecting your computer to a device such as a hard drive or a usb drive. this allows you to read / write to it. you need to mount any device in order to use it.

---

### Post by brunogirin on 2009-04-20
gvfs is responsible for mounting removable media. You have more details [in the gvfs-backends package description]("http://packages.ubuntu.com/intrepid/gvfs-backends").

Another piece of the puzzle is [HAL]("http://packages.ubuntu.com/intrepid/hal") that manages hardware and will notify other processes via dbus when some hardware gets added or removed.

So, my understanding is that when you insert a CD or a USB key, HAL will handle it and notify who wants to know via dbus. Both HAL and dbus run as root. gvfs is a process that runs under your user ID, with no special privilege and is started when you login. It gets notified via dbus that removable hardware is being added or removed, and offers access to it through a virtual file system that runs in user space.

I hope I got it more or less right and that it helps you understand how it all works.

---

### Post by nowhere@cox.net on 2009-04-21
Yes, it does help. I have two mounting problems I'm trying to solve and a better understanding will help.

1. When logging in through nx, I cannot mount any external media through nautilus or gnome. I actually have to make a folder and mount the media manually using sudo mount. This is on a desktop PC.

2. I recently formatted my old 80GB laptop hard drive in my ultrabay slot and it will only mount through gvfs in read only mode while my other 160GB hard drive mounts with full read/write for my user account. I tried ext3 and reiserfs but both are the same. I looked in my fstab and don't see anything special for the 160GB ultrabay drive.

---

### Post by Gen2ly on 2009-04-21
i think your problem is [gnome-volume-manager]("http://packages.ubuntu.com/intrepid/gnome-volume-manager") that's frontend can be found in the preferences under Removable Devices and Media.  GVM has alway been buggy for me but you could try a few options there and see if it-helps.

---

### Post by nowhere@cox.net on 2009-04-22
Thanks Dirk,

I couldn't find the preferences to which you are referring. I suspect we are on different versions. My Preferences menu has no Removable Devices option...

---

