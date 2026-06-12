---
title: "Dual boot off secondary drive"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by luke0927 on 2008-12-10
Hello new to the forum and ubuntu Im more of beginner at linux but have some unix/linux experience.

I tried to install ubuntu 8.10 on my old mandrake box but i just couldn't get it to go i think the graphics were killing it i couldn't even get through the install it would just hang...So i downloaded the alternate image and i was able to install it but when it would come up it would just hang....i figured it would run it a 1GHz processor, 512 ram box...the old mandrak 8 ran great on it....

So i have decided to install it on one of my desktops currently running XP Pro that has plenty or rescouce the only thing is im only using integrated video card but i dont think that should be a problem.

I have a secondary drive that i added i created a bootable partition on the drive i want to install ubuntu to that partition...how can i get the option to boot to that partion on start up...I though that they would have to be on the same disk to work....i would like to have it where i do not have to run it inside windows and can just boot right into ubuntu...basically a dual boot system...but each has its own drive....can someone help me out on how to make it work.

Sorry for the long post.

Thanks!

Luke

---

### Post by cdtech on 2008-12-10
Just install the GRUB bootloader to the second drive and use your BIOS settings to boot from that drive (rather than the primary drive).

---

### Post by luke0927 on 2008-12-10
can i do that right from the install cd or do i need to download the bootloader separately....what i guess i need to know is should i boot to the CD and i should beable to see the partition i created on the secondary drive or should i install it right through windows.

---

### Post by gregphil on 2008-12-10
The ubuntu/kubuntu install CD can do it, after selecting the destination partition etc, and just before you click "OK" to start the installation, 

STOP ! ! !

Look to the lower right and select the "advanced" button.  In there you will find the option to specify where (and if) to install GRUB, the linux bootloader.  Tell it to put GRUB on the partition you selected to install linux on, not on the active boot partion where Windows is.  Then click "OK"

When the installation is all done you should be able to select which operating system boots by changing a BIOS boot order setting setting.

This is not all that convient however because to switch which OS is loading requires entering the BIOS setup screen.

---

### Post by luke0927 on 2008-12-10
Thanks but i don't see that on there...it only has Accessibiltiy, Install, or Cancel? any other ideas?

so by doing it on seperate drive there really is no way to have the option to select the OS on startup without putting them on the same disk...I can live for that for now...if everything goes well i will put ubuntu on one of my laptops with a normal dual boot setup...

I guess if i have to i can just remove my windows drive and boot up and install to the partion i created and then just swith it in the bios when i start to it...just would like an easier way to install than that.

---

### Post by handydan918 on 2008-12-10
Good grief! What's wrong with installing Ubu to the second HD and installing GRUB to the MBR? 

Too simple?

---

### Post by luke0927 on 2008-12-10
> **handydan918 said:**
> Good grief! What's wrong with installing Ubu to the second HD and installing GRUB to the MBR? 

Too simple?

Thats what im doing now...i have the install starting on the second drive...i will just need to figure out how to do the install of grub on the MBR...

Im probably making it more complicated than it should be but this is my first time messing with anything dual boot i have always just had stand alone.

---

### Post by Radioman991 on 2008-12-10
This worked for me.  It appears you are attempting to do something similar to what did last year

[http://ubuntuforums.org/showthread.php?t=538245](http://ubuntuforums.org/showthread.php?t=538245)

Good luck

PK

---

### Post by luke0927 on 2008-12-10
Just got the install done on the second drive....it prompts me for username then password then acts like it logs in and just sits at the tan screen...never brings anything up....WTF!!!!!

---

