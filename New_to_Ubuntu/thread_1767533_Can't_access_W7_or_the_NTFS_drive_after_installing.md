---
title: "Can't access W7 or the NTFS drive after installing 11.04"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by mystvearn on 2011-05-25
I have a good knowledge of the windows ecosystem, DOS, but a beginner at  linux. I managed to install everything of 10.10 without looking up for  help at all. Having that slider to slide the size partition was so easy.  In 11.04, making partitions was not that easier. There is the partition  maker part, but then there is the swap partition part. Made a partition  and could not continue because it says something like "boot drive not  selected". Baffled by that for few mins and then there is the swap  drive. 

Finally found help from this link: 
[http://www.ubuntugeek.com/step-by-step-guide-installing-ubuntu-11-04-natty-on-a-windows-7-dual-booting.html](http://www.ubuntugeek.com/step-by-step-guide-installing-ubuntu-11-04-natty-on-a-windows-7-dual-booting.html)

Did what it said, but the "boot drive" error kept coming up. Don't know  what I did but after 20 mins, I managed to pass that and get it  installed. Would it be possible to revert back to the 10.10 installation  for future versions. I could see people who want to try Ubuntu from  windows shying away from 11.04 compared to 10.10.

After completing installation-entering 11.04, I noticed that I could not find boot into my W7 or find its NTFS partition. Installed the StartUP manager, in the link there, but I don't see the W7 partition to choose. What I do see is just Ubuntu, Ubuntu safe mode, and two memtest. I'm not sure if I've formatted W7, as I only allocated 30 GB + 8 GB Swap area, but I can't find my the rest of my 500 GB HD. When I opened the Disk Utility I noticed that it said 462 GB Free  space (unallocated space)

Anyone can help? I'm really screwed up here. I fear that I may need to do a clean install of my W7 and mount back W7 again and do the entire installation again. Great first impression of 10.10 looks like destroyed in 11.04...

---

### Post by IWantFroyo on 2011-05-25
If the rest of your hard drive seems to be missing, Windows is still there.

Try running this in Ubuntu:
```
sudo update-grub
```

If it still doesn't boot, make a recovery disc,[ recover Windows]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/"), and use a grub disc to reinstall grub.

Can anyone recommend a good grub installation disc? I don't know any.

---

### Post by jtarin on 2011-05-25
Follow the first part of [this post]("http://ubuntuforums.org/showthread.php?t=1291280") about installing and running the Boot Info script and post the results here. This will allow us to determine how your drive(s)look at present before we proceed any further. Use the "#" (code tag) from the reply message menu to post your results in.

---

### Post by jtarin on 2011-05-25
> **IWantFroyo said:**
> 
Can anyone recommend a good grub installation disc? I don't know any.Ubuntu Live CD.

---

### Post by IWantFroyo on 2011-05-25
> **jtarin said:**
> Ubuntu Live CD.

I didn't know you could do that with the good old Ubuntu disc...

I have to admit that I've never tried to do it, though.

---

### Post by mystvearn on 2011-05-25
Thanks for the reply. I have already installed StartUP-Manager which is a sort of GRUB right? I did a GRUB search in the get software and a legacy GRUB version comes up with the StartUP-Manager which I have already installed. Safe to say that The NTFS is gone

---

### Post by jtarin on 2011-05-25
> **IWantFroyo said:**
> I didn't know you could do that with the good old Ubuntu disc...

I have to admit that I've never tried to do it, though.[HERE]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

### Post by jtarin on 2011-05-25
> **mystvearn said:**
> Thanks for the reply. I have already installed StartUP-Manager which is a sort of GRUB right?No > I did a GRUB search in the get software and a legacy GRUB version comes up with the StartUP-Manager which I have already installed. Safe to say that The NTFS is goneWhat do you base this assumption on?

---

### Post by IWantFroyo on 2011-05-25
Go to the Ubuntu Software Center and install GParted.

My guess is that your NTFS drive is now a bunch of unallocated space :(

If it is or isn't, this should show you.

PS- Thank you for the guide. That'll help a lot in the future. :)

---

### Post by mystvearn on 2011-05-25
> **jtarin said:**
> [HERE]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")


I assume the drive is just gone.

I got Gparted and saw that 430.27 GB is unallocated (partition) and (file system)

---

### Post by jtarin on 2011-05-25
> **mystvearn said:**
> I assume the drive is just gone.

I got Gparted and saw that 430.27 GB is unallocated (partition) and (file system)Attach a screenshot of Gparted.

---

### Post by mystvearn on 2011-05-26
> **jtarin said:**
> Attach a screenshot of Gparted.

Here is the screenshot you wanted

---

### Post by jtarin on 2011-05-26
It's gone. :( If you need to setup windows and dual boot with Ubuntu start another topic so you can be guided through partition setup and OS installation. You will need a Windows and Ubuntu install disk. It gets easier as time goes on. If you decide to install windows look to my signature for EasyBCD. Become familiar with it before you install Ubuntu.
Mark this thread as solved if you would.

---

### Post by mystvearn on 2011-05-26
Thanks, noticed that straight away. :(

---

### Post by joehoward on 2011-05-26
Don't give up hope yet!  I think that something similar happened to my dad's laptop.

Get yourself a boot disk of System Rescue CD at [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

one of the tools may be able to rescue deleted partitions

I know this is not much info, but hopefully it can steer you in the right direction

---

### Post by mystvearn on 2011-05-26
> **joehoward said:**
> Don't give up hope yet!  I think that something similar happened to my dad's laptop.

Get yourself a boot disk of System Rescue CD at [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

one of the tools may be able to rescue deleted partitions

I know this is not much info, but hopefully it can steer you in the right direction

Too late-already installed and in the process of copying data.

---

