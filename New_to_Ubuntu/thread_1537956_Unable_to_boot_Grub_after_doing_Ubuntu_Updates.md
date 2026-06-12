---
title: "Unable to boot Grub after doing Ubuntu Updates"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by NonStop on 2010-07-24
I used Wubi recently via a CD of Ubuntu and installed Ubuntu within Windows. However, after carrying out updates to Ubuntu, the multiboot loader, GRUB, fails to load, instead this message appears:

error: no such device: 9abb4147-465b-46fc-babe-2c8cd5d80600
grubrescue>_

If I hit enter grubrescue is repeated. The boot loader isn't working at all, and I can;'t boot Windows anymore. Help would be much appreciated!

---

### Post by bcbc on 2010-07-24
> **NonStop said:**
> I used Wubi recently via a CD of Ubuntu and installed Ubuntu within Windows. However, after carrying out updates to Ubuntu, the multiboot loader, GRUB, fails to load, instead this message appears:

error: no such device: 9abb4147-465b-46fc-babe-2c8cd5d80600
grubrescue>_

If I hit enter grubrescue is repeated. The boot loader isn't working at all, and I can;'t boot Windows anymore. Help would be much appreciated!

Did you run updates or upgrade to 10.04?

---

### Post by NonStop on 2010-07-24
Ran updates on the most recent version.

---

### Post by bcbc on 2010-07-24
> **NonStop said:**
> Ran updates on the most recent version.

So you can't boot windows or Ubuntu. That means you just get a grub prompt when you start the computer? 

That is unusual because it means that grub installed itself as the bootloader on your drive - which shouldn't ever happen with wubi.

Why don't you boot from the Ubuntu cd (select 'Try without installing') and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results back here. That should make it clear what is going on.

---

### Post by NonStop on 2010-07-25
I have tried that, but if I out the disc in the CD drive, and then turn on the laptop, the grub prompt still opens up. Should I enter the setup and make the computer load from disc?

---

### Post by wilee-nilee on 2010-07-25
> **NonStop said:**
> I have tried that, but if I out the disc in the CD drive, and then turn on the laptop, the grub prompt still opens up. Should I enter the setup and make the computer load from disc?

+1 on the bootscript @bcbc; OP post the script to see whats going on.

---

### Post by bcbc on 2010-07-25
> **NonStop said:**
> I have tried that, but if I out the disc in the CD drive, and then turn on the laptop, the grub prompt still opens up. Should I enter the setup and make the computer load from disc?

Most laptops have a key to get boot options. This is not F8 which is the windows boot option key. On mine its F12, but it varies by model. You can also enter BIOS and change the boot order to boot from CD, but usually this isn't necessary.

I saw a thread somewhere that grub is asking again where to install itself while running updates. If you selected to install grub anywhere (e.g. /dev/sda) this will stop your computer from booting. Please can you confirm if this happened.

If so, then you need to replace the grub bootloader with the windows bootloader (or equivalent). Either insert windows repair disk and run fixmbr (xp) or bootsect.exe /fixmbr (vista/7) or install the lilo bootloader from an Ubuntu live cd as follows:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

If you have more than a single drive, you need to install the bootloader to the one that contains windows.

---

### Post by NonStop on 2010-07-25
I changed the BIOS settings via F2 to boot from CD, can get the Ubuntu CD to load. However there are only the options to do a full install, or to run it as a live cd.

By any chance, although I understand this would get rid of Windows and all my data (which was what I was intending to do before this happened), could I just select full install, wipe out anything on the disc drive, and install Ubuntu properly on top of it.

---

### Post by Truemedia on 2010-07-25
This is nearly the exact same problem I'm having just a different error message at grub rescue when booting windows (file not found)

---

### Post by wilee-nilee on 2010-07-25
> **NonStop said:**
> I changed the BIOS settings via F2 to boot from CD, can get the Ubuntu CD to load. However there are only the options to do a full install, or to run it as a live cd.

By any chance, although I understand this would get rid of Windows and all my data (which was what I was intending to do before this happened), could I just select full install, wipe out anything on the disc drive, and install Ubuntu properly on top of it.

You can run the Ubuntu cd live and post the script, or if you have everything backed up you can just overwrite everything by installing. Personally I would want to keep the MS setup myself if I had a license, and would want to have a install disc for it in the future.

---

### Post by wilee-nilee on 2010-07-25
> **Truemedia said:**
> This is nearly the exact same problem I'm having just a different error message at grub rescue when booting windows (file not found)

Start your own thread and post the bootscript in my signature in code tags as described, we keep these sort of problems separated as they can get convoluted with different problem sets.

---

### Post by bcbc on 2010-07-25
> **NonStop said:**
> I changed the BIOS settings via F2 to boot from CD, can get the Ubuntu CD to load. However there are only the options to do a full install, or to run it as a live cd.

By any chance, although I understand this would get rid of Windows and all my data (which was what I was intending to do before this happened), could I just select full install, wipe out anything on the disc drive, and install Ubuntu properly on top of it.

+1 on what wilee-nilee said.

While you can install fresh, I think it's rarely a good idea to let a little problem like this force your hand. 

Boot in live CD mode (try without installing). You can then a) post the script, b) install lilo as described above to get windows booting, c) you can also backup your data provided you have an external drive.

Also, I've seen many users quick to drop Windows, only to discover they need it later. I'm not saying you will, just it's a lot easier leaving it than trying to get it back later.

---

### Post by NonStop on 2010-07-26
I see. Well right now I don't have access to my laptop till late August, I'll resurrect this thread/cerate a new one and PM you guys if that's ok. If someone could be kind enough to newbie step by step tell me how to get hold of this script when I come back, I'd really appreciate it.

---

### Post by NonStop on 2010-07-26
Also, all my data is already backed up on another PC, so that's not a problem, but I do not have a Windows Repair disc as far as I know, Vista just came pre-installed on my laptop.

---

### Post by bcbc on 2010-07-26
> **NonStop said:**
> I see. Well right now I don't have access to my laptop till late August, I'll resurrect this thread/cerate a new one and PM you guys if that's ok. If someone could be kind enough to newbie step by step tell me how to get hold of this script when I come back, I'd really appreciate it.
I am subscribed to this thread, so you can just add a new post whenever you like and I'll see it.


> **NonStop said:**
> Also, all my data is already backed up on another PC, so that's not a problem, but I do not have a Windows Repair disc as far as I know, Vista just came pre-installed on my laptop.

Because you installed with WUBI, you need to have a windows bootloader (or equivalent). Booting straight to a grub prompt shows that you have the grub bootloader. So doing the following commands after booting from a live CD will fix that
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

The boot info script just confirms to us that you've reported correctly and gives us more confidence than blindly telling you to run commands, but if you're sure it was WUBI then you'll be fine.

---

### Post by Josh_Leaner on 2011-05-29
I am having a slightly similar problem. I have windows 7 on my main C:/ drive partition and I have installed Ubuntu 8. something (honestly I cant remember) Ive been using the linux size for a while and I decided to ressize my partition because I was running out of room, as I only allowed ubuntu 10 Gigs or so. I recently upgraded Ubuntu to v10.10 Meerkat and Ive decided to either resize it or do away with it and install OpenSuse KDE (all using Gparted live CD)

Problem: When I power my pc on and hit the F12 key to bring the other options up (boot from CD drive or USB, etc) does not show up AT ALL. It goes straight to the normal option of booting into Windows or Ubuntu.

I have seen problems sorta similar, but it seems to all be that the live cd would 'stick' or freeze but I dont have this problem...yet lol I just cant even get the option to boot to any media. Also, if it werent already a pain in the *** I cant boot into My BIOS either just doesnt work.

Setup:
Toshiba Satelite L655
intel i3
Windows 7
BIOS: Insyde H2Bios


if anyone has any ideas or has seen this similar problems and have the cure I would RRRRREALLY appreciate it, thanks :)

---

