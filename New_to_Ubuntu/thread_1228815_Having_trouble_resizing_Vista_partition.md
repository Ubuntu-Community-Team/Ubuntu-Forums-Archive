---
title: "Having trouble resizing Vista partition"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by duds2008 on 2009-08-01
Hello everyone! I recently got my mom interested in using Ubuntu/Linux. Today is the day I am trying to install it on her laptop alongside Vista. The problem I am having is that I have no idea how to use windows. I am trying to resize the partition using some "shrink" feature in vista (to make way for Ubuntu). It can only shrink the drive to about 2.5 GB. The ubuntu partitioner locks up when I try resize it from there. I have disabled some sort of system restore feature on windows. I have disabled hibernation (which funny enough you actually have to do as admin from their strange looking command line). I have run chkdsk. I have defragged the hard drive. Nothing seems to be helping. Any ideas would be sincerely appreciated. :)
Best wishes. Dudley.

---

### Post by Geoff918 on 2009-08-01
You have a couple of options; defragment the Windows partition a couple of times (I would recommend more than once to actually get the data better dealt with) and then go ahead and run Ubuntu Installer (it will allow you to create its own partition, anyway.

Or, what I might most recommend--get the Wubi installer (_MAYBE_ stands for Windows UBuntu Installer?) This would make the necessary changes, you'd likely be running an NTFS file system, but that doesn't tremendously matter anyway. And it makes it easy to uninstall if you should so choose. Just go to Windows Control Panel and click "Uninstall" and that's that.

You could use a windows-based partitioner, but why?

Also, programs like GParted are out there on download.com for windows (and it's actually a GNOME Partition editor) which will do the same thing.

---

### Post by irv on 2009-08-01
Why not just boot from the Ubuntu live CD and run Ubuntu off the CD. When the destop appears just go to System >gparted and run. With nothing mounted you can resize the Vista partition. 
Just like it said in the other post, run scandisk on the Vista before do this. Also mark down how much space is being used by Vista and leave a little extra for data file and room for installing other software if she plans on using it along side Ubuntu as a dual boot.

---

### Post by jpchipps on 2009-08-01
I just installed Ubuntu 9.04 alongside Windows 7. 

Booting from the Ubuntu CD I was able, right before the install, to resize the windows partition to make room for an Ubuntu partition. 

Dont mess with Windows if you dont know how. Use the Ubuntu installer.

---

### Post by mikewhatever on 2009-08-01
> **duds2008 said:**
> Hello everyone! I recently got my mom interested in using Ubuntu/Linux. Today is the day I am trying to install it on her laptop alongside Vista. The problem I am having is that I have no idea how to use windows. I am trying to resize the partition using some "shrink" feature in vista (to make way for Ubuntu). It can only shrink the drive to about 2.5 GB. The ubuntu partitioner locks up when I try resize it from there. I have disabled some sort of system restore feature on windows. I have disabled hibernation (which funny enough you actually have to do as admin from their strange looking command line). I have run chkdsk. I have defragged the hard drive. Nothing seems to be helping. Any ideas would be sincerely appreciated. :)
Best wishes. Dudley.

In addition to that, try also disabling the page file, which is Windows equivalent of swap. I have no idea how to do it though.

---

### Post by arikshtiv on 2009-08-01
Why not install ubuntu inside vista using wubi?

---

### Post by Mark Phelps on 2009-08-01
> **duds2008 said:**
> Hello everyone! I recently got my mom interested in using Ubuntu/Linux. Today is the day I am trying to install it on her laptop alongside Vista.

And, how do you think your mom is going to feel when (1) the Ubuntu install doesn't work (how do you know if it will unless you've tried the LiveCD first and confirmed that everything works?), and (2) you've followed all this BAD advice about using Linux utilities to shrink a Vista OS partition when this forum has dozens of posts about NOT doing just that -- and you then render her Vista OS unbootable as a side-effect.

So, do HER a favor and boot from the LiveCD first, to at least confirm that when your Ubuntu install is finished, she'll have a working machine. And, do NOT shrink the Vista OS to less than the 2.5GB recommended.  It needs free space and buffers to work.  If you force it smaller (using a Linux utility that doesn't care about what Vista needs), you'll just break it.

---

### Post by duds2008 on 2009-08-02
The live OS works! It was actually the first thing I tried. I never even had to disable acpi which is unusual for a laptop:)...(in my experience)
As for bad advice, I pretty much know it when I see it! I just wish I knew how to work with this MPD OS Windows!

---

### Post by duds2008 on 2009-08-02
Thanks for the advice Mikewhatever! But have you ever seen a Windows system running with the page file disabled? ... It's pretty funny to watch! A bit like a crack addict with multiple personality disorder! :) Thanks anyway to all of you for the advice, both good and bad! I think I might have sorted the problem now using Windows chkdsk, stopping system restore monitering, disabling hibernation, defragging the HD a couple of hundred times, running chkdsk a few more times (by the way chkdsk takes about 2 hours on this machine), 1 more defrag for good measure ... AND THEN ... good old Knoppix! I made a partition, Vista is working fine and am now ready to install Ubuntu 9.04 ... Will let you all know how it turns out! Thanks again! Viva Linux:)

---

### Post by presence1960 on 2009-08-02
> **Mark Phelps said:**
> And, how do you think your mom is going to feel when (1) the Ubuntu install doesn't work (how do you know if it will unless you've tried the LiveCD first and confirmed that everything works?), and (2) you've followed all this BAD advice about using Linux utilities to shrink a Vista OS partition when this forum has dozens of posts about NOT doing just that -- and you then render her Vista OS unbootable as a side-effect.

So, do HER a favor and boot from the LiveCD first, to at least confirm that when your Ubuntu install is finished, she'll have a working machine. And, do NOT shrink the Vista OS to less than the 2.5GB recommended.  It needs free space and buffers to work.  If you force it smaller (using a Linux utility that doesn't care about what Vista needs), you'll just break it.

+1

In a lot of cases vista tends to freak out and even become unusable when it's partition is shrunk with anything other than it's own partition manager.

---

### Post by duds2008 on 2009-08-02
I think it was designed to freak out!

---

### Post by presence1960 on 2009-08-02
> **duds2008 said:**
> I think it was designed to freak out!

LOL. I have an OEM version. I bought the DVD when I built my machine. Almost as quickly as I installed it did it come right off the machine. Went back to XP Professional. Then shortly thereafter discovered Linux.

---

### Post by lisati on 2009-08-02
Hmmmm Vista bashing? It seems there are a variety of experiences by users of the forums. Haven't had any MAJOR hassles with the copy preinstalled on my laptop. Yes, there have been a couple of MINOR annoyances, but generally easily fixed.....


Anyway, Welcome to the world of Ubuntu!

---

### Post by duds2008 on 2009-08-02
Both systems are working perfectly! (Well 1 of them is perfect at least!)
I am now going to update it, add the extra repositories, and get compiz running on it! Thanks for all the feedback! Ubuntu forums ROCK!

---

