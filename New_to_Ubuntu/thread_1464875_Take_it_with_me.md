---
title: "Take it with me"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by wolfdog on 2010-04-28
Hi

I'm just beginning my journey into the world of Ubuntu and am very pleased by what I see.  I checked out Linux years ago but didn't have the time or motivation to learn all the code.  Now it's a very clean, attractive, logical operating system and after years of living the Microsoft way, it's a very refreshing change.  I can see me changing over for good one day but for now I have loaded Ubuntu on an external hard drive with the idea that it would be a portable operating system - (poor man's laptop). It works fine on the system I installed it on, taking me to the Grub2 bootloader and giving me a choice between Windows or Ubuntu. I tried it on a laptop tonight and didn't get the boot menu and when I selected a drive to boot from, it wouldn't boot from the external drive.  Looks like my idea of a portable Ubuntu isn't working.  I didn't think the install to the external drive loaded any files on the hard drive of my computer but it must have to get the bootloader.  
How can I use this external drive from any computer to access my new friend, Ubuntu?

Thanks for your time and help

wolfdog

---

### Post by ubunterooster on 2010-04-28
Grub is on the Vista drive. :(
You will have to [move it]("http://ubuntuforums.org/showthread.php?t=1462264&highlight=move+grub+drive")

---

### Post by Kafubie on 2010-04-28
I discovered ubuntu...  Maybe 1-2 years ago.  I never used it until 4 months ago.  I had a wireless problem, but that worked out after a week.  Then I've been using ubuntu about 4-15 hours daily.

---

### Post by limey_rick on 2010-04-28
The reason it does not work is as you suspect; there is no boot loader on the USB disk, so when its plugged into another computer and you tell it to boot from it, it has no boot loader to boot anything. 

You could go back to the first PC where you installed it and bring up Ubuntu again same as before and then re-install GRUB on the MBR of the USB disk. You'd then have GRUB as the boot loader on both disks, which should be ok. 

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

You can find out more about GRUB here and this will help you install it on the MBR of the USB disk, and then you should be able to boot from it. You'll probably end up with GRUB recognizing the windows partition so obviously when you plug the USB disk into another computer, you won't be able to boot it. 

I think this should work.

---

### Post by wolfdog on 2010-04-30
Thanks for all your help but I have a couple of questions.  I have printed the instructions to copy the Grub files to the Ubuntu drive but have to start by booting to the live CD so I downloaded and burned Ubuntu 9.10.  I changed the boot sequence in the bios to CD as first boot device but still get the same old Grub bootloader screen giving me two choices of OS.  I'm not able to boot to the Live CD desktop and so can't access the files on the Ubuntu 9.10 disk I've created.  I'm assuming this disc is bootable. 
Am I no longer able to designate boot sequence?

Confused.

---

### Post by ubunterooster on 2010-04-30
Boot sequence is difficult on my bios but usually there is a "choose boot device" that only affects the current boot.

It varies which key to press on each motherboard

---

### Post by wolfdog on 2010-05-13
I started this post a while ago and ran into problems so put it on the back burner.  It should be a simple thing, to install the grub files on the drive with Ubuntu .  I boot to the live CD, mount the external hard drive that Ubuntu is on, (disk utility tells me it's sdc1) and run grub install on the terminal.  It says no device specified and does not finish the install.  What is it asking for?  My guess would be the location of the grub files but the directions I have for grub install don't mention that.  (sudo grub-install --root-directory=/mnt/ /dev/sdc1)

Thanks again

Roger

---

