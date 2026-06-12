---
title: "Realtek ALC883 driver to have surround sound"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Santooka on 2009-01-20
dear all,

i am trying to install the realtek-linux-audiopack-5.09 on my ubuntu intrepid ibex, because i am trying since a month from now to make myu surround system works, 4.1 speakers system on my mother board that supports 2, 4, 5.1, 7.1 channel audio; and i couldn't make them work yet....

so after searching i found this audiopack, but because i am not good or understanding in the compiling steps that i am supposed to i want any guide, and here is the README.txt file:

Code:```


The source code copy from [www.alsa-project.org](www.alsa-project.org).      ver:3.3-4
Linux Source Code for ALC audio codec
Support Codec list:
====AC97 Codec=====
ALC100,100P
ALC200,200P
ALC650D
ALC650E
ALC650F
ALC650
ALC655
ALC653
ALC658
ALC658D
ALC850
ALC101
ALC202
ALC250
ALC203

====HD Audio codec ====
ALC260
ALC262
ALC267
ALC268
ALC269
ALC272
ALC660
ALC660VD
ALC662
ALC663
ALC861
ALC861VD
ALC880
ALC882
ALC883
ALC885
ALC888
ALC889A

Installation:
This Source Code is from [www.alsa-project.org](www.alsa-project.org).
For OS installation, please remember add the Development tool kit.
For driver installation, please follow below steps. 

Automatic install: (Recommend RedHat distribution)
execute

  ./install

Note: Ubuntu OS, please use manual install.
      Run commands need to add sudo at first words.   

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support from kernel config 
	(soundcore module, default turn on)

Step 3. Complied source code
	a. cd alsa-driver-1.0.xx
	b. ./configure
	c. make
	d. make install
	e. alsaconf
	f. ./snddevices (Only kernel 2.4 does it)

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)
	 
        snd-xxxx is the card ID.

	-- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
	   --- Intel ICH6 ICH7 ---------
               snd-hda-intel

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
	       snd-via82xx
           --- ATI Chipset  -------------------------------
	       snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
	# ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss

Step 5. reboot your machine

Step 6. Use the alsamixer the disable mute (All audio line default is mute)
        *Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Note: 	1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
	2. Kernel Version must be 2.2.14 or later.
	3. All mixer channels are muted by default. You must use a native
		or OSS mixer program to unmute appropriate channels.
	4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
	5. The driver added to support the SPDIF functoin. 	
	6. a. You can download the alsa-lib-1.0.9 and alsa-utils-1.0.9a form the [www.alsa-project.org](www.alsa-project.org), then unzip and install them. 
	   b. Suggest use "alsamixer" to control mixer function.
	   c. Used "alsaconf" can autodetect which drive you need to install (step 4). 	
        7. SUSE Distribution must install the ncurses package.
```

first i don't understand what's the sound support from the kernel configuration that i am supposed to turn on?

and step 4 and 6.... i can understand step 5

thank you for your support

---

### Post by Santooka on 2009-01-20
in step 4;

i can't find neither modules.conf nor conf.modules ?!

---

### Post by Santooka on 2009-01-20
ok, now no sound at all

and i have no clue where to look at

---

### Post by bernardomtz on 2009-03-15
Santooka,

I guess I have a similar problem as you. Just to not make you wait  I quote the information to answer your doubt about the step 4 in the compilation instructions: 

> Before you send a mail complaining that "I don't have /etc/&#8203;modules.conf, where do I find it &#8230;&#8230;" &#8210; the /etc/&#8203;conf.modules has been deprecated with a few distro's, but in your case it may still be /etc/&#8203;conf.modules. Basically they are both the same, but recent version of modutils use /etc/&#8203;modules.conf instead. Nothing to worry about as such, optionally please update to the latest version of modutils. This should solve your problem. 
(...)
**Debian GNU/Linux users need to save this information into a file in the /etc/&#8203;modutils/ directory (eg. /etc/&#8203;modutils/&#8203;alsa) and run update-modules.**

Note also that the kernel module soundcore has been renamed in Debian kernels >2.6.23 into snd. A workaround is to put a symlink at /lib/modules/x.x.xx/kernel/sound/soundcore.ko pointing to snd.ko 

the full reference can be consulted at:
[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel]("http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel")

The following link might help also:
[http://ubuntuforums.org/showthread.php?t=85581]("http://ubuntuforums.org/showthread.php?t=85581")

But let me explain what is the problem that I have since the begining. This may help a future users.

I decided to install  in an [Acer aspire 6935]("http://www.acerpanam.com/synapse/forms/portal20.cfm?recordid=671&formid=3404&website=AcerPanAm.com&siteid=7117&words=all&keywords=&areaid=2") (with Core Logic Chipset Mobile Intel® GM45 Express) Ubuntu but I could get any sound after installing the OS. I have followed many tutorials to solve the problem but I couldn't get any simple beep from my computer :( 

After many hours of research I found the following important information:

From the  tutorial:

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

I followed some steps,

First I ensured to not turned off the sound (muted) with the **alsamixer** command (see the above tutorial to know how it works)

Then I executed:

lspci -v

and I found that my device was detected  as:
00:1b.0 Audio device:
      Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
      Subsystem: Acer Incorporated [ALI] Device 0146

And the audio devices with the command:

 aplay -l

were:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


After continue searching I found that another user with the same device ALC889 solve the problem following the steps of:
[http://mailman.alsa-project.org/pipermail/alsa-devel/2008-May/007653.html]("http://mailman.alsa-project.org/pipermail/alsa-devel/2008-May/007653.html")

I haven't try this option, but will if the first option doesn't work:
My first option is to get the devices from Realtek the vendor that is the manufacturer of the ALC889 device. The devices can be found at:

[URL="http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false"]
http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false[/URL]

By now I'm trying to follow the instructions for the drivers installation. But I still stuck with the step 2.

If I got any new information I will share it. I hope to have any sound soon. :(

If somebody can help us I really will appreciate it.

---

### Post by Cyberneticbrain on 2009-03-15
I am having the same problem and it is making me crazy. Really would like to have the sound through the HDMI but it just won't work. Using the Asus T-M3N8200. 

> **Santooka said:**
> dear all,

i am trying to install the realtek-linux-audiopack-5.09 on my ubuntu intrepid ibex, because i am trying since a month from now to make myu surround system works, 4.1 speakers system on my mother board that supports 2, 4, 5.1, 7.1 channel audio; and i couldn't make them work yet....

so after searching i found this audiopack, but because i am not good or understanding in the compiling steps that i am supposed to i want any guide, and here is the README.txt file:

Code:```


The source code copy from [www.alsa-project.org](www.alsa-project.org).      ver:3.3-4
Linux Source Code for ALC audio codec
Support Codec list:
====AC97 Codec=====
ALC100,100P
ALC200,200P
ALC650D
ALC650E
ALC650F
ALC650
ALC655
ALC653
ALC658
ALC658D
ALC850
ALC101
ALC202
ALC250
ALC203

====HD Audio codec ====
ALC260
ALC262
ALC267
ALC268
ALC269
ALC272
ALC660
ALC660VD
ALC662
ALC663
ALC861
ALC861VD
ALC880
ALC882
ALC883
ALC885
ALC888
ALC889A

Installation:
This Source Code is from [www.alsa-project.org](www.alsa-project.org).
For OS installation, please remember add the Development tool kit.
For driver installation, please follow below steps. 

Automatic install: (Recommend RedHat distribution)
execute

  ./install

Note: Ubuntu OS, please use manual install.
      Run commands need to add sudo at first words.   

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support from kernel config 
	(soundcore module, default turn on)

Step 3. Complied source code
	a. cd alsa-driver-1.0.xx
	b. ./configure
	c. make
	d. make install
	e. alsaconf
	f. ./snddevices (Only kernel 2.4 does it)

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)
	 
        snd-xxxx is the card ID.

	-- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
	   --- Intel ICH6 ICH7 ---------
               snd-hda-intel

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
	       snd-via82xx
           --- ATI Chipset  -------------------------------
	       snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
	# ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss

Step 5. reboot your machine

Step 6. Use the alsamixer the disable mute (All audio line default is mute)
        *Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Note: 	1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
	2. Kernel Version must be 2.2.14 or later.
	3. All mixer channels are muted by default. You must use a native
		or OSS mixer program to unmute appropriate channels.
	4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
	5. The driver added to support the SPDIF functoin. 	
	6. a. You can download the alsa-lib-1.0.9 and alsa-utils-1.0.9a form the [www.alsa-project.org](www.alsa-project.org), then unzip and install them. 
	   b. Suggest use "alsamixer" to control mixer function.
	   c. Used "alsaconf" can autodetect which drive you need to install (step 4). 	
        7. SUSE Distribution must install the ncurses package.
```

first i don't understand what's the sound support from the kernel configuration that i am supposed to turn on?

and step 4 and 6.... i can understand step 5

thank you for your support

I am just a newbie so please correct me :) In my ETC the config files are not found either, but a warning is shown after make install in step 3d. "config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting". After that its also not possible to preform step 3e salsaconf. I start to have the feeling to try something else except debian to see if it works out then. I would really appreciate your help and my thanks in advance!!> 

---

### Post by bernardomtz on 2009-03-16
Cyberneticbrain / Santooka :

Can you reproduce and hear any sound from your computer? for example the audio test of ubuntu (System > Adminitration > Hardware testing).

Because I have seen that other users have a similar but not the same problem, some of them can hear at least the ubuntu initialization sound. But in my case I can not hear anything. I just want to know if we really have the same problem.

I also have problems with the compilation of the driver, I will try to fix the using the steps of:
[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel]("http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel")
I do not discard the possibility of have to modify the Makefile.
After trying this I will post again. I hope it works... [-o<

---

### Post by markbuntu on 2009-03-16
First, if things are messed up, reinstall ALSA


(1) Remove the ALSA packages

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

(2) Reinstall the same packages

sudo apt-get install linux-sound-base alsa-base alsa-utils

Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:

sudo apt-get install gdm ubuntu-desktop

If you are using xubuntu this will also happen to you

sudo apt-get install gdm xubuntu-desktop

(3) Reboot.

Next, once you 2 channel sound is working, open the file /etc/pulse/daemon.conf

sudo gedit /etc/pulse/daemon.conf

find the line

default-sample-channels = 2

change the 2 to a 5 for 4.1 surround and to a 6 for 5.1 and a 8 for 7.1.

save the file and restart pulseaudio

killall pulseaudio

pulseaudio -D

If you need more help go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I have an ALC883 and it works just fine for me.

---

### Post by Cyberneticbrain on 2009-03-18
Thank you for your reply. But think I resign it doesn't help, never got any sound.....ever. Spend now many evenings and I fail. I'll buy something else to make it work, but it is frustrating that with windows it works fine..and I do not want to see any window at my television screen! :)

1) I made a mistake. If I type lspci it tells nVidia realtek ALC1200 8-channel high defenintion audio codec.

2) The command alsaconf doesn't work.

3) Bernard....hardware checking, play sounds...fails

Who got sound through HDMI on the Asus T-M3N8200 I wonder?!

Thank you for all the effort!

---

### Post by markbuntu on 2009-03-18
If you have an ALC 1200 sound chip (ASUS P5QL-EM mobo) you need ALSA 1.0.17 (which is included in Intrepid) or 1.0.18 or 1.0.19. In any case add the following line to the end of the /etc/modprobe.d/alsa-base file:

```

options snd-hda-intel probe_mask=1

```

This is a specific fix for the ALC1200 chip.

Once you get it working, to get surround sound follow the directions from above.

---

### Post by Cyberneticbrain on 2009-03-19
I keep on failing. Still no sound through HDMI. I did all the steps mentioned but all I have is sound through my headset. I made a clean new install of intrepid. Why it still shows the ALC833 in the sound preferences?

Some of the trouble I ran in with:
~$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.

sudo alsa force-reload
[sudo] password for richard: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/richard/.gvfs
      Output information may be incomplete.
Terminating processes: 5907 6645lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/richard/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/richard/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/richard/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

---

### Post by markbuntu on 2009-03-20
If you want HDMI you need the nvidia driver 177.78 or later since that is the first nvidia driver to support hdmi output. Even so, it does not work in all cases.

---

### Post by Cyberneticbrain on 2009-03-20
Thank you very much for your help Mark. Seems I did my home work bad! Still, it works under windows so I hope once it can work under Linux. I just didn't expect it as I supposed people would buy this barebone for its HDMI. What's the use if no sound synchronised by the same cable. 
I have to do my homework better this time and buy new hardware. This barebone with only one leg will move upstairs. If someone has any suggestions for the right barebone do not wait and PM me please :)

---

### Post by Cyberneticbrain on 2009-03-28
I am starting to get at the point to place a hamer into my asus M3N8200! Why? I gave up the idea to make sound through HDMI working, so now I connected a spdif cable between my television and pc. At the moment I am running Jaunty and whatever I tried still no sound besides on my headphones.
Anybody who has this working?

---

### Post by Cyberneticbrain on 2009-03-29
wish I knew this before......seems I had to buy a V3 instead of a T3

[http://linux-tested.com/products/results/asus_v3-m3n8200.html](http://linux-tested.com/products/results/asus_v3-m3n8200.html)

[http://linux-tested.com/products/results/asus_t3-m3n8200.html](http://linux-tested.com/products/results/asus_t3-m3n8200.html)

---

### Post by Cyberneticbrain on 2009-06-02
Solved!! My great full thanks towards the developers because under Ubuntu 9.04 the sounds through HDMI works perfect. Even at my asus T3 and V3 it works great. Sound now also recognised for the T3M3N8200! Make sure IE958 is selected and select HDA NVIDIA (Alsa mixer).

---

