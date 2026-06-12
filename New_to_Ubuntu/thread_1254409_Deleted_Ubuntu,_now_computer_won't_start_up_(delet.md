---
title: "Deleted Ubuntu, now computer won't start up (deleted GRUB)..."
date: 2009-08-31
forum: New to Ubuntu
---

### Post by Adamantus on 2009-08-31
Hi,

I was dual booting Windows Vista and Ubuntu 9.04. I started needing more space on my Vista partition for work (plus games), so I was going to resize the partitions using the disk manager utility built into Vista. It wouldn't let me expand the Vista partition, so I decided to delete the Ubuntu partition since I was using it very little due to my work (and I was just going to re-install when 9.10 came out). So I deleted it yet still couldn't expand my Vista partition, even with 165 GB free. So I shut down my computer last night and went to sleep.

Anyway, I tried starting up my computer his morning and right before it got to the OS selection screen (the GRUB screen I think it is called), it said "Loading Grub Bootloader" then "Error 17". I'm pretty sure it's because I deleted the Grub bootloader when I deleted the partition with Ubuntu on it. I now realize how stupid I was but can't do much about it. I'm using the 9.04 live CD right now and have access to all the files on my computer. How can I fix this?

---

### Post by Cheezespread on 2009-08-31
I would recommend you use SuperGrub. Burn it and load it . You will have options to overwrite the boot loader with that of vista and you can manage log into Windows. 

[Link]("http://linux.softpedia.com/progDownload/Super-Grub-Disk-Download-8071.html")

You can reinstall Ubuntu using the live cd you have after the same.

OR

If you have your Windows install CD , boot from it and go to recovery and type in fixmbr . This should write a new master boot record to the drive where your primary system is loaded; being Windows here.

Please correct me if i am wrong.

---

### Post by halitech on 2009-08-31
boot from your windows install cd, go into recovery and run fixmbr

---

### Post by Adamantus on 2009-08-31
I'll try Supergrub. I don't have my Vista install disk with me (it's back at my house) and it may be awhile before I can get it. I'd rather fix this quickly, so it's not really an option.

---

### Post by halitech on 2009-08-31
not sure if SuperGrub works with Windows but if it does, great seeing as how your windows cd isn't with you.

---

### Post by Adamantus on 2009-08-31
I'm not too sure if SuperGrub is going to work. I can't burn anything since I'm using the liveCD to run Ubuntu. Also, I have an HP from Best Buy..when I bought it, I wasn't given a Vista install disk. Instead, I was given an HP Vista recover disk, so I don't know if that will do the same thing.

Is there any other way to fix the bootloader from the liveCD. I would think it would just be a configuration file that I could edit or something.

---

### Post by Cheezespread on 2009-08-31
> **halitech said:**
> not sure if SuperGrub works with Windows but if it does, great seeing as how your windows cd isn't with you.

You can boot from the Supergrub CD . And fix the stuff ( The one i had did )
It has an option they had added to fix MBR ( which i believe does the same thing ) with a sad smiley with a text similar " Windows " which can be selected from the list .

---

### Post by halitech on 2009-08-31
> **Adamantus said:**
> I'm not too sure if SuperGrub is going to work. I can't burn anything since I'm using the liveCD to run Ubuntu. Also, I have an HP from Best Buy..when I bought it, I wasn't given a Vista install disk. Instead, I was given an HP Vista recover disk, so I don't know if that will do the same thing.

Is there any other way to fix the bootloader from the liveCD. I would think it would just be a configuration file that I could edit or something.

the recovery cd will restore the system to the way it was when it came from the store. and yes, it is a config file but its in the stuff  you deleted

> **Cheezespread said:**
> You can boot from the Supergrub CD . And fix the stuff ( The one i had did )
It has an option they had added to fix MBR ( which i believe does the same thing ) with a sad smiley with a text similar " Windows " which can be selected from the list .

I think the problem is going to be the fact that he is running from the Live cd so downloading and burning anything is going to be a problem unless its a desktop and he has 2 cd drives

---

### Post by Cheezespread on 2009-08-31
> **halitech said:**
> 
I think the problem is going to be the fact that he is running from the Live cd so downloading and burning anything is going to be a problem unless its a desktop and he has 2 cd drives

Didn't see that . Apologies . A newbie trying to help someone ;)

I just googled it and [this]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/") came up .Hope this helps. I am not sure of it though .

---

### Post by Adamantus on 2009-08-31
I had been looking at that ms-sys program, but I keep getting the response that the package can't be found, and I did enable the universal repository.

I got my friend's computer and I'm going to try to burn the super grub CD, but does anyone have an idea on ms-sys. It seems like it would be the best solution.

---

### Post by presence1960 on 2009-08-31
> **Adamantus said:**
> I'll try Supergrub. I don't have my Vista install disk with me (it's back at my house) and it may be awhile before I can get it. I'd rather fix this quickly, so it's not really an option.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

for next time- download the iso and burn the Vista recovery console. You can't install Vista but it will run the Recovery console which you don't have because you have recovery DVD/partition.

---

### Post by LewRockwell on 2009-08-31
we wanted to point something out for present and future visitors to this thread.

we use Puppy Linux LiveCD to run Gparted for partitioning and then, while we're there we just install the Pupster and Grub also.

****Important Notice****

When Puppy installs the Grub to your Master Boot Record it makes a back-up of your original MBR and puts a reference to that file, and instructions to restore it, in the /boot/grub/menu.lst file(big thanks to the Puppy Linux Folks!)

So...if you need to restore the original MBR it is quite simple to do so

Ubuntu could/should definitely take a hint with respect to this item!

we now return you to your regularily scheduled programming

.

---

### Post by b0b138 on 2009-08-31
If your friends computer is running vista, use it to create a system repair disc.

---

### Post by Adamantus on 2009-08-31
Okay, thanks to everyone for your help. I used Super Grub and it worked perfectly. I booted back into Vista and it's working fine. Thanks again.

---

### Post by Mike Beatty on 2009-08-31
Just for future reference, your HP Vista disk will restore the MBR just fine. I do it all the time. Just boot from the CD/DVD and when it asks, load restore from the hard drive, (it's faster.) As it prompts you to restore factory defaults, hit cancel. IT will eventually reboot after restoring the MBR.

---

### Post by scr9268 on 2009-09-30
Just a comment that I was able to fix my boot loader using [http://linux.softpedia.com/progDownload/Super-Grub-Disk-Download-8071.html](http://linux.softpedia.com/progDownload/Super-Grub-Disk-Download-8071.html) and did not have to go back to the windows 98 system disk.

Many thanks for the reference to the super grub iso!

bl

---

