---
title: "After Upgrade to 9.10 will not load to desktop"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by jkolak on 2009-11-04
I think this problem has been caused because I have not been using my Ubuntu installation and it was not up-to-date before I launched install from the update manager.

I had a successful install on the older version, maybe 8.4.

When I read 9.10 was ready, I booted up and ran opened the update manager. It informed me that several updates for the original system were available and also that the 9.04 upgrade was available.

I am thinking that if I had updated the 8.4 installation first I would not be in this position now.

So I accepted the offer to update to 9.04 first. I assumed this was a necessary prerequisite before updating to 9.10.

This upgrade process froze my computer at the message that it was updating Open Office.

After a few reboots and using the automated recovery option on GRUB, the 9.04 installation finally informed me that it had repaired itself.

So then the offer to upgrade to 9.10 appeared in the update manager, and I clicked on that. After it finished, it would no longer boot to a desktop. After running the automated recovery option on the GRUB loader several times, it will now load to a command prompt, and I can log in to the terminal, but I don't know what command to execute to see if I can load a desktop.

Thanks

---

### Post by RedSingularity on 2009-11-04
Type startx see if that works.

---

### Post by jrandolph on 2009-11-04
Just kinda wonder what kind of video card are you running?

I have had some real problems with the new releases because I have an old video card and im not sure the it works with the new versions

---

### Post by RedSingularity on 2009-11-04
> **jrandolph said:**
> Just kinda wonder what kind of video card are you running?

I have had some real problems with the new releases because I have an old video card and im not sure the it works with the new versions


ATI or Nvidia?

---

### Post by jrandolph on 2009-11-04
ATI

Radeon X550

---

### Post by RedSingularity on 2009-11-04
Oh.  The radeon cards are just beginning to get good support in terms of driver quality.  Thats why i switched to nvidia.  I got sick of the problems.  Though once you get it to work it is just fine.

---

### Post by jrandolph on 2009-11-04
yea well i have come to find out that for the time being there is no drivers for my card - im not all that worried - i have 8.04LTS
but upgrading to a new card would involve a new power supply - just dont have the funds that i want to be able to put into it
hopefully i have a whole new desktop in my near future

---

### Post by RedSingularity on 2009-11-04
So are you using the open source driver then.  The one that comes in the kernel?

---

### Post by vince.lupe on 2009-11-04
> **jrandolph said:**
> yea well i have come to find out that for the time being there is no drivers for my card - im not all that worried - i have 8.04LTS
but upgrading to a new card would involve a new power supply - just dont have the funds that i want to be able to put into it
hopefully i have a whole new desktop in my near future

Try doing a complete installation from a LiveCD. It worked for me, and I have a 4+ years old laptop (Gateway 400SD).

God bless,
Vince Lupe

---

### Post by jrandolph on 2009-11-04
> **RedSingularity said:**
> So are you using the open source driver then.  The one that comes in the kernel?

With 8.04 im am using the ATI accelerated graphics driver, but when I tried 9.04 I could never get it to boot to the desktop always a black screen - honestly I havent tried 9.10 just because I dont have time yet

> **vince.lupe said:**
> Try doing a complete installation from a LiveCD. It worked for me, and I have a 4+ years old laptop (Gateway 400SD).

I may give it a try with the live cd - but like i said right now I have 8.04LTS it doesnt do everything I want but it gets it done

---

### Post by jkolak on 2009-11-04
Thanks. 

After running startx I received the following messages:

EE - No devices detected
Fatal error - no screens found

xinit: No such file or directory. Unable to connect to X Server. No such process. Server Error.

Then returns to command prompt.

My video card is NVIDIA GeForce 7100. When I installed the driver with Ubuntu 8.4 it offered me the proprietary driver for maximum performance and I accepted it, and it ran fine.

I did notice a few threads below that another user has difficulty with this driver, and has the same symptom of only booting to a command prompt, and also a flashing screen, which I sometimes get.

---

### Post by jrandolph on 2009-11-04
> **jkolak said:**
> Thanks. 

After running startx I received the following messages:

EE - No devices detected
Fatal error - no screens found

xinit: No such file or directory. Unable to connect to X Server. No such process. Server Error.

Then returns to command prompt.

My video card is NVIDIA GeForce 7100. When I installed the driver with Ubuntu 8.4 it offered me the proprietary driver for maximum performance and I accepted it, and it ran fine.

I did notice a few threads below that another user has difficulty with this driver, and has the same symptom of only booting to a command prompt, and also a flashing screen, which I sometimes get.

Well I am of no help to you - I was just going to say if you were using an ATI card there in may be your problem

---

### Post by RedSingularity on 2009-11-04
From the command line do................

sudo apt-get install ubuntu-desktop

---

### Post by jkolak on 2009-11-04
> **jrandolph said:**
> Well I am of no help to you - I was just going to say if you were using an ATI card there in may be your problem

Oh, that's no problem. I appreciate the thoughtfulness.

I guess what I am really wondering is how to fix something like this without technical analysis.

In Windows if your installation goes bad, you just reinstall. 

I booted up my 8.4 to see if I could do that, but the first thing it asks me is to set my hard disk partitions.

I would like to just reinstall over my existing installation to see if I can keep my installed programs running like you do in Windows.

Can this be done?

---

### Post by jrandolph on 2009-11-04
there is threads out there on how to creat a seperate partition for ur home directory
as far as i know or have read you can do this and then reinstall leaving that partition be and then you will have your previous home directory 
but im no expert by any means - but search for it and maybe you can find something

---

### Post by jkolak on 2009-11-04
Thanks.

After running sudo apt-get install ubuntu-desktop I get messages on reading, building, and reading and then the final message says Ubuntu desktop is already the newest version.

Just for kicks I ran the recovery mode startup again and noticed some failure messages pertaining to downloads. 

They all said "Could not resolve us.archive.ubuntu.com" and said it could not fetch specific files there

/ubuntu/dists/karmic/release.gpg

and the same path again except karmic-updates and karmic-security

---

### Post by RedSingularity on 2009-11-04
Try this then..........

sudo apt-get install ubuntu-desktop --reinstall

---

### Post by jkolak on 2009-11-04
> **RedSingularity said:**
> Try this then..........

sudo apt-get install ubuntu-desktop --reinstall

That syntax didn't work. After checking the Ubuntu Pocket Guide, I found this syntax:

sudo apt-get --reinstall install ubuntu-desktop

After running it reported as successful installation, but the error message on startx were exactly the same as previously regarding no devices detected and no screens found.

Thanks

---

### Post by RedSingularity on 2009-11-04
Post the output of lspci | grep VGA

---

### Post by RedSingularity on 2009-11-04
And type this in terminal to create a xorg file.  

sudo dpkg-reconfigure xserver-xorg

---

### Post by jkolak on 2009-11-04
> **RedSingularity said:**
> Post the output of lspci | grep VGA

00:10.0 VGA compatible controller: nVidia Corporation C73 [GeForce 7100/nForce 630i (rev a2)

---

### Post by RedSingularity on 2009-11-04
I need to know your nvidia version so do this now.................

sudo cat /proc/driver/nvidia/version

---

### Post by jkolak on 2009-11-04
> **RedSingularity said:**
> I need to know your nvidia version so do this now.................

sudo cat /proc/driver/nvidia/version

NVRM version: NVIDIA UNIX x86 Kernal Module 185.18.36 Fri Aug 14 17:18:04 PDT 2009
GCC version: gcc version 4.4.1 (ubuntu 4.4.1-4unbuntu8)

I also ran the xorg command, but got no feedback after execution.

Thanks

---

### Post by rrossenn on 2009-11-04
Hi,

I just ran into the same problem under the same circumstances as far as I am aware of.

I found the fix for me here: [http://ubuntuforums.org/archive/index.php/t-435484.html](http://ubuntuforums.org/archive/index.php/t-435484.html)

Going to my xorg.conf file I saw that my driver is set to 'nvidia'. If you change it to 'nv', according to the linked thread that's a stable no-3D support driver, and then save it, you might get lucky and start xserver with the  'startx' command.

I can't say it all works fine but at least my xserver started and I got a desktop.. now the permissions of my account seem to be borked.. but maybe that is because I booted through recovery mode.

I hope this helps, just passing the word from others though :)

If I got any terminology wrong, forgive me, I'm pretty darn new to Linux.

- Reinier

EDIT: Argh! Happy too soon. After rebooting it got further than before but before loading the desktop it went back to the black background with the white blinker top-left... but.. its progress I guess.

---

### Post by rrossenn on 2009-11-04
Ah, I can't edit the post anymore...

So, a quick follow-up, maybe someone can shine some light on this.

When booting in recovery mode I get to the prompt where I can login to my regular account and run 'startx' succesfully but with nearly no rights in the 'gui' part. Is this an ubuntu recovery mode thing?

But when I boot normally it just goes back to the blinking white dash in the top-left. I'm lost as to why I can recovery boot -> 'startx' and why it doesnt start X through a normal boot.

Thanks for any input that might follow :)

(Also, don't mean to hijack the thread but it's pretty much the same issue I'm guessing)

- Reinier

---

### Post by RedSingularity on 2009-11-04
> **jkolak said:**
> NVRM version: NVIDIA UNIX x86 Kernal Module 185.18.36 Fri Aug 14 17:18:04 PDT 2009
GCC version: gcc version 4.4.1 (ubuntu 4.4.1-4unbuntu8)

I also ran the xorg command, but got no feedback after execution.

Thanks


In a terminal do 

sudo apt-get autoremove --purge nvidia-glx-185

then restart the computer.

---

### Post by transformers on 2009-11-05
i have allso problem when i upgraded to 9.10 . my graphic card is INTEL CORPORATION 82845G/GL  .   i did not had problems with my graphic card when i had 8.0, 9.1 ubuntu.
iam sick of this new 9.10 ubuntu .:mad:

---

### Post by jkolak on 2009-11-05
> **RedSingularity said:**
> In a terminal do 

sudo apt-get autoremove --purge nvidia-glx-185

then restart the computer.

Package removed successfully. Executing startx results in exactly the same error messages as previously, re:

EE - No devices detected
Fatal error - no screens found

xinit: No such file or directory. Unable to connect to X Server. No such process. Server Error.

Prior to this text, xserver also suggests I look at the log file at /var/log/Xorg.0.log

I noticed some interesting lines. First, there were two informational lines (II) stating it could not locate a core pointer and keyboard device, which is not relevant at this point.

Secondly, the probe line (--) states:

(--) PCI:*(0:0:16:0)

and then lists information probed from my device.

Then just before the (EE) No devices detected it says,

(II) Primary device is: PCI 00@00:10:0

So I wondered if this is why it says no device detected, because the PCI stats are different on these two lines.

Just a thought.

Thanks

I'll try to attach the log file here, but the forum reply function does not include .log files as a valid extension. I may have to add a .txt to it in order to get the forum to accept the upload.

---

### Post by jkolak on 2009-11-05
Not sure why attachment did not appear. I'll try again here.

---

### Post by RedSingularity on 2009-11-05
Ok now that its remove type in terminal............
cat /etc/X11/xorg
post the contents of that file.

If for some reason it wont open that file press CTL+ALT+F1.

in there do............

sudo service gdm stop

sudo Xorg -configure

And then reboot and try the first command again.

---

### Post by jkolak on 2009-11-05
> **RedSingularity said:**
> Ok now that its remove type in terminal............
cat /etc/X11/xorg
post the contents of that file.

If for some reason it wont open that file press CTL+ALT+F1.

in there do............

sudo service gdm stop

sudo Xorg -configure

And then reboot and try the first command again.

The cat command gives a message file not found.

CTL+ALT+F1 produces no result (I am already at the command prompt since there is no graphical interface).

Service stop command says stop unknown instance.

Xorg configure gives a back trace and the following messages:

(++) Using config file /home/usr/xorg.conf.new
(EE) open /dev/fb0: No such file or dir

Reboot and retrying cat command is no change with file not found.

Reran yesterday's instruction to create xorg file and no change.

So I ran the live CD to look in the filestructure. Inside /etc/X11/ I found no "xorg" file. There is an xorg.conf file, and there are three more with dates appended to the file name, 2 of them on Nov 4, and one of them appended with .dist-upgrade. with a later time on Nov 4. These are the only files with xorg as the file name.

I will post here the xorg.conf file with .txt appended again.

---

### Post by RedSingularity on 2009-11-05
Good thats the file.  Yes the xorg.conf.  

We need to add a line to that script........

sudo vi /etc/X11/xorg.conf

This is an editor you can use to edit the file in terminal mode.  Instructions on how to move the cursor and other things are [here]("http://www.cs.rit.edu/%7Ecslab/vi.html").

Edit this part to look like this

```

Section "Device"
              Identifier    "Configured Video Device"
              Driver        "nv"
EndSection

```Restart the comp

---

### Post by jkolak on 2009-11-05
> **RedSingularity said:**
> 
We need to add a line to that script........


The file was successfully modified, but startx results in exactly the same error messages as previously, re:

EE - No devices detected
Fatal error - no screens found

xinit: No such file or directory. Unable to connect to X Server. No such process. Server Error.

---

### Post by vince.lupe on 2009-11-06
jkolak,

Just do a complete re-install... it'll be so much easier. What have you got to lose? If you need to backup data, that's different. But, I am telling you, Karmic Koala is the way to go with Ubuntu!

God bless,
Vince Lupe

---

### Post by jkolak on 2009-11-12
Thanks to all who contributed to this thread. In the end I had to take Vince's advice and reformat.

---

### Post by mbailey on 2010-02-06
I had the same problem and followed the steps above, also to no avail. I later took a look at my proprietary drivers (system->administration->hardware drivers) and discovered that my nvidia drivers were gone. I reinstalled them, activated them and ran 

sudo nvidia-xconfig

This failed the first time, worked the second. Now things are fine.

Oddly, I was able to remote into a graphical session on the box during all these problems using NX

---

