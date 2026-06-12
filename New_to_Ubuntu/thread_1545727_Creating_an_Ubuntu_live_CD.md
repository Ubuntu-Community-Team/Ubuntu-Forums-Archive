---
title: "Creating an Ubuntu live CD?"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by newport_j on 2010-08-04
How does one create an Ubuntu Live CD? Do you just trasnfer the *iso file to a CD by burning it in?
 
Respectfully,
 
Newport_j

---

### Post by M1ke on 2010-08-04
> **newport_j said:**
> Do you just trasnfer the *iso file to a CD by burning it in?
 
Yes :)

---

### Post by ronnielsen1 on 2010-08-04
I'm assuming you mean from windows

[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

> Welcome to the ISO Recorder download page. ISO Recorder is a tool (power  toy)  							for Windows XP, 2003 and now Windows Vista, that allows  (depending on the  							Windows version) to burn CD and DVD images (DVD support is only  available on Windows Vista), copy disks, make images of the  							existing data CDs and DVDs and create ISO images from a content  of a disk  							folder. 						

---

### Post by corrytonapple on 2010-08-04
See this:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by TheNerdAL on 2010-08-04
Burn it at a **_low speed_** for best results. :P

---

### Post by newport_j on 2010-08-04
Okay, I have ben using the document that everyone has suggested. That document is entitled "Recovering Ubuntu After Installing Windows". Now that document on page 4 of 13 has the follwing statement:
 
To make sure this is indeed Ubuntu boot partition, run
 
ls /media/0d104aff-ec8c-44c8-b811-92b993823444/boot substituting 
 
0d104aff-ec8c-44c8-b811-92b993823444 with you voume's UUID from before. 
 
My question is how do I find my volume's UUID? Please remember that I have lost the Master Book Record (which I am trying to recover) and I can only boot into Windows Xp now.
 
Newport_j

---

### Post by ankspo71 on 2010-08-04
> **newport_j said:**
> Okay, I have ben using the document that everyone has suggested. That document is entitled "Recovering Ubuntu After Installing Windows". Now that document on page 4 of 13 has the follwing statement:
 
To make sure this is indeed Ubuntu boot partition, run
 
ls /media/0d104aff-ec8c-44c8-b811-92b993823444/boot substituting 
 
0d104aff-ec8c-44c8-b811-92b993823444 with you voume's UUID from before. 
 
My question is how do I find my volume's UUID? Please remember that I have lost the Master Book Record (which I am trying to recover) and I can only boot into Windows Xp now.
 
Newport_j
Hi,
What yo need to do is reinstall grub. Here are instructions to do that with a live cd: [https://wiki.ubuntu.com/Grub2#Restore GRUB2 - Recovering from a Windows XP / Vista / 7 Reinstallation](https://wiki.ubuntu.com/Grub2#Restore GRUB2 - Recovering from a Windows XP / Vista / 7 Reinstallation)
> Fire up a terminal from the Live CD for Ubuntu 10.04.
$ sudo fdisk -l (Note the partition number on which Linux resides)
$ sudo mount /dev/sdaX /mnt (Replace X with the partition number housing Linux)
$ sudo grub-install --root-directory=/mnt/ /dev/sda
$ sudo reboot
$ sudo update-grub

To burn an ISO in windows, you need to burn the ISO as an image to the cd, not just burn the ISO to the cd. Here is a quick howto from: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
> 95 / 98 / ME / 2000 / XP / Server 2003 / Vista: Infra Recorder

Download and install Infra Recorder, a free and open-source image-burning program.
Insert a blank CD in the drive and select Do nothing or Cancel if an autorun dialog box pops up.
Open Infra Recorder and click the 'Write Image' button in the main screen.
Alternatively you can select the 'Actions' menu, then 'Burn image'.
Select the Ubuntu CD image file you want to use, then click 'Open'.
In the dialog box, click 'OK'.
Hope this helps.

---

### Post by newport_j on 2010-08-04
What you say is very true. I can use it! However, I am using Ubuntu 8.04 so I guess that I use grub not grub2. How does that change this procedure? Do I just replace grub2 with grub wherever I see grub2? It cannot be that easy. Can it?
 
 
Newport_j

---

### Post by ankspo71 on 2010-08-04
Ahh, okay, then try this link:
[http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/](http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/)
Grub and Grub2 are different to reinstall, but this think should work fine.

---

### Post by newport_j on 2010-08-05
I tried the procedure to bring back Ubuntu 8.04 on my dual boot computer. The computer also has Windows installed. I used the link provided in the previous message and the procedure shown and now instead of booting only into windows it boots Ubuntu 8.04. That is what I want it to do.
 
My question is what happened to Windows? It does not give me a menu and a selection between windows and Ubuntu. So instead of booting directly into windows as before, it now boots directly into Ubuntu - an improvement. 
 
But what happend to the dual boot capability and in ths case Windows. I just as soon have it boot into Ubuntu since it is my preferred operating system. I thought by following the procedure that was shown in link in that I would get a menu and a choice between Windows and Ubuntu.
 
I know it says when booting up to press ESC to enter the menu and then does a quick count down. However, when I do press escape all I get on the menu are choices on Ubuntu!
 
Frankly, I am where I want to be, but just for future references where did Windows go? How do I get it back?
 
 
Respectfully,
 
 
James M. Yunker

---

### Post by oldfred on 2010-08-05
Grub legacy often did not find windows installs One of the advantages of grub2 is its much better osprober.

You can manually add a windows boot stanza to the menu.lst but to give specific instructions you can run this, so we can see where everything is:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

The entry can be as simple as this but ou have to adjust drive and partitions. If not drive0 then additional commands are usually required (Title can be any version of windows):

title        Windows 7 Ultimate, chainloader (on /dev/sda1)
rootnoverify    (hd0,0)
savedefault
chainloader +1

---

### Post by newport_j on 2010-08-06
I feel that I must ask this question again. I had a system with Windows XP and Ubuntu 8.04 that only booted to Windows XP. So I followed the directions for adding a MBR (master boot record) and now it only boots into Ubuntu 8.04! It does not give me a choice of Ubuntu or Windows. The mirror image of the problem that I had before. I can press ESC during boot up and I get a choice, but only of Ubuntu versions - no Windows XP.
 
The Windows partition is still there, I can see it on Gparted partion, but I cannot boot to it. How do I get back to that dual boot menu with Windows Xp and Ubuntu 8.04?
 
Newport_j

---

### Post by newport_j on 2010-08-06
Okay, now I see. I am sorry that I did not see it on the second page.
 
 
Newport_j

---

