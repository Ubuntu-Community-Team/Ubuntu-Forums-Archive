---
title: "No sound on my Asus notebook"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by Kurt S on 2011-07-02
Hi everyone, I've resolved a lot of problems by searching through these forums but I have one I can't figure out. I did a dual boot install on a new Asus N53JF notebook with Windows 7 and Maverick (10.10). Everything worked immediately on the fresh Maverick install and then I messed it up. I have Maverick installed on a Dell D600 and so I migrated my home folder over to the new machine. It recognized all of my settings and preferences but the sound quit. I don't get any sound running any apps or other basic notification type sounds. I'm guessing there's a command somewhere that is pointing to the wrong place but I don't know where to start. I checked all of my basic sound preferences and they're set up where they should be. This happened after the home migration so I figure it must be a command or wrong driver.
  I'm starting to figure out my way around the command line but I'm still pretty green. I've attached a screenshot of some info of my sound card as a starting point, but where do I go from here? Any help would be appreciated.

[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by CatKiller on 2011-07-03
> **Kurt S said:**
> I migrated my home folder over to the new machine. It recognized all of my settings and preferences but the sound quit. I don't get any sound running any apps or other basic notification type sounds. I'm guessing there's a command somewhere that is pointing to the wrong place but I don't know where to start.

My first instinct is that if you have a ~/.asoundrc file then you might want to try renaming it to something else. It's the most likely sound-based configuration file in your Home folder.

---

### Post by Kurt S on 2011-07-03
That's what I'm having trouble with. I look through my home folder and can't find anything that looks like it's a problem. I've gone through every .conf file and haven't found anything. I haven't found "asound" or any "sound" file in there. Here's a screenshot of my home folder. If you see anything that you can point me to it would help.

I've also been looking through the "hda-intel sound how to" document but it looks like something to do if it didn't work on the install. Also my codec isn't listed, I have a Realtek ALC259. I'm guessing it's the same as ALC260. When I look in my file system it seems like the alsa files are there. Should I go through this "how to" troubleshoot?

Thanks.

---

### Post by CatKiller on 2011-07-03
If you haven't got a per-user ALSA configuration that's been overwritten with the Home folder copy, possibly you've got a per-user PulseAudio configuration that's pointing at the old sound card. You could try renaming the .pulse folder to something else.

(I tend to recommend renaming rather than deleting since if it all goes pear-shaped it's reasonably straightforward to change things back - from the command line if need be - in case you were wondering)

Otherwise, yeah, it's a case of checking which devices are installed and making sure that you're configured to use them. ```
aplay -l
``` and *padevchooser* will probably be useful tools to that end.

---

### Post by Kurt S on 2011-07-03
Thanks for the suggestions, I'm still having no luck though. I renamed my ~/.pulse folder to ".old_pulse" and restarted. It made a new ~/.pulse folder with fewer files, so there were some old ones in there. It still didn't give me any sound.

I also installed padevchooser from Synaptic and looked in the device chooser. The server, sink and source point to the ~/.pulse folder and the default packages with the alsa devices in them. I've attached a screenshot.

Here's some more info on my chipset and card. To me it looks like I need the HDA Intel driver?

sudo lshw -c sound
[sudo] password for kurt: 
  *-multimedia            
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:48 memory:d9c00000-d9c03fff
kurt@Asus:~$ 


kurt@Asus:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
kurt@Asus:~$ 

Here's the contents of my /etc/modprobe/alsa-base.conf file:

[I]# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules[/I] [I]
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

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)[/I] [I]
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2[/I]

I can't see an HDA-Intel driver in there. Do I need to add that to this file? If so, what should it say? Am I going in the right direction or totally off base?

I've also been looking at the SoundTroubleshootingProcedure in Ubuntu documentation: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
It looks like it's for installs that didn't work originally so would it be of benefit to go through this?
I also found another thread: [http://ubuntuforums.org/showthread.php?t=1316634](http://ubuntuforums.org/showthread.php?t=1316634)
Could I do a purge and re-install of alsa and pulse or would it cause more harm than good?
Sorry I'm taking so long to respond but I'm doing a lot of reading to try and figure this out.

Thanks.

---

### Post by Kurt S on 2011-07-03
Well after burning my whole day on this I finally got it figured out after reading through many posts and documents in various sites. I opened /etc/modprobe.d/alsa-base.conf in gedit and added
 ```
options snd_hda_intel model=auto
``` "auto" is the default I tried for Realtek ALC259 which I found [here]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt").
I shut everything down and rebooted and it worked! I should have tried that sooner!

---

### Post by CatKiller on 2011-07-04
Glad you got it sorted.

---

### Post by Kurt S on 2011-07-04
Thanks CatKiller for taking the time to respond to me. I'm glad I got it figured too. I have an excellent setup now with all of my docs, pictures, etc. stored on a common partition that can be accessed whether I'm in Ubuntu (99% of the time) or Windows. My home folder's in it's own partition too. I'm loving my new laptop!

Thanks to people like you there's lots of information here that I can peruse to problem solve and design a great setup like this.

---

