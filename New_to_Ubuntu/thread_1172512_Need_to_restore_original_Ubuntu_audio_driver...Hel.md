---
title: "Need to restore original Ubuntu audio driver...Help!"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by The MAX on 2009-05-28
So I have the Asus P5Q-Pro and I was watching a movie in VLC and went to put it in 5.1 but it wasn't giving me the option. 
Other wise my audio was working fine, I never even bothered to try the drivers from Asus website. DLed and installed it and after a restart I have no sound.

Does anyone know how I can restore my original audio settings short of reinstalling Ubuntu?
Thanks for the help.

---

### Post by Hospadar on 2009-05-28
You should look at the readme from asus and see if there is any info.

Typically a driver is a kernel module, and if you blacklist the module you installed from asus, whatever was going on before will resume (although the asus driver install may have blacklisted the previous driver)

Could you put a link to the driver you installed, attach any install instructions/readme, etc, etc.  It's sort of hard to say exactly what you should undo before we know what you did.

---

### Post by markbuntu on 2009-05-28
To reinstall ALSA


(1) Remove the ALSA packages. From a terminal:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```
(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```
Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

```
If you are using xubuntu this will also happen to you
```

sudo apt-get install gdm xubuntu-desktop

```
(3) Reboot.

---

### Post by The MAX on 2009-05-29
That didn't seem to work.
also tried this [http://ubuntuforums.org/showthread.php?t=974481&highlight=Audio+Driver+P5Q-Pro]("http://ubuntuforums.org/showthread.php?t=974481&highlight=Audio+Driver+P5Q-Pro")
and this [http://ubuntuforums.org/showthread.php?p=7279149#post7279149]("http://ubuntuforums.org/showthread.php?p=7279149#post7279149")

here is my alsa-base.conf file
> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

and here is the readme for the drivers from the Asus website

> The source code copy from [www.alsa-project.org](www.alsa-project.org).      ver:3.3-4
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
ALC268
ALC660
ALC660VD
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
For driver installation, please follow below steps. 

Automatic install:
execute

  ./install

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support (soundcore module, default turn on)

Step 3. Complied source code
	a. cd alsa-driver-1.0.xx
	b. ./configure
	c. make
	d. make install
	e. ./snddevices

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)
	 
        snd-xxxx is the card ID.

	-- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
	   --- Intel ICH6 ICH7 ---------
               snd-hda-intel
           --- ATI chipset -----
	       snd-atiixp

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

I have audio for somethings but if I try to watch a movie the 5.1 audio I get nothing, not even an option to put it in stereo.
Thanks for the help guys.

---

