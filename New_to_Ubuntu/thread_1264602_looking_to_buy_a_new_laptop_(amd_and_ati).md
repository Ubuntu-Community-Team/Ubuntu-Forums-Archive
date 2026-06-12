---
title: "looking to buy a new laptop (amd and ati)"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by yoshiki2 on 2009-09-12
what laptop that is fully supported and compatible with ubuntu and kubuntu can i buy? I know buying any intel nvidia would be easier, but i wanna support the underdog.

---

### Post by NoaHall on 2009-09-12
AMD is a good processor to go with, but ATI? Seriously? If you're going to do that, you'll have a long hard few months/years depending on when the OS version of the ATI drivers are released.

---

### Post by sph on 2009-09-12
Not amd/ati but very easy:HP550. Cheap, well built and ubuntu works like a charm. I've set up two so far 

Cheers,
sph

---

### Post by PhoHammer on 2009-09-12
I loved my AMD with ubuntu/many other GNU/Linux's.

I know you can usually get a better AMD cpu in laptop for the same price as another 
machine with intel...

---

### Post by NexusZA on 2009-09-12
If you feel you really want to get an ATI laptop, [you can check out a thread I posted today]("http://ubuntuforums.org/showthread.php?t=1264546") about a way to get the AMD drivers working in Jaunty. Its a long winded process but I have used it succesfully on two machines. Just remember, it may not work on yours and then you may be in for a long wait till AMD update them correctly.

---

### Post by yoshiki2 on 2009-09-12
then amd and nvidia.. any advices?? am looking for 4 gigabytes ram and turion x2 ultra (that one is the last processor i think)

---

### Post by Truefire on 2009-09-12
I've had a TON of problems with AMD and ATI cards. It's not worth it man.

---

### Post by zman58 on 2009-09-12
I recently set up a HP laptop for my son. It is Dual Core AMD Athlon X2 with Nvidia 8200 graphics. The model is HP G60-244DX. It is a great machine and there are others like it in the HP lineup. Everything worked perfectly including wireless. The Nvidia graphics are great and the overall system is very fast. Here are the basic instructions I wrote down as I set it up with Ubuntu. I set it up as a dual boot system Windows/Ubuntu although all I ever see my son use on it is Ubuntu :)

Notice how much time (many hours) it takes to fuss around with Windows Vista :(
I would stay with Nvidia for graphics for now--fast and snappy graphics. But never fear; Soon the ATI open-source drivers will be ready then AMD/ATI will be the way to go. Intel graphics are also a good alternative because the Intel video driver works very well, however the Intel graphics chips are somewhat slow.

[INDENT]Setting up Ubuntu 9.04 on HP G60-244DX Laptop
2009-08-03

Wait!
Do not start Windows.
Do not power up the machine for the first time yet!

How to access the BIOS setup program in the HP G60 laptop:
	Press and hold F10 key while power-up button has been activated.

While in the BIOS program, Change boot options in BIOS boot order to CD, USB, then Hard Drive.

Boot from CD or USB to backup the entire system disk drive: 
	Make a full system drive backup for emergency recovery purposes 
	Use a reliable external USB drive as target for full system drive backup
	Using Ghost v11 for this (took ~2 hours)
	Boot Ghost from CD or Boot Ghost from USB (either should work)
	There are some other backup options available (TBD)

Start Windows Vista for first time now...

Go through Windows setup (takes ~1 hour of fussing around)
	Don't allow Norton Antivirus to install.

Apply updates for Windows.
	Setup automatically leads you through update process (~3 hours)

Completely remove Norton Antivirus software. (save $$ and processor resources)

Install AVG antivirus (The free home version) [http://free.avg.com/](http://free.avg.com/)

Defrag Windows NTFS partition C: (takes ~4 hours)

Disable Windows System Restore (Shadow Copy) service (frees additional ~70GB of drive space) on drive C:

Use the disk management tool in Vista to resize Windows NTFS partition (takes ~2 minutes)

	I created 120 GB of free space by reducing the size of the NTFS
	
Power down. Now you are ready to install Ubuntu

Now it is time to begin the process of installing Ubuntu onto the G60

Installing Ubuntu-9.04-desktop-i386 on the G60... (entire process ~1 hour)

Boot the Ubuntu live CD. Select all defaults until partitioner comes up. Make
sure to install Ubuntu into the free space which was created when the Windows
NTFS drive was resized.

Installing Ubuntu:
 - Let update run. It will start automatically after loggin into main account.

 - Synaptic - Add Third-Party repositories to sofware sources (source repositories are optional here)

 - Enable the nvidia graphics driver in "System - Administration - Hardware Drivers"

 - Remove mono-runtime (this will remove several apps including f-spot and tomboy)

 - Add zim (replaces tomboy)

 - Add vim-gnome

 - Add flashplugin-installer

 - Add msttcorefonts

 - Add gphoto2

 - Add showfoto

 - Add qcad and partlibrary

 - Add inkscape

 - Add smbfs

 - Add gnome-mplayer

 - Add gstreamer0.10-ffmpeg

 - Add gstreamer0.10-plugins-ugly

 - Add gstreamer0.10-plugins-bad

 - DVD playback. Add CSS (content scrambling system) using script:
   sudo /usr/share/doc/libdvdread4/install-css.sh
   ([https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html))

 - Blacklist the pc speaker. It is too loud.
   /etc/modprobe.d/blacklist.conf "blacklist pcspkr"

 - Provide required accounts under the system menu.

 - Connect to home wireless. provide wireless key to network manager.

 - Get a .mp3 file and try to play it with Rhythmbox. Search for codecs when asked
 and install the suggested codecs (ffmpeg, gstreamer).

 - Get a .mpg file and try to play it with Movie Player. At first it seemed that sound
 did not work with mpg playback. Added mplayer-gnome and now sound works with mpg playback.[/INDENT]

---

### Post by Philip550c on 2009-09-19
I love my $400 Gateway netbook
[http://www.gateway.com/systems/product/529668275.php]("http://www.gateway.com/systems/product/529668275.php")

AMD 64bit and ATI card, 250Gb hard drive, 2GB DD2, fullsize keyboard. I think its perferct for a small laptop.

---

### Post by zkriesse on 2009-09-19
DO NOT GO WITH ATI!!!!!!!! And 64 bit is a little difficult as well depending on the graphics card...and Dell is better with Ubuntu than HP...keep that in mind

---

### Post by Philip550c on 2009-09-19
although I do like my amd/ati laptop, I do agree with everyone else that I have had a much better experience with my nvidia/intel desktops.

---

### Post by sideaway on 2009-09-30
I own two intel/ATi machines one intel/nVidia machine... I seriously recommend nVidia. The issues I've had with the ATi machines mount up to quite a handful. Didn't realise that there were compatibility issues with AMD chipsets?

---

