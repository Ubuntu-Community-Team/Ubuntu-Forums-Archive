---
title: "SD memory problem"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by e.jejcic on 2010-09-14
Good afternoon to all: I am a really beguinner to Ubuntu. I have a problem with a SD card and is the following:when I insert the card when Ubuntu is running is not mounted, but it is when boot-up. When browse t5he content I find a "lost&found" file with a lock on top that I not able to delete it.It bring me a lot of weird things: I cannot remove it safely (the card). I can only eject it, and then never mount again (if Ubuntu is running), but I can if I restarted.
This happend when somebody insert a card in the memory slot. I have another memory card that I inserted via USB and works fine. My problem is: how Ican getrid of this "lost & found file. I appreciate any help. Thanks in advance. Thanks again from Eduardo.

---

### Post by e.jejcic on 2010-09-15
Any help, please?.

---

### Post by -kg- on 2010-09-15
What it sounds like is that the SD Card has been formatted with an ext2/3/4 file system.  That's the only reason I can think of that the card has a "Lost & Found" file.

If that's the case, you might want to reformat the card to FAT16 (if under 2 Gigs) or FAT32 (if over, or if you want to use it for some special purpose).  What are you planning to use it for?

Still, I don't quite understand why the card won't auto-mount when you plug it in.  My external hard drive has several ext4 and one ext3 partitions on it, and they all auto-mount when I plug it in.  Perhaps it's something to do with the type of media.

---

### Post by coffeecat on 2010-09-15
> **e.jejcic said:**
> When browse t5he content I find a "lost&found" file with a lock on top that I not able to delete it.

A lost+found folder is normal when a filesystem is formatted ext2, ext3 or ext4 which are Linux filesystems. You have to have root powers to remove it, but do not remove it if you want to use it with a Linux filesystem. It is there for a purpose.

However, SD cards usually come formatted with FAT32 which, although it's a Microsoft filesystem, is universally usable in any operating system. So - someone must have formatted it using a Linux computer.

What do you want to use the SD card for? If you want to use it in a camera, simply format it in the camera. If you want to use it with your computer, an ext filesystem is fine, but you need to do one or two things so that you can write to it. You may find it easier to format it to FAT32 using Disk Utility in the System > Administration menu.

---

### Post by e.jejcic on 2010-09-15
Well, thaks both of you for the response.
First of all I will say that I am too a radioamateur. I should say too that I am stupid and old for Ubuntu. The answers are very explanatory. And yes the card belongs to a Cannon digital camera (32 MB capacity)that I want to use it for my recorded music.I reformated in my Linux machine and it shows as an Ext3 file type.Does it something to do with mount or not mounting?.
When I try to format (to fat) with Disk Utility it says that the volume is busy(?),so the operation requested cannot be performed.I tried demounting the card but then is not shown in Disk Utility.
I do not known if I explain myself (sorry my english)Regards and thank you bothfor the help.

---

### Post by coffeecat on 2010-09-15
If you unmounted it from the desktop, that might explain the problem  with Disk Utility. Plug the card in and let it mount. Open Disk Utility,  select the card from the left pane and click on the 'unmount' button.  Now you should be able to re-format it FAT32.

If that doesn't work, you could simply reformat it in the camera. Then when you plug it in to the computer, delete the folders the camera has made and use it however you want. The camera will have formatted it either FAT16 or FAT32.

---

### Post by e.jejcic on 2010-09-15
I am here again. Iformatted the card with my camers (canon Power Shot A470) and it gives FAT12 with Canon label.Then I put my live CD and used Gparted to re-format it with FAT16 (samebody said that cards upto 32MB  must be in FAT16).Now I have the card in FAT16(cheked with Disk Utility).Is that OK?.
Now the problem of the card not detected and not mounted still persits.I have to re-boot to mount it. Regards from Eduardo I appreciated it very much.and thanks for  your time.

---

### Post by e.jejcic on 2010-09-17
I think no solution. Thank you all.

---

### Post by e.jejcic on 2010-09-17
Bump................

---

### Post by MooPi on 2010-09-17
Sounds like you have a problem Eduardo. If you can stay with me for a short while I think I can walk you through this. Are you there ?

Lets start by unmounting the flash media first.

---

### Post by e.jejcic on 2010-09-17
OK Moopi, I stay tunned. Thank you.

---

### Post by MooPi on 2010-09-17
Do you have the flash media mounted  now ?

---

### Post by e.jejcic on 2010-09-17
Yes, I have it mounted and working OK.

---

### Post by MooPi on 2010-09-17
Start Gparted and find your drive in the right hand menu.Select your flash media then right click with your mouse the drive area and from that menu unmount if it is mounted.

---

### Post by e.jejcic on 2010-09-17
I did that nad when I want to repeated it shows that I can do it again. When I check properties shows that cannot find mount point.

---

### Post by MooPi on 2010-09-17
Now that your drive is unmounted, lets delete the partition completely. Right click with your mouse and select delete.
After it is deleted create a New partion.

---

### Post by e.jejcic on 2010-09-17
Cann"t delete it because it is still mounted.

---

### Post by MooPi on 2010-09-17
So your saying that gparted can't unmount the drive ?
 Did you have to enter your password to start Gparted ? What I'm really asking is do you have sudo privileges or admin when your start Gparted. Just as a precaution please close all file managers and any other application that may be running. Close everything except Gparted and your internet browser .

---

### Post by e.jejcic on 2010-09-17
Yes it asked for the password, etc,etc.
Everything failed at the first step. When I right click it shows me t5hat I can unmount. OK I unmount and check again shows me that I can unmount again.

---

### Post by MooPi on 2010-09-17
I'm going to ask several questions now.
Is this an SD flash card ?
If it is a SD card , is the write protect tab pushed up  or down in the locked position ?
Make certain it's not locked.
If it isn't locked close Gparted and pull the card out of your computer for a moment, then re-insert it.
 Now only open Gparted again and attempt to delete the partition the same way as before.

---

### Post by e.jejcic on 2010-09-17
It is a memory flash card(kodak).
It is not locked because i can write, and lock is unlocked(it is not write-protected).
Tried again G-parted no luck.
I want to say again that when pull out the card with "safely remove" I have to reboot the computer to be able to mount the card. If I use eject the card can be mounted with the computer running.

---

### Post by MooPi on 2010-09-17
That sounds like you have found your own solution then. Only eject this card and don't safely remove. I would like to suggest that you use the FAT 32 file system on your card if you can get it formated. Sounds as if the camera can do this for you. Good Luck.

---

### Post by e.jejcic on 2010-09-17
Well, somebody told me that cards over 32MB can be formated in FAT32, cards under 32MB shoul be formated with FAT16 (maximum both) (??). That is the way I am using it ,but I don"t like this way. Anyway thank"s a lot for your time. Regards from Eduardo.

---

### Post by MooPi on 2010-09-17
It is just the opposite. Larger flash media should be formated to FAT32. But even this has it's down sides because FAT32 can't read large files over 4 gig in size.

---

