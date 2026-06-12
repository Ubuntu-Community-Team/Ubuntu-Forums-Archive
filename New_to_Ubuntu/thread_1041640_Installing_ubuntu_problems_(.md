---
title: "Installing ubuntu problems :("
date: 2009-01-16
forum: New to Ubuntu
---

### Post by azz2811 on 2009-01-16
I have been trying to install ubuntu on my Acer Aspire One but i have  problem.  When i use the install app on the desktop it goes trough ok until i have to select the drive to install i to.  I want to install it to my c drive butt i cant see any drives there.  I am a complete beginner when it come to ubuntu and Linux so i have probably done something wrong if you know what i have done wrong please let me know

Also i dont know if this helps but i am using a usb with ubuntu 8.10 on it that i downloaded from the ubuntu website i think it is the live cd version. i got it on the usb using unetboot 3.4

Thanks

---

### Post by JoshuaRL on 2009-01-16
> **azz2811 said:**
> I have been trying to install ubuntu on my Acer Aspire One but i have  problem.  When i use the install app on the desktop it goes trough ok until i have to select the drive to install i to.  I want to install it to my c drive butt i cant see any drives there.  I am a complete beginner when it come to ubuntu and Linux so i have probably done something wrong if you know what i have done wrong please let me know

Also i dont know if this helps but i am using a usb with ubuntu 8.10 on it that i downloaded from the ubuntu website i think it is the live cd version. i got it on the usb using unetboot 3.4

Thanks

Does the installer not see any drives, or do you not recognise your C:// drive there on the list?

---

### Post by logic++ on 2009-01-16
Hi,
 how many disks are plugged on your system and what are they? sata-ide etc...

---

### Post by azz2811 on 2009-01-16
There is only one drive in the machine (160gb) that internal and i dont know how to check if it is sata or what ever  sorry.

---

### Post by JoshuaRL on 2009-01-16
> **azz2811 said:**
> There is only one drive in the machine (160gb) that internal and i dont know how to check if it is sata or what ever  sorry.

Does the installer see anything at all?  If so, could you put it here for us to see?

---

### Post by talsemgeest on 2009-01-16
Ok, from  the sounds of it (correct me if I am wrong), you are trying to use the wubi installer. This installs ubuntu onto a file within windows. To check, are you trying to install it while you are inside windows? If you are, follow my following instructions. If you are not, ignore this post. ;)

Try downloading wubi from its website [here](http://wubi-installer.org/) and running it. Make sure the ubuntu disk is in the drive, and answer the questions. After you are sure you have given it the right drives, password etc, click "install".

---

### Post by handydan918 on 2009-01-16
...and are you using *shudder* WUBI?

---

### Post by azz2811 on 2009-01-16
No i am not using wubi i am booting from the usb stick into ubuntu and then i click on the install icon and go through some steps and then i get to the partition manager or something like that and there is nothing in the window no c drive or anything so i dont know whats going on

---

### Post by talsemgeest on 2009-01-17
Ok, from the live ubuntu environment, go to Applications>Accessories>Terminal and run the following command. ```
sudo fdisk -l
``` and post the output.

Note that the l in "fdisk -l" is a lower case "L", not a "1".

---

### Post by azz2811 on 2009-01-17
ok ill try that now thanks

---

### Post by azz2811 on 2009-01-17
ok so i did that and this is what it said:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11a8ba38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288318+   7  HPFS/NTFS

Disk /dev/sdb: 2002 MB, 2002255360 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00016b34

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         244     1955200    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(242, 254, 63) logical=(243, 106, 55)

---

### Post by talsemgeest on 2009-01-17
Ok, well ubuntu can definitely pick up the hard drive. Also try taking out your 2GB flash drive while you are trying to install.

Since it can definitely pick it up (the drive you want to install to is sda), go through the installer, when you get to the partition screen, select manual, then create a screenshot and post it here.

---

### Post by azz2811 on 2009-01-17
ok i dont think that i can take the usb out because ubuntu is running off it but ill try and get that screen shot

---

### Post by azz2811 on 2009-01-17
ok got that screen shot for you

ignore the transparent take screen shot window.  u will see that nothing comes up in the disk partition lis behind the transparent screen

[IMG]http://i276.photobucket.com/albums/kk13/azz2811/ubuntuscreencopy.jpg[/IMG]

---

### Post by talsemgeest on 2009-01-17
Ok, I see. I really have no idea what is stopping the installer from seeing the partitions.

The only thing I can think of is to try installing from the text based alternate installer. You can download it from [here](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate).

---

### Post by azz2811 on 2009-01-17
ok thanks alot :)

---

### Post by azz2811 on 2009-01-17
i thought i would try one more time at the way i was trying it just before the txt thing and it worked!!!.   Now i have windows xp already installed on my machine if i re size or create a new partition inside the c drive will i still be able to use windows?

---

### Post by talsemgeest on 2009-01-17
> **azz2811 said:**
> i thought i would try one more time at the way i was trying it just before the txt thing and it worked!!!.   Now i have windows xp already installed on my machine if i re size or create a new partition inside the c drive will i still be able to use windows?
Wow, that's unexpected! If you resize the windows xp partition and create the ext3 partition for "/" and a swap partition, you should have both xp and ubuntu installed properly. Just make sure you don't format your xp partition!

---

### Post by azz2811 on 2009-01-17
Yes i think i know what the problem is it always seems to work if i turn the machine off and then boot it back up into ubuntu instead of restarting from windows xp into ubuntu :)

is there a tutorial anywhere on this forum for what you have said about partitioning the drive?

thanks

---

### Post by talsemgeest on 2009-01-17
Basically just use the resize feature of the installer, and choose a percentage that you want for ubuntu.

---

### Post by azz2811 on 2009-01-17
yeah figuerd all that out thanks it should be working soon ill get back to u later

---

### Post by azz2811 on 2009-01-17
GUESS WHAT NO MORE PROBLEMS!!! i got it all working fine thanks for everyone's help.   Especially talsemgeest  kudos to u :D

---

### Post by talsemgeest on 2009-01-17
Awesome, glad I could help!

---

