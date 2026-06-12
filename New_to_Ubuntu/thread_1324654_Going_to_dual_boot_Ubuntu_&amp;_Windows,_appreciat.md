---
title: "Going to dual boot Ubuntu &amp; Windows, appreciate advice"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by green351 on 2009-11-12
Hi.  My first post here.

I have a lenovo thinkpad with Vista and wanted to move to a dual boot with Ubuntu.  I've done a lot of research and know how to make the dual boot and how to install software and which software to use to replace the ones I can.  

1. I'm wondering what ratio should I make the partition.  I have 86.9 GB total on my laptop.  I don't know how much space Windows and Ubuntu will take up.  The Windows partition I would like to keep as small as I can.  The only software I would like to keep on that partition is AviraAnti Virus, CCleaner, Spyware Blaster, a card game package, netflix movie player, and AVStoDVD which is a video format conversion tool.  In fact the last two are the only reasons I am keeping the windows partition, since there doesn't seem to be any ubuntu versions (correct me if I'm wrong).

2. Does Ubuntu 9.4/9.10 come with DVD burning software?  If so is there any difficulty getting it to work with my DVD burner?

3. Is it possible (if I change my mind in the future or want to sell my laptop) to revert back to a full windows installation?  I.e is there any way to "un-partition" the hard drive?

Thanks for any advice.

---

### Post by jnorthr on 2009-11-12
Welcome aboard   :popcorn:

---

### Post by danastasio on 2009-11-12
1. when i dualbooted it was a 50:50 split. but if you leave ~20 GB's for windows, you should be fine.

2. YES! NOPE! it works with all disk formats right out of the box

3. and yes, you delete GRUB and then you delete the partition and expand the windows install. but give them ubuntu as a parting gift :P

---

### Post by tommynz1975 on 2009-11-12
yes you can dump an installed linux.

you may want to make a copy of your mbr before you do anything..

1st things 1st
make a backup of what you want to keep.. email, bookmarks and such like.
scan your drive for errors.
defrag your drive

If  in vista / win7   use their tool to shrink your  NTFS partition. the utility will tell you how much it wants to give up.. (my understanding is, vista onward they changed the NTFS format in some way)

reboot into  windows a few times, as it will do scans due to the sudden loss in space.

tell the installer to use the free space.

if its xp, follow same steps but shrink drive durring install.

The installer has a import your windows settings near the end of the install, it would not hurt to give it a crack

In the words of the experienced, never partition when drunk or wasted.


best of luck,  and welcome onboard.

---

### Post by RJ12 on 2009-11-12
I decided to do a Ubuntu Dual Boot running 9.04 and XP. I have not loaded XP in a long time. I recommend that you get Ubuntu 9.04 because its the current stable one you can upgrade later (I would recommend doing a clean install though) Dont forget to install your home directory seperate which Im sure some one else can tell you how to do this. Im also making Presentations to help new users but currently I only have a Adding New Users one at my website in my signature. Just go to Ubuntu Corner then ODP Presentations (After you install Ubuntu). Trust me you wont miss Windows:p;):D! But have you ran a Live CD first to test your hardware? I advise you do so, to do this when you pop in the CD choose the Try Ubuntu without making changes to my computer option (Worded something like that)

---

### Post by eagle416 on 2009-11-12
You can use VLC (which also plays dvds IIRC), Avidemux and Kdenlive for media conversion and K3B for DVD burning to name just a few. I have sacked all my Windows XP space as I have found opensource alternatives to everything.

---

### Post by oldfred on 2009-11-12
Some times pictures are good and these sites show dual boot installs with different versions. Generally version differences only show some difference in screens but the procedures are the same.

Backup important data, house clean windows, defrag, defrag again, shrink partition and leave at least 20% free space for windows or else it may work hard drive excessively. 

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

Vista does not always like to shrink:
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by green351 on 2009-11-12
Wow thanks for all the quick and great replies.  

> **tommynz1975 said:**
> 
you may want to make a copy of your mbr before you do anything..


If  in vista / win7   use their tool to shrink your  NTFS partition. the utility will tell you how much it wants to give up.. (my understanding is, vista onward they changed the NTFS format in some way)

Is this: [http://www.freesoftwaremagazine.com/columns/backing_up_your_master_boot_record](http://www.freesoftwaremagazine.com/columns/backing_up_your_master_boot_record) a good tutorial for backing up my mbr?
Whick tool do I look for in vista do shrink my NTFS partition?  Is this different than using WUBI to partition the drive?  Or will I be doing that also?

> **RJ12 said:**
> Dont forget to install your home directory seperate which Im sure some one else can tell you how to do this. But have you ran a Live CD first to test your hardware? 
I'm not sure I know what you mean by installing my home directory seperately,  is there a thread about this that you can refer me to?
Yeah I think I'll run the Live CD tonight to give it a whirl before I do anything else.

THANKS!:D

---

### Post by RJ12 on 2009-11-12
Here is a guide I found [http://ubuntuidaho.org/node/16](http://ubuntuidaho.org/node/16)

---

### Post by Clark76 on 2009-11-12
> Whick tool do I look for in vista do shrink my NTFS partition?

[LIST]
[*]Click Start
[*]Right click on "Computer"
[*]Click on Manage
[*]In the Computer Management window that appears click on  Disk Management
[*]Locate the drive you wish to shink (in most cases it will be C:, but everyone's system is different ;) )
[*]Right click on the drive to shrink and choose Shrink
[*]The computer will then calculate the max about of that drive it will allow you to shrink
[/LIST]

Just remember that before doing any of this make sure to back up anything important just on the off chance something goes wrong.

Hope this helps

---

### Post by green351 on 2009-11-12
Thanks for all the advice folks!  I'll let you know how it goes.

---

### Post by sandyd on 2009-11-12
> **green351 said:**
> Hi.  My first post here.

I have a lenovo thinkpad with Vista and wanted to move to a dual boot with Ubuntu.  I've done a lot of research and know how to make the dual boot and how to install software and which software to use to replace the ones I can.  

1. I'm wondering what ratio should I make the partition.  I have 86.9 GB total on my laptop.  I don't know how much space Windows and Ubuntu will take up.  The Windows partition I would like to keep as small as I can.  The only software I would like to keep on that partition is AviraAnti Virus, CCleaner, Spyware Blaster, a card game package, netflix movie player, and AVStoDVD which is a video format conversion tool.  In fact the last two are the only reasons I am keeping the windows partition, since there doesn't seem to be any ubuntu versions (correct me if I'm wrong).

2. Does Ubuntu 9.4/9.10 come with DVD burning software?  If so is there any difficulty getting it to work with my DVD burner?

3. Is it possible (if I change my mind in the future or want to sell my laptop) to revert back to a full windows installation?  I.e is there any way to "un-partition" the hard drive?

Thanks for any advice.
2. It comes with a CD burning software called brasero
p.s.
After installation, go to Applications -> Accessories -> Terminal
and copy & paste. (HINT: use tab key to accept the SUN EULA when it comes up)
```

sudo apt-get install ubuntu-restricted-extras lame
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update

```32 bit ubuntu
```

sudo apt-get install w32codecs libfaac0 libfaad0 lame gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly

```64-bit ubuntu
```

sudo apt-get install w64codecs libfaac0 libfaad0 lame gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly

```
     ^                                                                                  ^
All the steps above should install most commonly used codecs


VLC media player (practically plays everything) can be found in synaptic package manager. (youll have to look around the menus, i don't have gnome)

List of Media Conversion Software (can also be found in synaptic)
avidemux
kdenlive
winff
ffmpeg (commandline)

DVD burning tools
brasero
k3b
Nero Linux (commercial)

DVD creation tools
devede

DVD Ripping tools
Handbrake (currently not working with ubuntu, wait for next release) [http://handbrake.fr](http://handbrake.fr)
Acidrip
dvd::rip

Music Players
amarok
rythmbox
songbird (not in synaptic)
exaile
audacious2
banshee
realplay (real.com)

and yes, i listed this all out from my KDE menu ;)

---

### Post by green351 on 2010-01-17
Thanks for all the advice folks, after a month of the dual boot, i decided i actually had no use for the windows after all.  so i got rid of it completely and only run ubuntu 9.10 now.

thanks

---

