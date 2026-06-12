---
title: "Dual Boot Windows Restore Grub Problem"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by tabruhn on 2010-11-03
About two months ago, I installed Ubuntu (version 10.04.1) for the first time. I installed it as a dual boot configuration since I already had Windows XP on my PC. I only have one hard drive on this PC, so Ubuntu partitioned the drive for dual boot. Everything worked great with both operating systems for over a month.

My problem occured last week. I was booted up in Windows and I noticed that my PC was operating very slowly. I thought maybe I had picked up a virus so I did a system restore in Windows. I was very carefull not to pick a restore point which was logged prior to my installation of Ubuntu, as I was fearful it might erase my Ubuntu installation. After the restore, my windows booted up automatically. I was no longer given the boot screen which allowed me to choose which OS to boot into. I did some research and discovered that it is likely the restore corrupted my MBR. For the last week, I have been attempting to fix the problem using a lot of the grub reinstall tutorials that are available online. Thus far none of them have been able to fix my problem. I know my linux partion still exists because I attempted to reinstall using the LIVE CD but I got a prompt when attempting to partition my drive stating that there was already a linux partition on the drive. Now I am just trying to figure out how to access my ubuntu installation- or if it is even possible to access it again. 

As you can tell, I am an absolute beginner. But if anyone thinks they can really walk me through how to fix this, I would greatly appreciate the help. -thanks!

---

### Post by Hippytaff on 2010-11-03
Download this script and follow the instructions, then a results.txt will appear on your desk top. Post that and people will be better able to assist you...and welcome :-)

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by tabruhn on 2010-11-03
Thanks for all your help! Very happy to be a part of the community. I've copied my results below.

-------------------------------------------------------

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk /boot/grub/core.img

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       85f508db-c537-4d9f-ab90-cfd3d429ca53   ext4                                     
/dev/sda1        CE304001303FEF59                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

---

### Post by Mark Phelps on 2010-11-03
> **tabruhn said:**
> I did some research and discovered that it is likely the restore corrupted my MBR.
Then, your research was faulty ... because Windows didn't "corrupt" your MBR, it "replaced" it -- a standard function that takes place when you restore a Windows OS.


All you should have to do is boot from an Ubuntu LiveCD and reinstall GRUB. A link with the instructions is below:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

(See section 12)

That will get you back into Ubuntu.

To get Windows boot back, open a terminal inside Ubuntu and run "sudo update-grub".  That will regenerate the GRUB menu and should add an entry for Windows.

Yes ... it really is that simple.

---

### Post by waynefoutz on 2010-11-03
If that's a Wubi install, there is no Grub, it's using the Windows bootloader.

---

### Post by wilee-nilee on 2010-11-03
sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr
/ubuntu/winboot/wubildr.mbr /wubildr
/ubuntu/winboot/wubildr /ubuntu/disks/root.disk
/ubuntu/disks/swap.disk **/boot/grub/core.img**

You have installed grub here in you weeks work. Don't do any grub installs on your computer is not using grub in the usual way, it is a wubi setup a little different.

Personally I would stop messing with it there are a couple of regulars that are familiar with wubi, all the wubi files show correctly in sda1. Wait for their help.

I think the restore did rewrite mbr at one point even though it is again a ms bootloader. I think this is probably fixable but you have to chill for some help. It may be a simple as writing the correct stanzas to boot.ini to boot Ubuntu.

---

### Post by tabruhn on 2010-11-03
> **Mark Phelps said:**
> Then, your research was faulty ... because Windows didn't "corrupt" your MBR, it "replaced" it -- a standard function that takes place when you restore a Windows OS.


All you should have to do is boot from an Ubuntu LiveCD and reinstall GRUB. A link with the instructions is below:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

(See section 12)

That will get you back into Ubuntu.

To get Windows boot back, open a terminal inside Ubuntu and run "sudo update-grub".  That will regenerate the GRUB menu and should add an entry for Windows.

Yes ... it really is that simple.

Thanks Mark. I did all the steps using the 'Simplest Method.' After step 6, the reboot step, I rebooted my computer and the first screen that popped up is a GNU GRUB command screen. It says "Minimal BASH-Like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible device or file completions." Then it gives me the grub> pointer. I tried doing sudo update-grub command but it says "error: unknown command 'sudo'" Any advice on how to move forward from here? 

Once again, thanks everyone.

---

### Post by tabruhn on 2010-11-03
> **wilee-nilee said:**
> sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr
/ubuntu/winboot/wubildr.mbr /wubildr
/ubuntu/winboot/wubildr /ubuntu/disks/root.disk
/ubuntu/disks/swap.disk **/boot/grub/core.img**

You have installed grub here in you weeks work.

Personally I would stop messing with it there are a couple of regulars that are familiar with wubi, all the wubi files show correctly in sda1. Wait for their help.

I think the restore did rewrite mbr at one point even though it is again a ms bootloader. Your definitively going to have to get rid of the highlighted grub file from sda1, before it will work. I think this is probably fixable but you have to chill for some help.

Probably good advice. I think I probably messed things up by trying to reinstall GRUB. Woops- lets hope it can still be fixed.

---

### Post by amjjawad on 2010-11-03
I don't want to get in the way as much experienced users than myself are capable of guiding you to fix this but just a simple thing :)
I suggest to re-do the steps again, just in case you missed something. It happens as you know :)

---

### Post by wilee-nilee on 2010-11-03
Actually mark Phelps may know a answer. We all miss stuff once in awhile, I do it on a minute by minute basis.;)

It is difficult at times to get all the facts together and understand every bodies post.

Here is what the sda1 line looks like with a normal wubi install you can see that you have everything there.

  Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

The restore has thrown a communication glitch in there or removed the boot.ini stanzas, probably, or put the root.disc somewhere.

---

### Post by wilee-nilee on 2010-11-03
> **amjjawad said:**
> i don't want to get in the way as much experienced users than myself are capable of guiding you to fix this but just a simple thing :)
i suggest to re-do the steps again, just in case you missed something. It happens as you know :)

lol.;)

---

### Post by amjjawad on 2010-11-03
> **wilee-nilee said:**
> lol.;)

Especially when you have Windows, you need to re-do and re-do and ...ZzZz :D

---

### Post by tabruhn on 2010-11-03
I threw the LIVE CD in and was able to boot live again. I tried to continue on where I left off by typing the command: 'sudo update-grub.' The response message was "/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mount?)."

---

### Post by wilee-nilee on 2010-11-03
> **tabruhn said:**
> I threw the LIVE CD in and was able to boot live again. I tried to continue on where I left off by typing the command: 'sudo update-grub.' The response message was "/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mount?)."

Bro your using wubi you should never go near any grub install or update command.

The only thing that does happen is that a grub update can come through always choose to not install it. Your not using grub, I know you see a grub menu when you boot wubi but it is a illusion basically.

---

### Post by amjjawad on 2010-11-03
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by tabruhn on 2010-11-03
Yeah, I won't touch anything for now. My ignorance got the best of me. After all, I don't even know what Wubi is.

---

### Post by amjjawad on 2010-11-03
> **tabruhn said:**
> Yeah, I won't touch anything for now. My ignorance got the best of me. After all, I don't even know what Wubi is.

Check my previous post!

---

### Post by tabruhn on 2010-11-03
Haha gotcha, thanks. I think this might be what I was looking for.

---

### Post by amjjawad on 2010-11-03
> **tabruhn said:**
> Haha gotcha, thanks. I think this might be what I was looking for.

Google is your amigo :P

---

### Post by tabruhn on 2010-11-03
Well it kinda seems like I can probably fix Wubi if I can get into Windows again. But every time I restart my computer now I get the GNU GRUB command screen. [Minimal BASH- like line editing is supported. For the first word,.....]

Any advice on how to proceed from this point? Like I said, the only other thing I have been able to do is boot to the live Ubuntu CD.

---

### Post by amjjawad on 2010-11-03
> **tabruhn said:**
> Well it kinda seems like I can probably fix Wubi if I can get into Windows again. But every time I restart my computer now I get the GNU GRUB command screen. [Minimal BASH- like line editing is supported. For the first word,.....]

Any advice on how to proceed from this point? Like I said, the only other thing I have been able to do is boot to the live Ubuntu CD.

Still have your Windows CD?

---

### Post by tabruhn on 2010-11-03
I don't think so- Not for this computer I fear. Are you gonna recommend I Recover or Reinstall?

---

### Post by amjjawad on 2010-11-03
> **tabruhn said:**
> I don't think so- Not for this computer I fear. Are you gonna recommend I Recover or Reinstall?

I was about to recommend this: [http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

If you don't have it, then you should :)

Edit: What do you mean for this computer? if you have XP, then any CD that has XP will do the needful.

---

### Post by tabruhn on 2010-11-03
I have the product key for my XP license. However, I don't think it came with a disk .:(

---

### Post by tabruhn on 2010-11-03
I will try with my other XP cd then.

---

### Post by amjjawad on 2010-11-03
> **tabruhn said:**
> I have the product key for my XP license. However, I don't think it came with a disk .:(

My friend, you don't need that to fix your issue. You need a disk/CD.
See if you could get from a friend of yours.

---

### Post by wilee-nilee on 2010-11-03
Geez, here is a XP ISO download burn it go to the repair command and run fixmbr, and wait for qualified help. I can appreciate the other posters attempts here but they are way out of their league here, geez I realize that about myself here and I'm quite experienced in this area. Use the brain you were born with.

[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

---

### Post by tabruhn on 2010-11-03
> **wilee-nilee said:**
> Geez, here is a XP ISO download burn it go to the repair command and run fixmbr, and wait for qualified help. I can appreciate the other posters attempts here but they are way out of their league here, geez I realize that about myself here and I'm quite experienced in this area. Use the brain you were born with.

[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)


Thanks guys. Per your advisement, I have ran fixmbr. I can now get into Windows fine again. :) I will wait for next steps.

---

### Post by wilee-nilee on 2010-11-03
Sorry to be cantakerous, but it was seeing things happen I know wont work got the better of me, sorry to the other poster as well we are all trying to help.;)

---

### Post by bcbc on 2010-11-04
Your boot.ini is missing the following line:
```
C:\wubildr.mbr = "Ubuntu"
```

The whole file will look like this:

> [boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
C:\wubildr.mbr = "Ubuntu"


---

### Post by waynefoutz on 2010-11-04
Why don't you install Ubuntu the right way? Wubi isn't a real install in the first place. It's not meant to be permanent.

---

### Post by waynefoutz on 2010-11-04
> **wilee-nilee said:**
> Bro your using wubi you should never go near any grub install or update command.

The only thing that does happen is that a grub update can come through always choose to not install it. Your not using grub, I know you see a grub menu when you boot wubi but it is a illusion basically.

that's exactly what I said 4 hours ago.

---

### Post by wilee-nilee on 2010-11-04
> **waynefoutz said:**
> that's exactly what I said 4 hours ago.

Well fortunately the one person who really knows wubi and a whole lot more has posted.;)

---

### Post by waynefoutz on 2010-11-04
> **wilee-nilee said:**
> Well fortunately the one person who really knows wubi and a whole lot more has posted.;)

personally, I think Wubi creates more problems with the newbies than it solves. I mean, it's a great way to try Ubuntu out, get your feet wet without committing yourself by partitioning your drive, but no one explains that it's not meant to be permanent. Too many people slap the disk in and think they have a real installation. No, you have a big loop mounted file in your Windows file system.

---

### Post by bcbc on 2010-11-04
> **waynefoutz said:**
> personally, I think Wubi creates more problems with the newbies than it solves. I mean, it's a great way to try Ubuntu out, get your feet wet without committing yourself by partitioning your drive, but no one explains that it's not meant to be permanent. Too many people slap the disk in and think they have a real installation. No, you have a big loop mounted file in your Windows file system.

Give it a rest:roll:. This is a request for help, not for your personal opinion. If the OP wants a direct partition install we'll all show him/her how. If you want Canonical to stop shipping wubi, then tell them. Complaining here does nothing.

---

### Post by tabruhn on 2010-11-05
Thanks, bcbc! I was able to edit the boot.ini and corrected it. Upon restart, I was given the option to boot into either OS again. However, when I choose the option to boot into Ubuntu I get an error "Windows could not start because the following file is missing or corrupt: <windows root>\system 32\hal.dll. Please reinstall a copy of the above file. I think I will try to boot into recovery and try bootcfg/rebuild. Do you think this might solve my problem? I am thinking it could end up causing a bigger issue so I thought I better ask first. Again-thanks (and Yes everyone, I will uninstall wubi and install Ubuntu correctly as soon as/if I can get my files off the wubi install.)Sorry for being such a pain-in-the-neck newb, haha.

---

### Post by oldfred on 2010-11-05
Hal is not the issue, just the symptom.

Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt]("http://members.iinet.net.au/%7Eherman546/p15.html#hal.dll_is_missing_or_corrupt")
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)

Did you use Ubuntu to edit boot.ini? That can cause issues also. Linux uses different line endings and many editors do not recognize the difference.
If editing windows files like boot.ini
(Using nano instead of gedit, it's better for dos-style linebreaks)

---

### Post by tabruhn on 2010-11-05
> **oldfred said:**
> Hal is not the issue, just the symptom.

Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt]("http://members.iinet.net.au/%7Eherman546/p15.html#hal.dll_is_missing_or_corrupt")
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)

Did you use Ubuntu to edit boot.ini? That can cause issues also. Linux uses different line endings and many editors do not recognize the difference.
If editing windows files like boot.ini
(Using nano instead of gedit, it's better for dos-style linebreaks)

Thanks oldfred. I did use Ubuntu live cd to go in and edit boot.ini. I tried using Windows but I was completely unable to edit it in Windows. Also, I did indeed use gedit as my editor. Do you think I should go back in and redo what I did- this time in nano?

---

### Post by bcbc on 2010-11-05
For future reference, before editing boot.ini, uncheck the read only option in windows (right-click, properties etc.) Then use notepad. 

Or as per microsoft:
> 
**Edit the Boot.ini File**

  To view and edit the Boot.ini file:  
[LIST=1]
[*]Right-click **My Computer**, and then click **Properties**.   -or- 
     Click **Start**, click **Run**, type sysdm.cpl, and then click **OK**.
[*]On the **Advanced** tab, click **Settings** under **Startup and Recovery**.
[*]Under **System Startup**, click **Edit**.
[/LIST]
It's a good idea to back it up before changing as well.

PS if you just want to recover data from a wubi install, use ext2read (it gives you read-only access from windows - just point it at c:\ubuntu\disks\root.disk).

PPS if you want to move to a direct install, you can use this guide to migrate the wubi install including settings and data. Of course you'll have to get it booting first: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by tabruhn on 2010-11-05
Wow this is pretty much everything I wanted to know. I can't thank everyone enough. I am gonna do the above mentioned steps and hopefully in a few minutes I will be able to mark this thread solved. -Thanks!

---

### Post by wilee-nilee on 2010-11-05
> **tabruhn said:**
> Wow this is pretty much everything I wanted to know. I can't thank everyone enough. I am gonna do the above mentioned steps and hopefully in a few minutes I will be able to mark this thread solved. -Thanks!

Hey, thanks for being patient to wait the proper help.;)

---

### Post by tabruhn on 2010-11-05
Ext2read worked perfectly for recovering all my files. :) Now I am just hoping to uninstall the Wubi Ubuntu because it is still having problems. Can I just use add/remove to uninstall it in Windows?

---

### Post by Hippytaff on 2010-11-05
Yes..you can just use the uninstall feature in windows

---

### Post by tabruhn on 2010-11-05
:) Done

---

