---
title: "low volume on PC spkr (not beep)"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by yoshimandk on 2008-12-26
OK folks this has been a tricky time getting audio to work. I pretty much a newbie so i thought Id err on the safe side and post here, but this is a sound issue.

Just installed intrepid (8.10) and I had sound problems from the get go. for a few days I thought I had no sound. I tryed maxing out everything in any mixer i had --the default mixer next to the clock (everything is checked and maxed) alsa from the terminal, the alsa gnome GUI.. no help.

Interestingly I have no ticker for anything that looks like pcspkr or internal sound or anything like that i can control. Mono is all the way up too. 

I also had playback problems in skype so i had no audio. Ultimately I found one day I had audio on the headphone and line out jacks. (yay). except i usually use the internal PC speaker. (my speakers have power issues) (boo) 

uninstalling pulseadio and running apt-get install esound (or something simlar i found the fix on someones blog i cant seem to find again) fixed my audio woes in skype. later that night i noticed i did have sound from the internal speaker but it was very, very low. Was this there before? i dont know. sound on the line out and headphone jacks is fine. What i am looking to do is turn that internal speaker all the way UP!

heres some info for ya:
machine is a Lenovo 6075-BJU (desktop)

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
um I know theres a terminal command to output the volume levels for everything but i dont remember what that was. 


Ive come across nothing that helps. i have some out-there ideas though. I read on one forum for lenovo laptops the modem has to be enabled in the BIOS for audio to work. I saw nothing about modems in my BIOS, although i have the intel bios extension i havent looked at yet. 

also i heard anecdotally about people who had volume muted or low in windows and installed linux, and then couldnt raise their volume level.
My last distro was arch, perhaps my audio was low on that installation and it carried over somehow. I did reseat the motherboard battery to try and eliminate anything stored at the hardware level (shooting in the dark here...) but that didnt help. I wonder if using a PE (windows live disk) could allow me to  get to the audio controls i need and up them?

yeah the above is a little crazy but im out of ideas. eitherway something like bartPE has to be compiled in windows so im not even sure if i could do that in wine. 

questions comments and limericks appreciated!!!

thanks

---

### Post by yoshimandk on 2008-12-26
i also just noticed the above post is grammatically speaking, a mess. my apologies

---

### Post by druellan on 2008-12-26
You can try this. Edit /etc/modprobe.d/alsa.base (use on a terminal: sudo gedit /etc/modprobe.d/alsa.base) and add at the bottom:
options snd_hda_intel model=basic

Reboot and check if that helps (open the mixer and check if there are new controls there). If not, update the Alsa drivers to the latest version here: [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

Good luck!

---

### Post by namdung on 2008-12-26
In terminal type:

```
alsamixer
```

use the arrow keys to increase the volume.

---

### Post by yoshimandk on 2008-12-26
should there be any text in etc/modprobe.d/alsa.base? there is no text in that file right now before adding the above line...

---

### Post by druellan on 2008-12-26
Mmmm yes. Ubuntu's installer supposed to fill up this file with some config defaults. Seems weird that your's empty but you can try adding the options snd_hda_intel model=basic line to see what happens.

BTW this is my alsa-base:

```
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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
```

---

### Post by 2hot6ft2 on 2008-12-26
> **yoshimandk said:**
> 
uninstalling pulseadio and running apt-get install esound (or something simlar i found the fix on someones blog i cant seem to find again)
Probably the 4th link below would sound familiar then.

Here are a few options to choose from from fixing pulse to disabling it and using asla, or replacing pulse with esound.

First fixing pulse
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Disabling pulse and using alsa (Before deciding to remove pulse you should read the warning here as to what the result could be).
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)
and another one going the same route here
[http://ubuntuforums.org/showthread.php?p=6370902#post6370902](http://ubuntuforums.org/showthread.php?p=6370902#post6370902)

Replacing pulse with esound
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

There are more but this gives you some alternatives that are being used.

---

### Post by yoshimandk on 2009-01-03
sorry if this came off looking like a dead thread... in true noob fashion i wrote in the alsa update thread that id be away for a week and thanks for the help so far instead of in this one.  anyway im back now and ill be trying all of this.

---

