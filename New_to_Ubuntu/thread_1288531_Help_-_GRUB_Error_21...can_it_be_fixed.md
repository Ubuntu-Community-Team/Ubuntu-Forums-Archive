---
title: "Help - GRUB Error 21...can it be fixed?"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by jburrell on 2009-10-11
Hi all.  I have have an HP desktop with two internal drives.  One is a SATA drive I just installed with Ubuntu v10 loaded on it and the other is the drive that came with the pc and that one has Windows XP loaded on it.  I was using XP and I shut down my pc normally.  I turned it on the next day and now I get a "GRUB Error 21."

Before this error the computer would boot and ask me if I wanted to run Windows or Ubuntu.  I would then choose and the rest was normal booting process.

I don't know what to do with this GRUB Error 21 because it won't let me do anything, the cursor just sits there and blinks and all I can do is turn it off and try to boot it again.  The BIOS is fine.  I've gone in the setup within the BIOS and checked everything...

I found an old Windows 98 CD that is bootable. I managed to get past the BIOS and get to DOS.  I look in DOS for my hard discs and they are not there but yet they both show in the BIOS.

Is there anything that can be done?  What is this "GRUB" thing?  Is GRUB some sort of Linux version of DOS?

Thank you for your help & wisdom...

---

### Post by Sef on 2009-10-11
This [thread ]("http://ubuntuforums.org/archive/index.php/t-875952.html")has a solution.

---

### Post by madsmeg on 2009-10-11
[http://ubuntuforums.org/showthread.php?t=62717](http://ubuntuforums.org/showthread.php?t=62717) try here

GRUB is not like DOS, it is not a file system. GRUB allows you to choose between operating systems that you have installed on your hard drive(s).

---

### Post by madsmeg on 2009-10-11
Beat me to it Sef

---

### Post by oldfred on 2009-10-11
Your windows 98 boot disk will not see any Linux partitions. It just does not recognize ext3 types.

More info on error 21:
[http://members.iinet.net.au/~herman546/p15.html#21](http://members.iinet.net.au/~herman546/p15.html#21)

If it was working before did you unplug an external drive that the system was really booting from. Or did a drive die? If BIOS sees the drives they should be good, but may have problems.

---

### Post by jburrell on 2009-10-12
All, thanks for the recommendations. I had looked at a couple of threads before posting but was/am confused by GRUB as I have no experience with it.

OldFred - in answer to your question one of my drives (the SATA loaded with Ubuntu) was acting funny and Ubuntu wouldn't boot so in the meantime I was using Windows to do what I needed to do.  I don't know if the drive is dead, how can you tell?  

My problem is that when I get the GRUB Error 21 I can't do anything more because it just sits there and the cursor blinks at me.  Is there some way I can interrupt the process?

---

### Post by jburrell on 2009-10-12
I also forgot to mention that before I installed the SATA drive with Ubuntu 8.10 I had gone ahead and loaded the same version of Ubuntu on my HP IDE drive.  I had to quit using that one because I forgot the password and then I had the idea to get a new SATA drive and load 8.10 as a standalone on that drive.

Sorry to keep throwing these things out there instead of putting them in a short & concise post...

---

### Post by oldfred on 2009-10-12
Did you unplug the IDE drive after you installed on the SATA? It could have changed the drive numbers. Ubuntu now usually uses UUID that do not change to eliminate the drive number issue.

On the IDE drive you can go in single user mode and change the PW. I will let you search google for that if you desire.

So we can see you configuration use the liveCD and download and run this script that documents your configuration.

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

