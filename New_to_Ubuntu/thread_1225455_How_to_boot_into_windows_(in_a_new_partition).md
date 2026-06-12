---
title: "How to boot into windows (in a new partition)?"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by Max Williams on 2009-07-28
hey all

I just made a new partition on my ubuntu 8.04 laptop and installed windows xp into it.  I had to edit my grub settings (like in this post - [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)) to be able to get back into ubuntu - but now it always boots into ubuntu and  i can't work out how to get back into windows. 

Do i need to edit my grub settings again?  If so, how?

thanks
max

---

### Post by pastalavista on 2009-07-28
When you first boot-up, hit escape to access the grub menu. Windows should be listed as an option. If it isn't listed, then you will have to manually add it to menu.lst.

---

### Post by Max Williams on 2009-07-28
> **pastalavista said:**
> When you first boot-up, hit escape to access the grub menu. Windows should be listed as an option.

Hi - i was just about to edit my post and say something like "btw,  i tried hitting ESC when it starts to boot - i get 3 options for linux, each with a safe mode (or something similar) and some linux memory management option.  But no windows option."

---

### Post by poppemall on 2009-07-28
Is this windows the only other partition you have on the hard disk?

---

### Post by pastalavista on 2009-07-28
Download, burn and boot from a [SuperGrub disk]("http://www.supergrubdisk.org/index.php?pid=5"). It makes it easy.

---

### Post by Max Williams on 2009-07-28
> **poppemall said:**
> Is this windows the only other partition you have on the hard disk?

hi poppemall.  I have three partitions - the first is ubuntu, the second is the windows one (which I can't get to) and the third is my linux-swap partition.  I accidentally wiped out the swap partition when i was installing windows, and added it back again afterwards.

I'm downloading the supergrub iso that pastalavista recommended, going to try that.

thanks
max

---

### Post by Max Williams on 2009-07-28
OK, been experimenting with supergrub for a while.  It gave me the option to boot windows, but i got this error when i tried it:

Error13: Invalid or unsupported executable format

The only thing i managed to do was prevent the laptop from booting into linux - this was by choosing the 

WIN => MBR & !WIN!

option.  This just gave me the same error.

After this, when the laptop started up, and got to the point where it would start booting an os, it just sat at a blinking cursor.  So, i put the linux install disk in, loaded linux off the cd, went into the terminal and set up grub again. So, now i'm back at the only-able-to-boot-linux stage.  Which isn't so bad, i can still work.  But i'm no closer to gettign windows working.

Does windows have to be in the first partition?

I'm wondering if i should reinstall windows.  When i did it yesterday i chose the option to reformat the partition in order to install windows.  I'm wondering if that was a mistake - originally i'd set the new partition to ntfs which i thought would be fine for windows xp to install into.  But it didn't seem happy for some reason.

Anyway if anyone has any advice i'd love to hear it.  Kind of stumped now. 

thanks
max

---

### Post by pastalavista on 2009-07-28
I believe the problem is in your Windows MBR. When dual botting, it is best if Windows is installed first because Ubuntu can work with Windows and alter its MBR to work with Grub. Ubuntu uses the Windows "boot sector" even though menu.lst is on the Ubuntu partition. Can you post the output (in Ubuntu) of the terminal command ```
sudo fdisk -l
``` to see which partition has the boot notation (*)

Snce you installed Ubuntu first, its boot sector would have been placed on the Ubuntu '/' partition. Installing Windows created a new boot sector on the Windows partition. If you restored the Windows MBR, it would create a new boot sector and completely ignore the Linux boot sector because Windows doesn't play well with others. Best bet... install Windows first and then Ubuntu. 

You should be able to create an entry for Windows in /boot/grub/menu.lst now if the Windows MBR is valid. There's lots of documentation on the web about it.

---

### Post by Max Williams on 2009-07-28
Thanks pastalavista, but i don't want to wipe out my existing ubuntu installation, it would be too much hassle to get up to work speed again.  I think you're right though that windows first then ubuntu seems to make life easier.  I guess lots of people want to move from windows to ubuntu but not vice versa.  In my case i only want windows to run some music software (ableton live) which doesn't work well in linux afaik.

As it happens, I actually solved my problem, thanks to this page:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

All that i had to do was add the following text to the end of my /boot/grub/menu.lst file (i would have never figured this out on my own)

title Windows XP
root (hd0,1)
makeactive
chainloader +1 

I added this text, then rebooted, and now have windows on my ESC menu, and it boots up fine.  Hurrah.

Thanks very much for your (and the others) advice.

max

---

### Post by starcannon on 2009-07-28
Grats on solving it:
 
If anyone else comes along and needs a guide:
 
Here is a very good guide for how to dual boot Linux and Windows, Linux installed first:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
 
GL

---

### Post by Max Williams on 2009-07-29
> **starcannon said:**
> Grats on solving it:
 
If anyone else comes along and needs a guide:
 
Here is a very good guide for how to dual boot Linux and Windows, Linux installed first:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
 
GL

That is good, that's why i linked to it in my last post :)

---

### Post by starcannon on 2009-07-29
> **Max Williams said:**
> That is good, that's why i linked to it in my last post :)

Sorry, missed the link in your last post; great minds eh?

---

