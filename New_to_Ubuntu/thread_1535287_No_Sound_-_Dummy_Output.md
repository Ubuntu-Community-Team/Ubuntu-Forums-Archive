---
title: "No Sound - Dummy Output"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by dondiego2 on 2010-07-20
I turned my computer on today and went to watch a lecture in a class I am taking remotely and -no sound!  I have been struggling with this all day.  In sound preferences under Output it says "Dummy Output".  There are no other devices to choose.  Under the hardware tab there is nothing listed.  I know I have a an NVIDIA MCP51 chip on my motherboard.  It works in Windows XP but will not work in Ubuntu - although it was working yesterday.  Help!

---

### Post by lidex on 2010-07-21
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by dondiego2 on 2010-07-21
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)


```
carl@carl-desktop:~$ uname -a
Linux carl-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
carl@carl-desktop:~$ aplay -l
aplay: device_list:223: no soundcards found...
carl@carl-desktop:~$ dpkg -l | "alsa"
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}
carl@carl-desktop:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
carl@carl-desktop:~$ 

```

I have a Compaq Presario desktop.  I had given up and burned a fresh 10.04 disk to reinstall but that doesn't even work.  It won't run, it just shuts my monitor down...but that's a different problem.

---

### Post by dondiego2 on 2010-07-21
Just an update.  It seems sound plays when I am in Firefox and go to youtube.  I get sound.

I just don't hear anything when I start up Ubuntu, or if I play anything with one of my sound or video programs, i.e. VLC, Rhythmbox, etc.

---

### Post by lidex on 2010-07-21
OK. Do this.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

Now this. Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
**Reboot.**

---

### Post by dondiego2 on 2010-07-22
[QUOTE=lidex;9620055]OK. Do this.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```**Logout/in.**

Here is what happened when I ran that:
```
carl@carl-desktop:~$ rm -r ~/.pulse ~/.asound*
rm: cannot remove `/home/carl/.asound*': No such file or directory

```
```
carl@carl-desktop:~$ sudo rm /etc/asound.conf
rm: cannot remove `/etc/asound.conf': No such file or directory

```

When I did the update/upgrade all it found was two updated to grub.  Still no sound.

---

### Post by lidex on 2010-07-22
Did you re-install alsa?

---

### Post by dondiego2 on 2010-07-22
> **lidex said:**
> Did you re-install alsa?


Yes I did and also rebooted and no change.  I also have no volume control on the top panel.  I just re-added the indicator applet and the only thing that show up is the envelope.  Still no sound.

---

### Post by lidex on 2010-07-22
Thought I posted this already but I don't see it. Try this:
```
sudo apt-get install gnome-media gnome-media-common
```
logout/in

---

### Post by dondiego2 on 2010-07-22
> **lidex said:**
> Thought I posted this already but I don't see it. Try this:
```
sudo apt-get install gnome-media gnome-media-common
```logout/in


Here are the results of the command:
```
carl@carl-desktop:~$ sudo apt-get install gnome-media gnome-media-common
[sudo] password for carl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-media is already the newest version.
gnome-media-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
carl@carl-desktop:~$ 

```

I didn't bother rebooting since nothing was installed.

---

### Post by lidex on 2010-07-22
Do you have all these installed? See screen.

---

### Post by dondiego2 on 2010-07-22
> **lidex said:**
> Do you have all these installed? See screen.


I was missing two of those including the sound indicator app.  So now I have my volume indicator back (thanks!) but still showing a Dummy Output and no sound.

---

### Post by lidex on 2010-07-22
How about this output:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

And let's see this again please. 
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**

---

### Post by dondiego2 on 2010-07-22
> **lidex said:**
> How about this output:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```And let's see this again please. 
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**


Here is the first one:
```
carl@carl-desktop:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
[sudo] password for carl: 
Specified filename /dev/snd/* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/dsp:            carl       1837 F.... plugin-containe
/dev/dsp0:           carl       1837 F.... plugin-containe
/dev/dsp_in:         carl       1837 F.... plugin-containe
/dev/dsp_mmap:       carl       1837 F.... plugin-containe
/dev/dsp_multich:    carl       1837 F.... plugin-containe
/dev/dsp_out:        carl       1837 F.... plugin-containe
carl@carl-desktop:~$ 

```

Here is the rest again:

```
carl@carl-desktop:~$ uname -a
Linux carl-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
carl@carl-desktop:~$ aplay -l
aplay: device_list:223: no soundcards found...
carl@carl-desktop:~$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-oss                              1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                       0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                          0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transitional package
rc  libsdl1.2debian-alsa                  1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA options)
ii  libsox-fmt-alsa                       14.3.0-1.1build1                                SoX alsa format I/O library
carl@carl-desktop:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

```

---

### Post by lidex on 2010-07-22
Did you install these for a reason:
> ii  libesd-alsa0                          0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transitional package
rc  libsdl1.2debian-alsa                  1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA options)

Something is blocking alsa from your soundcard. Try removing those through synaptic.
This is pretty screwy. Need more info. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by kozmos on 2010-07-22
> **lidex said:**
> OK. Do this.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

Now this. Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
**Reboot.**

Hi. I had the same problem but double-whammied with no sound on youtube or flash.

Coupled with the solution above, try playing around with the volume control options. (configuration tab)

I think it may be a conflict of drivers and configs between alsa and pulse. (i think)

---

### Post by dondiego2 on 2010-07-22
> **lidex said:**
> Did you install these for a reason:

Something is blocking alsa from your soundcard. Try removing those through synaptic.
This is pretty screwy. Need more info. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```Enter your user password when prompted. Provide a link for the output or post it here using code tags.


You lost me with this last request.  Where do I copy this?  Is it in the "file system" and "usr"?  Under "usr" are other folders such as "bin" etc.  I tried just copying to "usr" and when I try to run it in terminal it can't find it.

I uninstalled those two programs through Synaptic and it uninstalled all kinds of programs I had installed including Rhythmbox which I have since reinstalled.

---

### Post by lidex on 2010-07-23
> **dondiego2 said:**
> You lost me with this last request.  Where do I copy this?  Is it in the "file system" and "usr"?  Under "usr" are other folders such as "bin" etc.  I tried just copying to "usr" and when I try to run it in terminal it can't find it.

I uninstalled those two programs through Synaptic and it uninstalled all kinds of programs I had installed including Rhythmbox which I have since reinstalled.

In home, your user folder. If your user name is lidex it would be /home/lidex/ or ~/
I do it that way because the terminal defaults to a users directory. I can have someone run a command without having to explain how to change directories which makes it easier with noobs especially when people just want the problem fixed and could care less about learning terminal commands.

---

### Post by dondiego2 on 2010-07-23
OK.  I ran your script and produced an output file.  Do you want me to copy and paste it here or do you want me to sent it to you?

---

### Post by dondiego2 on 2010-07-23
> **kozmos said:**
> Hi. I had the same problem but double-whammied with no sound on youtube or flash.

Coupled with the solution above, try playing around with the volume control options. (configuration tab)

I think it may be a conflict of drivers and configs between alsa and pulse. (i think)


I cannot get PulseAudio to recognize my sound card  So when I go to the configuration tab it says there are no sound cards to configure.  Hence "Dummy Output".

---

### Post by lidex on 2010-07-23
Yeah, post it here. Use the code tags.

---

### Post by dondiego2 on 2010-07-23
> **lidex said:**
> Yeah, post it here. Use the code tags.


Here is is:

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Fri Jul 23 11:34:26 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"


!!DMI Information
!!---------------

Manufacturer:      Compaq Presario 061
Product Name:      EX325AA-ABA SR1950NX NA670


!!Kernel Information
!!------------------

Kernel release:    2.6.32-23-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:10.1 0403: 10de:026c (rev a2)
    Subsystem: 103c:2a3e


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------



!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:223: no soundcards found...

ARECORD

arecord: device_list:223: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
isofs
udf
crc_itu_t
aes_i586
aes_generic
binfmt_misc
ppdev
oss_usb
oss_hdaudio
osscore
arc4
b43
mac80211
cfg80211
usbhid
usblp
led_class
fbcon
tileblit
font
bitblit
softcursor
k8temp
nvidia
agpgart
vga16fb
vgastate
i2c_nforce2
lp
parport
hid
ohci1394
usb_storage
8139too
8139cp
mii
ssb
ieee1394
pata_amd
sata_nv
forcedeth


!!ALSA/HDA dmesg
!!------------------
```

---

### Post by lidex on 2010-07-23
This is all I need to see:
```
!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.22
Utilities version:  1.0.22

```
Borked alsa install.

Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
**Reboot.**

---

### Post by dondiego2 on 2010-07-23
OK, I followed your instructions and now it is worse.  All I get out of sound is a high pitched hum,  and it still says dummy output.

---

### Post by dondiego2 on 2010-07-23
> **dondiego2 said:**
> OK, I followed your instructions and now it is worse.  All I get out of sound is a high pitched hum,  and it still says dummy output.

Here is the output from your script again if it helps.

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sat Jul 24 02:37:11 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      Compaq Presario 061
Product Name:      EX325AA-ABA SR1950NX NA670


!!Kernel Information
!!------------------

Kernel release:    2.6.32-23-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:10.1 0403: 10de:026c (rev a2)
    Subsystem: 103c:2a3e


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------



!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:223: no soundcards found...

ARECORD

arecord: device_list:223: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
isofs
udf
crc_itu_t
aes_i586
aes_generic
binfmt_misc
ppdev
oss_usb
oss_hdaudio
osscore
arc4
b43
fbcon
mac80211
tileblit
font
bitblit
cfg80211
softcursor
nvidia
usbhid
led_class
agpgart
vga16fb
i2c_nforce2
k8temp
vgastate
usblp
lp
parport
hid
ohci1394
8139too
usb_storage
8139cp
mii
ieee1394
ssb
pata_amd
sata_nv
forcedeth


!!ALSA/HDA dmesg
!!------------------



```

---

### Post by lidex on 2010-07-23
Did you reboot?
Are you/were you using OSS??
Show the contents of this file please:
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by dondiego2 on 2010-07-23
> **lidex said:**
> Did you reboot?
Are you/were you using OSS??
Show the contents of this file please:
```
cat /etc/modprobe.d/alsa-base.conf
```

Yes I rebooted.  What is OSS?  I may have installed something trying to get RealPlayer to work.  I don't know, but at one time everything worked but RealPlayer, then nothing worked but RealPlayer, now nothing works.

Here is the result you asked for:

[CODEcarl@carl-desktop:~$ cat /etc/modprobe.d/alsa-base.conf
# autoloader aliases
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
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
][/CODE]

---

### Post by dondiego2 on 2010-07-23
```
carl@carl-desktop:~$ cat /etc/modprobe.d/alsa-base.conf
# autoloader aliases
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
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

```

---

### Post by lidex on 2010-07-24
Output of this command please:
```
dpkg -l | grep "OSS"

```

---

### Post by dondiego2 on 2010-07-24
I got kind of POed and found Computer Janitor in Administration.  I just ran that and it removed a boat load of files.  I rebooted and all my sound is back.  It also removed RealPlayer which probably started my issues.  

The classes I am taking have lectures that I play on my computer and they wanted me to use RealPlayer.  I saw that there was a version for Linux so I tried to use it and the video played great but no sound.  So when I tried to fix the sound in RealPlayer I probably screwed everything else up.  I will just try and play the files in VLC and hopefully they will play fine.

I am going to bed now.  I will check it out tomorrow and let you know.

Thank you very much for all the help you gave me and for your patience.

Also, the Dummy Output is now gone.  Sound preference lists the correct hardware and drivers now.

---

### Post by renkinjutsu on 2010-07-24
A good trick is to start pulseaudio as a daemon before anything starts and hogs the audio card.. I put```
su *myuser* -c "pulseaudio -D
```
into my /etc/rc.local so it runs before i even log in. I did that just to make sure pulseaudio gets to hog my soundcard first.

---

