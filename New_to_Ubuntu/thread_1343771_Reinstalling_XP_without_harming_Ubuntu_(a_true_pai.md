---
title: "Reinstalling XP without harming Ubuntu (a true pain?)"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by Enamin on 2009-12-02
hi
 

 I have searched for an answer to my problem and didn't find a solution.
 I just want to reinstall a windows XP SP3 next to my Ubuntu 9.10 (karmic) is it possible at all?!
 

 Here is the story:
 

 I had a Windows XP SP3 just like anyone. Then I installed Ubuntu so I was able to boot to any one of them. (though I just used my Ubuntu cause XP is a pain you know) anyway... now my XP is dead (!) so I want to uninstall it and reinstall a fresh copy (I need a XP next to my Ubuntu for gaming reasons!) but I don't want to harm my Ubuntu in this uninstalling-reinstalling process. And there are something I dont Understand (I'm new to linux):
 

 1) If I format my C drive (to get rid of my XP) does it harm my Ubuntu?
 

 2) do we have “primary OS and secondary OS” kind of thing in the world? And if we have, does my Ubuntu is secondary OS?
   
 

 anyway, if at all there is a solution to this complicated problem please teach this grateful student. Thanks a lot  
 

 Amin

---

### Post by PaulInBHC on 2009-12-02
I had a problem with XP that I could not fix. A friend recommended Ubuntu. I installed 9.04 as a dual boot with XP. Later I tried the XP CD to repair XP. I did not fix my problem. My XP consisted of a C: partition with programs and D: with program .exe's and a backup of pictures and docs. I ended up using the repair function of the XP CD to reinstall XP. It formatted the C: but nothing else. My grub was not effected and dual booting was fine.

EDIT I don't remember having a grub problem but according the the other posters you will. They have more knowledge than I do. Sorry if I am wrong.

---

### Post by mikewhatever on 2009-12-02
> **Enamin said:**
> 
 

 1) If I format my C drive (to get rid of my XP) does it harm my Ubuntu?

No, absolutely not.
 

>  2) do we have &#8220;primary OS and secondary OS&#8221; kind of thing in the world? And if we have, does my Ubuntu is secondary OS?

No. When two OSs are installed on separate partitions, they are independent of each other. Neither is primary, nor secondary.
   
 
The only way you can 'harm' Ubuntu when reinstalling XP is by formatting the wrong partition, but that's easier said then done, since XP can't read any of the Linux file systems by default. The only thing you'll have to do after the installation is reinstall GRUB from the Ubuntu installation cd. If you want to avoid that too, simply backup the MBR and restore it later.

[Backup your MBR]("http://members.iinet.net.au/~herman546/p17.html#Back_up_your_MBR")

---

### Post by corncob on 2009-12-02
I bought an eeebox running Xandros Linux.  I went to install XP on an external hard drive but it wanted to take over my whole computer and format the Xandros drive too.  I finally gave in to it as it just wouldn't install with a non-windows partition on the computer, figuring I could reinstall Xandros afterward.  Sure nuff, it wiped out Xandros and then didn't work itself.  I ended up installing Ubuntu and installing XP in VirtualBox.

---

### Post by Joe Ker1086 on 2009-12-02
yes, i agree with mike, just be careful when formatting, be 100% sure you are formatting the right partition. Just a heads up when installing windows tho, whenever windows is installed on a pc it wipes the MBR for any other non-windows partition so you will most likely need to pop your ubuntu install disc back in and fixmbr

---

### Post by halitech on 2009-12-02
first off, how did you install Ubuntu? Did you do a true dualboot install or did you use WUBI? If its a true install then just reinstall and then use a live cd to fix Grub. If its a WUBI install, then Ubuntu will be gone when you reinstall windows.

If you aren't sure, post the output of
```
sudo fdisk -l
```thats a lowercase L, not the number 1

---

### Post by frncz on 2009-12-02
An alternative to dual boot is to install windows xp as a virtual machine within Ubuntu. I am using this since yesterday, and it is wonderful. Use synaptic to install virtualbox OSE and then follow the instructions in virtual box.

---

### Post by Enamin on 2009-12-03
Thanks for your kind replies  
 

 so I have 2 options:  
 

 
[LIST=1]
[*]formatting C drive and     reinstalling XP + reinstalling GRUB
[*]Delete my windows and install XP     in virtual box (hmm... sounds intresting...)
[/LIST]
 


 here is my &#8220;fdisk -l&#8221; details:
 
Device  Boot           Start                  End               Blocks           Id            System
/dev/sda1   *                 1                    2718            21832303+     7            HPFS/NTFS
/dev/sda2                      2719              19457         134456017+   f            W95 Ext'd (LBA)
/dev/sda5                      2719               6709            32057676       7            HPFS/NTFS
/dev/sda6                      6710              17724          88477956       7            HPFS/NTFS
/dev/sda7                     17725            19378          13285723+  83         Linux
/dev/sda8                     19379            19457            634536          82          Linux swap / Solaris

    
as far as I know I had just three partitions not six!

 can you tell which is my windows partition? Is it sda1?

---

### Post by mikewhatever on 2009-12-03
```
here is my &#8220;fdisk -l&#8221; details:


[code]Device Boot Start End Blocks Id System 
/dev/sda1 * 1 2718 21832303+ 7 HPFS/NTFS
/dev/sda2 2719 19457 134456017+ f W95 Ext'd (LBA) 
/dev/sda5 2719 6709 32057676 7 HPFS/NTFS 
/dev/sda6 6710 17724 88477956 7 HPFS/NTFS 
/dev/sda7 17725 19378 13285723+ 83 Linux 
/dev/sda8 19379 19457 634536 82 Linux swap / Solaris
```

as far as I know I had just three partitions not six!

can you tell which is my windows partition? Is it sda1?[/code]

Yes, Windows is most probably on sda1, which is equivalent to C:\. It's worthwhile verifying that before reinstalling, by checking what's on the partition from the live cd. As said, it's safe to format and reinstall, and by the way, there seems to be a lot more then three partition.

---

### Post by musarraf172 on 2009-12-03
If you have good hardware(enough ram and cpu speed ), then you can use virtual box and instakll xp in virtual hard drive.

If you are running out of ram ( within 1gb ) then you should install xp separately in 1st partition.

While formating c drive, you must ensure that grub in not installed on MBR. If grub is installed on MBR , then after xp installed you have to reinstall grub to boot into ubuntu..

If grub is installed on linux partion itself then after installing xp just change the boot flag to linux partition..
and configure grub to get your xp boot menu.

---

### Post by Enamin on 2009-12-03
> **musarraf172 said:**
> If you have good hardware(enough ram and cpu speed ), then you can use virtual box and instakll xp in virtual hard drive.

If you are running out of ram ( within 1gb ) then you should install xp separately in 1st partition.

While formating c drive, you must ensure that grub in not installed on MBR. If grub is installed on MBR , then after xp installed you have to reinstall grub to boot into ubuntu..

If grub is installed on linux partion itself then after installing xp just change the boot flag to linux partition..
and configure grub to get your xp boot menu.


so this is how it goes... 

I have to search about this grub thing in forums a little more. (for example how to locate it, instal it via cd , etc...)

---

### Post by kansasnoob on 2009-12-03
Please also post the output of:

```
sudo parted /dev/sda print
```

---

### Post by Enamin on 2009-12-03
> **kansasnoob said:**
> Please also post the output of:

```
sudo parted /dev/sda print
```


here it is:
[[img]http://www.freeimagehosting.net/uploads/th.76f1e448ba.jpg[/img]](http://www.freeimagehosting.net/image.php?76f1e448ba.jpg)

---

### Post by kansasnoob on 2009-12-03
Please read this all before proceeding.

Well you should see what's on sda5 and sda6, probably data of some sort?????????????

They're 32 & 90 GB respectively so I doubt they're just wasted space :p

But your Win OS is on sda1 so I'd use Gparted to delete **only** sda1 (leave it unformatted and Win should sniff it out), then you should be able to reinstall Windows like it shows here:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Only instead of resizing your Ubuntu partition you're actually deleting the Win OS partition which is sda1. You can use gparted either from the Live CD or, in this case, install it and ntfsprogs:

```
sudo apt-get install gparted ntfsprogs
```

Note: it may require a reboot for ntfsprogs to be able to read the ntfs partitions!

Also since you have Karmic you probably have grub2 if this was a fresh install of Karmic rather than an upgrade. You can find out what version of grub you have by running:

```
grub-install -v
```

(0.97 is legacy grub & 1.97 is grub2)

If this is grub2 you need to boot the Live CD (choosing Try Ubuntu without changes to your computer) and follow these steps to restore grub after reinstalling Windows:

```
sudo mount /dev/sda7 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
grub-install /dev/sda
```

If that shows any errors:

```
grub-install --recheck /dev/sda
```

Then:

```
exit
```

And:

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

If it's legacy grub you'd do this from the Live CD:

```
sudo grub
```

```
root (hd0,6)
```

```
setup (hd0)
```

```
quit
```

But I'm very curious what's on sda5 and sda6! Only a fool does any re-installation or repartitioning without a full data backup!

Oh and just why are you having to reinstall Win?

Maybe it can be fixed??????????

---

### Post by Enamin on 2009-12-04
My version is GNU GRUB 1.97~beta4 so I guess it's grub2 and I've to follow the first instructions
 

 by the way, if I say I don't know what is on those partitions do you laugh at me?!!! (Cause it IS funny!! :))
 

 as far as I know I had 3 partition before installing Ubuntu (C,D,E) and in Ubuntu in &#8220;/media&#8221; I also have three partitions but with strange names: &#8220;826C51596C5148D5 , 1890060E9005F2D4 , D2&#8221;
 the first one have my C: data, the second one has my D: data, and D2 has my E: files and directories
 

 in &#8220;places&#8221; menu I have three choices. They calling themselves : &#8220;22 GB file systems , 33 GB file systems , D2&#8221; They have my C: D: and E: data respectively.  
 

 I've to say that I didn't do any customization on partitions when I installed Ubuntu.
 
> **kansasnoob said:**
> 
But I'm very curious what's on sda5 and sda6! Only a fool does any re-installation or repartitioning without a full data backup!

                                   

according to Sizes I think those are D: and E: (E: was around 100 GB but I think Linux Cut some space for it's system files)  
    	 	 	 	 	 	  Ah! by the way... for example if I insert my bootable Win CD and boot and whan it says I want to format c: and I reply: &#8220;so be it&#8221; it doesn't format d: or e: does it? So is there a way to loose the data in sda5 and sda6? More terrifying!... is there a way to loose the partition table which Ubuntu has defined currently?   
 
 

 > **kansasnoob said:**
> 
Oh and just why are you having to reinstall Win?

Maybe it can be fixed??????????

This is a sad story!!:( I have Virut &#8220;reader_s&#8221;. once in a while my XP crushes and won't come up any more. The only way to get rid of &#8220;reader_s&#8221; is to fully format my Hard drive that is why I changed to Ubuntu to protect my data and put an end to that nightmare. When I reinstall a fresh copy of XP I can use it for a few months (if I don't connect to Internet) it's good for me because I do all of my works and studies with Ubuntu (and it's a lot easier than that cursed XP) but I think it's too soon for s.o. like me to say good bye to my Windows forever. I have to be more experienced in using &#8220;Wine&#8221; and at least I have to buy and read some Linux and Ubuntu books as well and it takes a little time.

---

### Post by kansasnoob on 2009-12-04
It sounds like you have a handle on this. Just to be clear though, there is always some danger of losing data with any repartitioning or reinstallation!

I know that not everyone has the resources to do so but I'd personally never do such a thing without a full backup to an external usb drive.

But Windows should recognize the partition you want to reinstall to as Drive C.

---

### Post by Son of William on 2009-12-04
You stated that you keep XP around so that you can play games.  If that is so, I would recommend against using a virtual machine like VirtualBox.  I have used VirtualBox for a couple of years now and it is very useful but gaming performance is limited (I know they have recently added 3D support but it still slower than native).  

Any virtual OS is going to be slower than the same OS installed directly on the same machine.  If gaming performance is important then just re-install XP.  If it is not, then consider using an emulator like WINE.

---

### Post by Enamin on 2009-12-05
> **kansasnoob said:**
> It sounds like you have a handle on this. Just to be clear though, there is always some danger of losing data with any repartitioning or reinstallation!


  	 	 	 	 	 	  Yes, thanks a lot for this very informative discussion. Now I know what to do with my system. 



First I will remove my dead Win XP, Then I'll try the virtual box. Because I know if I install a Win XP (dual boot) I have to reinstall this fresh XP sooner or later (because of reader_s) why bother to back up several Gigs of data?! Because of the worst OS ever?!! no thanks! … It is very funny! Thinking about how Linux is compatible with anything but how tough windows is. When I installed Ubuntu next to my XP nothing bad happened neither to my data nor to XP but now... I think after seeing Ubuntu, and its great advantages, thinking about XP is funny isn't it?! I think this is a good decision for me, at this stage.  
 

 Anyway... Thank you all for teaching me how to do the task (reinstalling Win next to Ubuntu). I'm sure I'll use it some day but not soon.

---

### Post by Enamin on 2009-12-26
I'm back just to share my experience. It may help others:
 

 I had a free time in weekend so I gave it a shot and it worked completely for me thanks to detailed instructions above. In fact, I did exactly as kansasnoob kindly described above but with two exceptions:
 

 When I used “cp /etc/resolv.conf /mnt/etc/resolv.conf” it said something like there is no such file or directory but I ignored it and continued the instructions.
 

 When I successfully reinstalled the GRUB, it didn't recognized my new windows by default. So I had to Update it with “grub-update” command.  
 

 In fact, it wasn't as complicated as I thought, but it was a scary task!
 

 Here is some details:
 

 1. I deleted my ex-windows by deleting all of those famous files of Microsoft in Ubuntu. So my new win xp didn't recognized there was an old xp on my system and it didn't tried to repair it or something luckily. But I didn't format my sda1.    
 

 2. I formatted my first hard partition (windows called it c) with boot-able windows CD.  
 

 3. Because of my poor CD drive, windows didn't installed completely in my first, second and third attempts! So I lost and reinstalled GRUB three times!!  
 

 4. Because of my poor CD drive, my Ubuntu Live-CD couldn't boot my computer at all so it was quite a disaster for me! (not having a working OS on system and not being able to boot the system with Ubuntu or XP... disaster isn't it?)
 

 5. If you ask “so how did you able to reinstall GRUB four times without live-CD?!” I have to say: I was able to boot my system with Ubuntu live USB! It was way faster than booting with live-cd. so I recommend it to every one (to always have an Ubuntu live USB. CD isn't a trust-able media after all.)
 

 6. after reinstalling xp 4 times, I have to agree that reinstalling win don't harm Ubuntu (as every one told me here :-|) and the only thing needs to be cared is GRUB.

---

