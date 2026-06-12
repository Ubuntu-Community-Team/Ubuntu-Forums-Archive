---
title: "Before I enstall and then what?"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by TerryV on 2011-02-26
Hi,
I am running XP and wish to install a 2nd OS.

I have repartitioned my HD and reformated the new partition for ext3 - 

Q1: is the correct or should I be staying with NTFS?. 

Q2: With a dual boot system , how do I choose which system to boot from, are there some changes that need to be made to the BIOS? 

I have just downloaded Ubuntu 10.10-netbook-i386 which took over twelve hours.

It is sitting on my flash drive.

Q3: Do I open it under XP or am I supposed to use it as a boot disc?

Thanks

---

### Post by TeoBigusGeekus on 2011-02-26
1)Backup crucial data from xp before you do anything in case it hits the fan...

2)Enter your BIOS settings and choose usb as your first boot device.
Plug in your flash drive and boot from there.

3)Choose "Try Ubuntu without changing anything in my pc".
You've just booted into a live session. Try everything to see if it works: internet, wireless, sound, etc. - just anything you can think of.

4)If you're satisfied and still with to install ubuntu, reboot and go into xp. Defragment your drives 5 or 6 times. 

4.5)You can install ubuntu inside windows (wubi), but I recommend against it. It's slow and windows will have access to your linux filesystem (brrrrr...).

5)Boot up with the live usb again and choose install ubuntu. Everything is straightforward in the installer, apart from the partitioning part.

6)Installation: partitioning
Don't be tempted to choose "Install ubuntu alongside windows" or whatever it's called. Choose manual partitioning.
Right click your free space and create a new partition of 1gb - usage=swap (pseudomemory, something like the windows' pagefile).
Right click your free space again and create another partition of about 20gb. Format:ext4, mount point: /. This will be your root partition, where the main ubuntu installation will be placed.
Finally, right click again and create a new partition with the remaining space left on your hd. Format:ext4, mount point: /home. This will be your home folder, where your user settings will be stored. It can be useful in the future to have a separate home partition in case of a reinstallation/upgrade. 
The rest of the installation is easy (use lowercase letters for your username and a strongish password).

7)The installer will install the grub2 bootloader on your hard drive which lets you choose which os you want to boot. Don't worry too much about it.
For more info
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by 3rdalbum on 2011-02-26
On the Ubuntu website, in the Download page, there are instructions for creating a bootable USB from the disk image. Otherwise the earlier poster's advice seems right.

---

### Post by TerryV on 2011-02-26
Thanks for previous responses - how ever when i try to boot from the (actually its is a WD USB HD) i get the message - "NTLDR is missing" - I hope it does not require another 12 hour download (lol)

Cheers

---

### Post by TeoBigusGeekus on 2011-02-27
[http://support.microsoft.com/kb/318728]("http://support.microsoft.com/kb/318728")

---

