---
title: "Replacing Fedora with Ubuntu"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by BarryRD on 2010-08-03
I currently have a Fedora Linux system installed on my PC, dual-booted  with Windows XP, separated into partitions on three disk drives,  including the boot drive. It was installed by a Linux guru in an attempt to wean me from MS Windows, but Fedora doesn't seem very user friendly. I think I would like to replace or overlay my Fedora system with  Ubuntu, but I really need to retain my existing partitions, and the data that I  have previously created on them, including the Windows partitions. I'm not concerned with the applications, just the data. And to answer your unspoken question, no, I don't know how to back up the data.

Is this feasible with an Ubuntu installation? I am unable to find  any information about doing this sort of thing on the Ubuntu Internet help pages, and I  would like to know if it is even possible before spending time and  effort in installing Ubuntu.

---

### Post by SunnyRabbiera on 2010-08-03
well if you have a seperate /home partition you can spare your personal files but over write the root directory.

---

### Post by PremiereWebDesign on 2010-08-03
I just recently done this. Only exception being that I was running Fedora 13 and have Windows 7. 
First back up all the data that you want to keep from the Fedora installation. If everything is in your home folder, a simple way to do this would be to copy your home folder to a CD or DVD. 
Next, use the Ubuntu Live CD and try it without installing. After booting, go to System >> Administration >> Disk Utility. You will most likely have to click on your hard drive from the options on the left side of the screen. Once you do  that, you will see the different partitions. Take special note of the NTFS partitions as this is your Windows OS. You will see at least 3 other partitions. They will be something like extended, Swap, and then the other will probably just give the size of the partition. When you click on these, the properties will be listed below. They will say they are linux partitions. With the exception of the extended, which will say it is a container for logical partitions. Delete all of these. Once again, do not delete the NTFS partition or you will lose Windows as well.
Once you have these deleted, do a restart. What you will probably have to do is hit the power button. Because you don't want the Live CD to eject. You need it to remain in the CD Drive. So, hit the power button and then once your system shuts down, start it back up. It will boot from the CD again and now you can install Ubuntu from the CD. Once installed, restart again so that you are booting from the hard drive (remove the Live CD first). Now, copy the backup that you made on the other CD back onto your system.
After using this method, the next time you boot Windows, it will do a chkdsk. Just let the chkdsk run and then you should be ok.
Like I said, I just done the same thing by using the method I just described and it worked perfectly.

---

### Post by snowpine on 2010-08-03
Welcome to the forums! Get help from the person who helped you install Fedora, that would be my advice. :) You certain are risking all the data on both your Fedora and Windows partitions if you press ahead without backing everything up to an external drive.

Also, Fedora and Ubuntu are very similar in almost every way. Have you at least tried a Live CD of Ubuntu to verify that it is, indeed, "user friendly" by your definition?

---

### Post by BarryRD on 2010-08-04
Thanks to all who responded to my question. I have decided to take snowpine's advice and stick to Fedora.

---

### Post by SoFl W on 2010-08-04
I tri-boot with Fedora, Ubuntu and Windows.

---

### Post by aeiah on 2010-08-04
the biggest difference between the two is that by default, fedora likes to be installed to an LVM group (hence why you have a /boot partition). it might also be encrypted as this was a common option before it was prominent in ubuntu.

if you are going to replace fedora with ubuntu you'll find things a lot less painless if you backup all your data, and remove your fedora partitions before reinstallation. no need to touch the windows partition.

---

