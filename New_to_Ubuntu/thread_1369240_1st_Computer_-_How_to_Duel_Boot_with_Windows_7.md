---
title: "1st Computer - How to Duel Boot with Windows 7"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by TheTeamFromMars on 2009-12-31
I just bought my first PC (laptop) today. 
It has Windows 7 pre-installed. 
what's the best way to install Ubuntu so that I can use both Windows 7 and Ubuntu?
I want to keep Windows 7 for work but I want to learn how to use Ubuntu/Linux.
I don't have any personal files on the laptop yet, just the Windows 7 OS. 
I don't want to destroy a brand new laptop by messing this up so would appreciate some advice. 
Are there any downsides to dual booting?

---

### Post by running_rabbit07 on 2009-12-31
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Ferretti on 2009-12-31
All you have to do is download Ubuntu from: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) Then burn it to a CD or install it to a flash drive. Next, When you run the CD or USB drive from Windows you have the option to install Ubuntu while running Windows. If you select that option, at bootup, you will have the option to boot into either Ubuntu or Windows. Hope this helps!

---

### Post by Rayve on 2009-12-31
If you check out the thread "How to fstab" linked from my signature, you'll be able to learn a lot about mounting hard drives.  :)  If you still have questions, come back to us here.

---

### Post by joshedmonds on 2009-12-31
psychocats +1

Also [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by sandyd on 2009-12-31
> **TheTeamFromMars said:**
> I just bought my first PC (laptop) today. 
It has Windows 7 pre-installed. 
what's the best way to install Ubuntu so that I can use both Windows 7 and Ubuntu?
I want to keep Windows 7 for work but I want to learn how to use Ubuntu/Linux.
I don't have any personal files on the laptop yet, just the Windows 7 OS. 
I don't want to destroy a brand new laptop by messing this up so would appreciate some advice. 
Are there any downsides to dual booting?
Ok, theres the thing. From windows vista onwards, windows hates it if you mess with its partitions w/ gparted or some other tool other than its own.

So, while running windows, go into the control panel -> Administrative Tools -> Computer management -> Disk Management 

Resize the windows partition to give ubuntu some room. Ubuntu installs on a minimium of 6GB. (i think)

leave the space you just created as free space.

Then, boot up the ubuntu cd (at the bios, press...... i think its f12?) to get to the boot options.
select cdrom
then when you get to the ubuntu installer paritoning, select "use largest block of free space"

---

### Post by wilee-nilee on 2009-12-31
You have 3 main options of installing Ubuntu. First you could install inside of Windows=Wubi, this is okay for trying out the Ubuntu program, but can have inherent problems, it is Ubuntu inside of a operating system that if it fails will also make it difficult to access either OS.

Second you could dual boot it, but then Ubuntu takes over the boot-record with grub which is okay, because generally you can manipulate the master boot record with a bootable Windows disc or thumb this is the same for Ubuntu.

Third you can just do a full install to a USB thumb of bigger then 4 gigs 8 is probably the least for ease of use. If you go this route it is quite easy and doesn't change your new computer at all while you check out Linux and the Thumb will work on any USB bootable computer. This method though must be carefully done though so without knowing how; a person would want to get all the instructions ahead of time, not a difficult complex problem but a specific path.

There is also a 4th option of downloading unetbootin into windows and loading the Ubuntu ISO onto it for a bootable thumb, but it will not save anything it is just reading the ISO and saving while using but it is not persistent upon a restart. This method is a okay way to make sure your computer is basically compatible, and check out the distro.

---

### Post by TheTeamFromMars on 2010-01-21
Thanks! I finally got around to installing Ubuntu. Now I just have to learn how to use it...

---

