---
title: "Dual booted Ubuntu file transfer?"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by cheapodonuts on 2011-04-25
As Prince Hamlet, air the the throne of Denmark once said.
To sleep, perchance to transfer my files from one Ubuntu partition to the other, aye there's the rub!

No, I'm not really lazy, but I am, as my sig mentions, a permanent noob. So I've messed up something on my Hardy 32bit install and couldn't get online. Consequently I have installed Karmic 64bit on a separate partition from my purchased cd, and would like to transfer files to it.
 I know I could burn them to a cd or use a usb stick, but that means moving my hand further than the keyboard. ;)
 But seriously, I have several old comps here on which I will attempt various installs at some time, so I'm thinking that learning file transfer methods is a good thing. Whether I remember it after learning it is another matter entirely.

Molto thanko in advanceo folks.
(I'm good with foreign accents)

---

### Post by hakermania on 2011-04-25
Well, don't you find the other partition under the places menu in order to mount it and to transfer via this your files?

---

### Post by cheapodonuts on 2011-04-25
No my Massstr. I crave your indulgence. All I see is my 300gig HD and a 165gig partition. And when I open the HD it only shows the 165gig partition that contains Karmic 64. But if I reboot I get all the other install options including the Hardy install on the other partition.

---

### Post by grahammechanical on 2011-04-25
ooh arrh, you do have a problem. 

I have four partitions and when I run the file manager by clicking on places I see four hard disk icons in the side panel. I can click on any of these partitions to mount them and then I can browse the drive. I can copy and paste from one partition to another. At the moment I am using 11.04 beta and I am using LibreOffice to work on documents on my standard /home partition. I can open the documents and save the documents back on that partition or to a new location if I wish. In the past I have used copy and paste from one partition to another to save my data when I have messed up my installation.

You should be able to do the same, innit. I do not think that this is a Ubuntu studio issue either because I am trying out that version also.

Have you tried Disk Utiltiy to examine the hard disc. It might let you mount a partition.

Regards.

---

### Post by cheapodonuts on 2011-04-25
Arr, Oi can see all the partitions be in Disc Utility but the Hardy partition baint got no location address.
 (thinks) I'l prolly reboot to Hardy and use the usb stick just to get 'er done.

---

### Post by aphatak on 2011-04-27
Do you see the 'missing' partition in the df command?  If you haven't already tried it, you might want to -
[LIST=1]
[*]Start a terminal (Applications->Accesories->Terminal).
[*]Type the command 'sudo fdisk -l'.  When you see the response '[sudo] Password for <your user name>: ', key your password in.  The output will show a list of hard disks and their partitions.  You should see something like '/dev/sda1' and '/dev/sda2'.
[*]At the next command prompt, type the command 'df'.  The first column of the resulting output will show the device, and the last column will show where it is mounted.  My guess is, the 'missing' partition should be visible in the fdisk output, and not visible in the df output.  If it is, you almost home!
[*]Create a directory in your home directory with the command 'mkdir ~/missing'.
[*]Mount the missing partition in directory that you created with the command 'sudo mount <device name> ~/missing'.  If you get no error messages, you are finished.
[*]Start your file manager.  In your home directory, you should see the new directory you created, 'missing'.
[*]Open the missing directory.  The contents of your missing partition should now be visible, to copy to wherever you want.
[/LIST]
If it does not work, please post the output of the fdisk and df commands here, so then we can figure out what went wrong.  If it works, post the results anyway; we can then discuss how to make the contents permanently visible.

PS: I don't mean to talk down to you by giving such detailed instructions; it's just that if you do need them, this will save a lot of back-and-forth conversations.

---

