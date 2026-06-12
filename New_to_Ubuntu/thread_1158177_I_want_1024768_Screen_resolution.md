---
title: "I want 1024*768 Screen resolution"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by klabezo on 2009-05-13
**I have 800*600 ****[B]Screen resolution but I want 1024*768/60@**
I search the forums but I found nothing .

[SIZE=3]that is my vga card [/SIZE]

 klabezo@ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
klabezo@ubuntu:~$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 960 x 600
default connected 800x600+0+0 0mm x 0mm
   960x600        60.0  
   960x540        60.0  
   800x600        60.0*    56.0  
   768x576        60.0  
   720x576        60.0  
   856x480        60.0  
   800x480        60.0  
   720x480        61.0  
   640x480        60.0  
   400x300        60.0  
   320x240        61.0 


plz help me


[/B]

---

### Post by MarkX on 2009-05-13
I want that res too. If I enable the nvidia driver it goes down even further to 640x480! I nearly always have resolution problems with Ubuntu but in 9.04 it's even worse!

I wish there were a simple GUI where one can set the undetected resolutions manually.

I can't even find a readable guide on how to fix this in 9.04!

HEEEELP!!!

---

### Post by CatKiller on 2009-05-13
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

---

### Post by MarkX on 2009-05-13
> **CatKiller said:**
> Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

YeSSS! That worked. (well the gksudo gedit ... bit did)
You could copy and paste your post to a whole load of posts of people having resolution probs here and become a Superhero!
Thanks!

Not at all pleased with the Ubuntu writers though... Before they go on to fancy stuff like "cloud computing" all the basic stuff should be got working. Loads of people with resolution problems and no simple way of fixing them in GUI...

---

### Post by CatKiller on 2009-05-13
> **MarkX said:**
> YeSSS! That worked. (well the gksudo gedit ... bit did)
You could copy and paste your post to a whole load of posts of people having resolution probs here and become a Superhero!
Thanks!

LOL. That's what I've taken to doing. The forum search isn't that great, and new users don't often use it anyway, so the same questions come up time and time again. This is one of them.

My cape's in the post, I think.

> Not at all pleased with the Ubuntu writers though... Before they go on to fancy stuff like "cloud computing" all the basic stuff should be got working. Loads of people with resolution problems and no simple way of fixing them in GUI...There's not really anything that can be done in software; it's a hardware fault. EDID's been a standard for 15 years. You'd think that monitor manufacturers would have got the hang of it by now. Without valid information, there's no way for X to configure the display.

Windows "monitor drivers" are just the values that the manufacturers should have put in the EDID information in the first place, like the refresh rates that you just put in. The Ubuntu team did write an application that would read the information from the Windows driver and configure X appropriately in the manner that you just did, but it needed to be re-written because X changed to the current automatic method and none of the other distributions had started using it yet, so it's being re-done with a more distro-agnostic method. Not finished yet, though, as I understand it.

---

### Post by lazyart on 2009-05-13
Respectfully, most of us have moved well beyond SiS740 video and 1024x768 resolution.  You might find that Ubuntu 9.04 runs slow on that hardware.  I hope your experience is positive, but if not a different distro (or an older Ubuntu) might be in your future.

---

### Post by SunnyRabbiera on 2009-05-13
> **lazyart said:**
> Respectfully, most of us have moved well beyond SiS740 video and 1024x768 resolution.  You might find that Ubuntu 9.04 runs slow on that hardware.  I hope your experience is positive, but if not a different distro (or an older Ubuntu) might be in your future.

Yes though for me I wont replace my out of date MX50 until it catches on fire and explodes, shes still a good monitor despite her age.
My max is 1024x760 and its enough for what I need it for,

---

### Post by MarkX on 2009-05-13
lazyart and catkiller:
Hordes of people want to try Ubuntu and they very often put it on older computers first. That's what Linuxers often suggest for noobs. There are also plenty of people having problems with modern monitors.

I don't think a GUI for entering the resolutions into xorg config like the EDID should would be too difficult?

---

### Post by CatKiller on 2009-05-13
> **MarkX said:**
> I don't think a GUI for entering the resolutions into xorg config like the EDID should would be too difficult?

I've suggested it myself. Hasn't happened yet.

---

### Post by klabezo on 2009-05-14
> **CatKiller said:**
> Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

plz what is my screen values  ?? i cant understand

---

### Post by starcannon on 2009-05-14
klabezo heres a nice modeline generator, this may help. [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

You may need to look at the manuals that came with the monitor, or go to the manufactures website and get the manuals or specifications there.

GL and have fun.

---

### Post by klabezo on 2009-05-14
thank you [starcannon]("http://ubuntuforums.org/member.php?u=242952")

thanks for all

---

### Post by Luca_turicci on 2009-05-16
hey, thanx to those in this post, i seem to have solved my problem too, but i don't know for hoy long..... it always goes back to 960x600 each time i reboot....

---

### Post by longtom on 2009-05-22
> **Luca_turicci said:**
> hey, thanx to those in this post, i seem to have solved my problem too, but i don't know for hoy long..... it always goes back to 960x600 each time i reboot....

I have the same problem with one of the pcs here...

---

### Post by alfredborg on 2009-06-02
Hi, I have the same problem. I cannot go to a resolution higher than 800*600. I have tried this way but still does not work for me. Sorry but I am a newbie to linux commands, so please do bear with me. I have just installed 9.04 ubuntu on my pc. Any one would help me solve my problem please? Thanks

---

### Post by KDante on 2009-06-04
Hi, I have the same problem, that max resolution that I can get is 960x600. This is my graphics card:
klabezo@ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

Connected to 15" LCD Acer AL1521 trough analog D-SUB.

I have tried to edit xorg.conf and still unable get 1024x768 pixels resolution.

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Depth	24
		Modes	"1024x768@75"	"1024x768@85"   "800x600@85"	"800x600@75""800x600@56"	"640x480@85"	"640x480@60"
	EndSubSection
EndSection

---

### Post by spillin_dylan on 2009-06-04
You guys are going to hate me for this... I have the same problem, but backwards.  My resolution starts out at 1600x1200-75Hz, and I keep having to change it back to 1280x1024-60Hz so it doesn't fry my monitor.

---

### Post by SunnyRabbiera on 2009-06-04
This is why getting rid of displayconfig-gtk was a stupid idea, it made editing monitor settings much easier then manually editing xorg.
But it was offed as it would mess up xorg, but so can manaually editing xorg without knowing what to do...
Go figure, thats why I think Ubuntu is long overdue for something like YAST or Mandriva's control center...
Gnome's and KDE's default monitor editors are not enough!

---

### Post by CatKiller on 2009-06-05
> **SunnyRabbiera said:**
> This is why getting rid of displayconfig-gtk was a stupid idea, it made editing monitor settings much easier then manually editing xorg.
But it was offed as it would mess up xorg, but so can manaually editing xorg without knowing what to do...

It wasn't, actually. It was offed because it didn't work with the new X.org and no other distributions used it to help with the re-write. It's being re-done, but slowly. The ability to automatically take the values from the Windows "monitor driver" was a great idea though.

---

### Post by Luca_turicci on 2009-06-05
:D I don't have that problem anymore, now I have 1024*768, but don't remember how the hell I did it... I tried too many different methods to remember wich one worked for me... but i've learned not to mess with Xorg without knowing wath i'm doing :)

---

### Post by ajithvijayas on 2009-07-20
[B]@CatKiller

Re: I want 1024*768 Screen resolution[/B]             
                                                                Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with      Code:
     sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf 
     
Code:
     Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

I tried the above code.
My Manual told H-Frequency 31KHz-69KHz, V-Frequency 56-75Hz. I entered 31 for aa, 69 for bb, 56 for cc and 75 for dd. After this i save the .conf file and restarted the system. It did not work. I dint get desired resolution. Please help

---

### Post by NOTAGEEK on 2009-07-20
my results were different...  i installed 9.04 and had the 8x6 res problem that is very common... i started playing with different nvidia  setups (180, 185 if i remember right) with zero help...

i had my partitions messed up and ended up doing a complete reinstall with the help of this forum and its members and got the partitions right...

at point of the reinstall 9.04 recognized my monitor with the default settings as a vizio 42" 1080p lcd tv and i have res available from 720x400 to 1920x1080 and 60,70, and 75 refresh...

it is recommended that i install the nvidia 180 upgrade but i will leave it well enough alone as i am very new to pc's/9.04 and dont have the know how yet to fix my mistakes...

i wont suggest a complete reinstall to anyone... this is just how i got resolution choices...

thanks...

---

### Post by CatKiller on 2009-07-20
> **ajithvijayas said:**
>  My Manual told H-Frequency 31KHz-69KHz, V-Frequency 56-75Hz. I entered 31 for aa, 69 for bb, 56 for cc and 75 for dd. After this i save the .conf file and restarted the system. It did not work. I dint get desired resolution. Please help

Have you tried putting ```
        Option          "UseEDID"                       "False"
``` in the Device section?

Otherwise, some information about your graphics card and monitor would be useful.

---

### Post by lavallie on 2009-07-20
ARGH!!!  Well I ran a recent update for UBUNTU, graphics adapter was just fine before and now screwed up.

user1@user1-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

How can they release updates that screw up the machine...!!!

Any ideas?

---

### Post by CatKiller on 2009-07-20
> **lavallie said:**
> Any ideas?

I suggest you start a new thread detailing your problem. You'll get more eyeballs that may be able to help that way. This thread is so old and so generic that I shouldn't imagine anyone new is looking at it.

---

### Post by lavallie on 2009-07-20
Thanks.  Anyway the fix for me was here:
[http://ubuntuforums.org/showthread.php?t=891327](http://ubuntuforums.org/showthread.php?t=891327)

Posted by: cdtech
$ sudo dpkg-reconfigure -phigh xserver-xorg
$ sudo /etc/init.d/gdm restart

This fixed the problem

---

### Post by Micke89 on 2009-08-20
I recently installed Xubuntu on my dad's old computer, to make it functional again. 
However, somehow the standard screen-resolution is 1280x1024. Which is too high for the graphics-card/screen, and causes the image to flicker. If I change to 1024x768 the flicker disappears, and the image looks good. But when I log out or restart it changes back to 1280x1024. :( So how do I change the resolution the computer uses as standard?

---

### Post by krustybaguette on 2009-12-28
[QUOTE=CatKiller;

Re: xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.[/QUOTE]

My system: Acer Aspire One AOD250, Karmic Koala as guest in Virtual Box under Host Windows7 Home Premium. 1024x600 screen resolution works just fine in Windows but 800x600  or 640x480 are only options showing up in Ubuntu.
Monitor is "Generic PnP Monitor"
Refresh Rate is 60 Hertz. I couldn't find and Vert Sync spec.

Can I create a xorg.conf file or will Ubuntu generate one for me?

I have two virtual machines installed, the first from the Karmic Desktop CD, the second from the Ubuntu netbook remix. Yhe latter wouldn't boot the last time I tried. I installed it thinking maybe it would solve the netbook video resolution problem, but when it booted I had the same 800x600 and 640x480 choices.

Thanks in advance for any help.

I tried the copy and edit commands above and found no file with the copy command and an empty file with gedit.

KB :confused:

---

