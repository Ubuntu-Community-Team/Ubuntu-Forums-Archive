---
title: "Absolute Noob Installs Updates, Can No Longer Access Desktop"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by juliarain on 2009-12-10
So I installed Ubuntu using the [Wubi]("http://wubi-installer.org/") installer for Windows (not because I want to keep Windows, but because I don't have a CD driver on my laptop anymore and didn't want to attempt [these complicated instructions for installing Linux from a USB drive]("http://wiki.archlinux.org/index.php/Install_from_a_USB_flash_drive")). 

I should mention that the whole goal of this was to get a working wireless card again, since I accidentally deleted the Windows software that allows me to use it. I know nothing about C++. I just thought Linux would be a good option since I didn't want to repurchase the software that would allow me to access the internet again. Dell did not send me any installation disks with the laptop - and even if I had them, I couldn't use them due to my nonexistent CD drive - and the laptop is literally held together with packing tape at this point, so it's really not worth spending any money on. It would just be nice to have a working internet connection on it again. Anyway... 

I had Ubuntu installed (via Wubi) and it was working fine for several days. Then I installed a bunch of updates, and restarted my computer. Now, when I start the computer and tell it to run Ubuntu, it gives me this: 


[CENTER]GNU GRUB  version 1.97~beta4
[/CENTER]

 [ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ] 

sh:grub>_


// So I press tab, and it says: 


Possible commands are: 
 . [ baldram boot cat chainloader configfile cpuid dump echo exit export halt help initrd insmod linux list_env load_env loopback ls lsmod parser.rescue parser.sh reader.normal reader.rescue reboot rmmod root sav_env search set sleep source terminal_input.console terminal_output.console test unset
sh:grub>_


Obviously I don't understand what any of this means (with the exception of "exit"), so my question to you is, what do I do now to access my desktop? 

Thanks so much for your help, 

- Julia

---

### Post by Merk42 on 2009-12-10
The USB instructions were probably complicated because it was Arch Linux.  USB instructions for Ubuntu can be found [here](https://help.ubuntu.com/community/Installation/FromUSBStick)

As for your current issue, not too familiar with GRUB2 or WUBI, possibly there was kernel update and it needs to be added as an entry?

So try update-grub at that terminal you get.
More information on GRUB2 [here](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by juliarain on 2009-12-11
Thanks for your help! I input "update-grub" at the sh:grub>_ line, but it didn't recognize the command. I have re-posted this at the Updates forum here with GRUB2 in the subject line to see if anyone knows more about it. 

Thanks for the link on USB installation :)

---

