---
title: "GRUB madness"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by File 5 on 2009-09-28
I am writing this in my first few hours as a linux and Ubuntu user. For my first crack at it I decided to install onto an 8GB USB drive from a CD that I burned. My intention was to keep everything about my laptop hard drive the same and use the USB drive for everything new. I knew nothing about GRUB as I was doing this installation. Going by the limited amount I've learned about GRUB and bootloading in general since then, it seems that GRUB (at least phase1) was installed on my hard drive (hd0). Here's what happens when I boot up:


[LIST]
[*]     If I don't have the USB drive in, it quickly gives me Stage 1.5 Error 21
[*]If I do have the USB drive in:
[LIST]
[*]The first time I boot it quickly gives me Stage 1.5 Error 2.
[*]The next time I boot after hitting Ctl-Alt-Del it take a minute or two and gives me Stage 1.5 Error 24.
[*]The third time I boot it goes right into the GRUB menu and I can boot Ubuntu or Windows just as I please.
[/LIST]
 
[*]If I restart instead of shutting down, it goes right into the GRUB menu and I have no problems.
[/LIST]
 
In case anyone's wondering, here's the result of when I look into grub from the terminal:
```

me@my-laptop:~$
grub> find /boot/grub/stage1
 (hd1,0)
grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
```When I go to find stage1 in the actual GRUB command line it says its in hd(0,0) and when I run setup on (hd0) I get the exact same results as above, except that it's for (hd0). As it stands now I can use my machine for Ubuntu and Windows, but I have to boot it 3 times after every shutdown and it's useless without the USB drive. Any ideas?

---

### Post by girishsasikumar on 2009-09-28
The first thing you must do is to restore windows boot 

If you are using Windows Vista, use restore/installation CD and use the option to fix boot/startup (i don't remember the exact name)

If you are using Windows XP, use the installation disk and choose repair windows installation option. Once you get the command prompt give the command
```
bootcfg /rebuild
```
```
fixmbr 
```

I cant think of any reason why it would boot only on 3rd attempt though

---

### Post by ajgreeny on 2009-09-28
Which version of Ubuntu, and therefore, which version of grub are you using?  You seem to have a most unusual situation here, as most users who do what you did find that they can boot straight into the grub menu if the USB is attached, but get nowhere if it is absent.

If you have a windows install CD, restore the MBR using the recovery system when you boot to that CD, if it is a OEM recovery disk you may also have that ability, but often they do not allow this, only a complete restore of the OS as it was at the time of purchase, so be very careful with that.  If you do not have any other option, you can use supergrub to do the same thing.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

The other thing you will need to do is put the grub bootloader on the usb disk, which you can probably do easiest by booting to ubuntu now and then running ```
sudo grub-install /dev/sdb
```This assumes that your usb disk is /dev/sdb, so check that with ```
sudo fdisk -l
``` first, and report back here with the details of the output if you're not sure what it means.

---

### Post by pedro3005 on 2009-09-28
See, your error was you tried to use make a normal install with a USB stick, and that went wrong. After fixing windows, format your USB stick and try following a guide. I don't know of any, but using google I found: [http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)
Maybe someone could recommend a better one.

---

### Post by louieb on 2009-09-28
The short answer is boot order. (hd0) refers to the 1st drive in the boot order. Change the boot order - and the drive GRUB thinks is (hd0) changes.

Grub is actually 3 programs.

[LIST]
[*]stage1 - goes in the drives MBR (or a partitions boot sector) - only job is to load stage2 - or in some cases stage 1.5
[*]stage2 - main program - displays the grub menu - by default found in /boot/grub
[*]stage1.5... - file system support for loading stage2 when not in an ext# formatted  partition.
[/LIST]
Sounds like you've managed to put stage1 code in the MBR of both the internal and external drive.  (at least stage1 is on the internal or windows would boot without the USB drive in).

once you get the **grub>**  prompt use the **geometry (hd0)** to get  an idea of which drive GRUB thinks is (hd0) 

Anyway I guess you want the PC to boot windows when the USB drive is not plugged in. Since you forgot to mention which version of windows - I'll refer you to [IDBS Remove Replace Uninstal Grub]("http://members.iinet.net.au/%7Eherman546/p18.html")  .

The [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") is another nice thing to have around. Got to go but heres how ro run from the live CD. [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") - Good luck.

---

### Post by File 5 on 2009-09-29
OK, first the things I forgot. I'm running Windows XP Professional and Jaunty (9.04). Also, I don't have the Windows install CD so that route is out.
 
@ajgreeny: Ran fdisk and sdb is in fact my USB drive (I'm very new to this but the part where it said sda was ~60GB and sdb was ~8GB gave it away). Installed GRUB on sdb and the following occurred: Instead of the triple-boot phenomenon it went down to a double-boot phenomenon; now when I boot from a complete shutdown it gives me Error 2 and then when I boot after that it works fine. Also, when booting Windows I got Error 13 but I fixed that with a quick forum search and edited /boot/grub/menu.lst to remap the hd assignment in the Windows entry. I only wish I could install it again and get rid of Error 2 like I did Error 24 (heh I tried it...didn't work).
 
@louieb: geometry shows that it thinks (hd0) is the USB drive. What I'd like to do is have GRUB manage booting on my hard drive even when the USB drive isn't in. In order for it to do this I guess I'd have to create a small partition on sda on which to put /boot/grub and then re-install GRUB to have the stage1/stage1.5 point to the stage2 on that partition. Of course I have no idea how to do that.
 
Lastly, I'm still very confused as to whether GRUB is properly installed on my USB key (sdb) and whether it would boot if my hard drive wasn't there. I tried switching the boot order for USB drive and hard drive in BIOS but regardless of the configuration everything behaves the same (Error 2 then boots successfully). Based on the evidence I've seen it seems to me that phase1/phase1.5 is installed identically on sda AND sdb and in each case points to /boot/grub on sdb. Mind you, this is a guess based more on behavior I've observed than any substantial knowledge of GRUB. At this moment I don't have access to another computer on which I can test the USB drive. Thanks all for the quick replies!

---

### Post by girishsasikumar on 2009-09-29
Take a look here to create a new boot partition and set it up
[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall]("https://help.ubuntu.com/community/CreateBootPartitionAfterInstall")

---

### Post by louieb on 2009-09-29
> **File 5 said:**
> .... is have GRUB manage booting on my hard drive even when the USB drive isn't in. .. create a small partition on sda on which to put /boot/grub ... Of course I have no idea how to do that.
Its called a dedicated grub partition.  The short of it is use Gparted to create a small partition. I make mine 16MB and thats overkill GRUB will use 2-3MB.  Create the boot and boot/grub directories. Copy the content of /boot/grub from your USB install.  Setup the MBR of the internal drive to boot it.   More here: [IDBS make a dedicated GRUB partition]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition_") 
    
> 
Lastly, I'm still very confused as to whether GRUB is properly installed on my USB key (sdb) and whether it would boot if my hard drive wasn't there. Get and run the script linked to in post #5. [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")  After downloading 

```
sudo bash ~/Desktop/boot_info_script*.sh
```It creates file RESULTS.TXT - Put it in your next post - will be able to tell from it if the USB drive is setup to boot on its own.  

The information will help in setting up the USB to boot on its own. 
And is useful to have to get a dedicated GRUB partition setup too.

---

### Post by egalvan on 2009-09-29
OK, my fellow Texan *louieb* hit the important points...

hermanzone

Boot Info Script


herman has excellent information on GRUB.
His web-site is highly recommended.
meifra and caljohnsmith did excellent work on the boot_script.

---

