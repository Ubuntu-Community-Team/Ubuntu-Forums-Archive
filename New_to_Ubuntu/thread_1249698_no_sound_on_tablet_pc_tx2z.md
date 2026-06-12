---
title: "no sound on tablet pc tx2z?"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-08-25
tryed UnMuteing in 
```
alsamixer
```

mm=unmute right?
or is it 00?

anything else i can do?

---

### Post by Ayuthia on 2009-08-25
> **R3fr4cti0n said:**
> tryed UnMuteing in 
```
alsamixer
```

mm=unmute right?
or is it 00?

anything else i can do?

mm=mute and 00=unmute.

Have you tried:
```
sudo echo "snd-hda-intel model=toshiba" >> /etc/modprobe.d/alsa-base
```
This is from the [HOWTO setting up ubuntu 8.10 intrepid on the HP tx2z tablet pc]("http://ubuntuforums.org/showthread.php?t=1038898") thread.  Once you add that, the easiest way to test it is to restart your computer.

---

### Post by Favux on 2009-08-25
For Jaunty (9.04) use (enter in a terminal):
```
sudo echo "snd-hda-intel model=toshiba" >> /etc/modprobe.d/alsa-base.conf
```
Reboot.  They renamed alsa-base to alsa-base.conf going from Intrepid to Jaunty.

It adds the line:  snd-hda-intel model=toshiba
To the end of the file "alsa-base.conf" located in the directory "/etc/modprobe.d/".  You could also add the line by directly editing alsa-base.conf by using in a terminal:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Save, close.  Reboot.

---

### Post by R3fr4cti0n on 2009-08-25
> **Favux said:**
> For Jaunty (9.04) use (enter in a terminal):
```
sudo echo "snd-hda-intel model=toshiba" >> /etc/modprobe.d/alsa-base.conf
```Reboot.  They renamed alsa-base to alsa-base.conf going from Intrepid to Jaunty.

It adds the line:  snd-hda-intel model=toshiba
To the end of the file "alsa-base.conf" located in the directory "/etc/modprobe.d/".  You could also add the line by directly editing alsa-base.conf by using in a terminal:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```Save, close.  Reboot.
  
ya i tried that back a few thought it was wrong for my tx2z cause it saids toshiba just tried it again n got the same error

bash: /etc/modprobe.d/alsa-base.conf: Permission denied

---

### Post by Favux on 2009-08-25
Hi R3fr4cti0n,

Both sudo and gksudo make you root.  With root you have all permissions.  So you must not be doing something right.

When you log on and enter your user name you also enter a password.  With gksudo when it pops up the box it wants the same password.  Give it to it and then you will be root.  That's why you want to edit just that one file with the Text Editor (gedit) that pops up.  You've now made it a root editor and you can seriously mess up other files if you use it to access them.  You want to close it right away after you've saved your edit, adding the line to the bottom.

---

### Post by R3fr4cti0n on 2009-08-25
favux i opened the terminal pasted ```
sudo echo "snd-hda-intel model=toshiba" >> /etc/modprobe.d/alsa-base.conf
```

push enter and i get 
 
bash: /etc/modprobe.d/alsa-base.conf: Permission denied
julian@Abriella:~$ 

did i serously mess that up?

---

### Post by Favux on 2009-08-25
R3fr4cti0n,

That's not the line to use with gksudo gedit.  This is the line you add to the bottom of the file:
```
options snd-hda-intel model=toshiba
```
(actually we both forgot options, oops)
The line:
```
sudo echo "options snd-hda-intel model=toshiba" >> /etc/modprobe.d/alsa-base.conf
```
Does it all in one step.  sudo makes you root, echo is like print and >> directs it to the file alsa-base.conf in the /etc/modprobe.d/ directory.  See the difference?

---

### Post by R3fr4cti0n on 2009-08-25
> **Favux said:**
> R3fr4cti0n,

That's not the line to use with gksudo gedit.  This is the line you add to the bottom of the file:
```
options snd-hda-intel model=toshiba
```(actually we both forgot options, oops)
The line:
```
sudo echo "options snd-hda-intel model=toshiba" >> /etc/modprobe.d/alsa-base.conf
```Does it all in one step.  sudo makes you root, echo is like print and >> directs it to the file alsa-base.conf in the /etc/modprobe.d/ directory.  See the difference?
   

i put it at the bottem as you siad still no sound this is what i have.. is this serously beyond my understanding? am i not really getting this? 

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
sudo echo "options snd-hda-intel model=toshiba" >> /etc/modprobe.d/alsa-base.conf
```

---

### Post by Favux on 2009-08-25
Yes you are not getting it.  Instead of:
```
sudo echo "options snd-hda-intel model=toshiba" >> /etc/modprobe.d/alsa-base.conf
```
it should be:
```
options snd-hda-intel model=toshiba"
```
Then reboot.

Like I said the first line is a different way of adding
```
options snd-hda-intel model=toshiba"
```
to the file.

---

