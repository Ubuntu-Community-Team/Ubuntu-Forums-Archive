---
title: "SB Audigy SE (No Sound)"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by Cleveland Rock on 2009-08-16
Hello. I can't seem to get any sound at all in Ubuntu except for the drums at the login screen. There seem to be various threads and tutorials about this, but they all seem geared towards people with a lot more knowledge than me.

I have a Creative Labs Sound Blaster Audigy SE sound card. I installed Ubuntu via Wubi yesterday. I can't find any Linux drivers or anything. Can you help me?

Thanks.

---

### Post by northern lights on 2009-08-16
Please post the outputs of ```
sudo lshw -C multimedia
```and```
aplay -l
```Thank you.

---

### Post by Cleveland Rock on 2009-08-16
```
clevelandrock@ubuntu:~$ sudo lshw -C multimedia
  *-multimedia            
       description: Audio device
       product: 82801JI (ICH10 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia
       description: Multimedia audio controller
       product: CA0106 Soundblaster
       vendor: Creative Labs
       physical id: 1
       bus info: pci@0000:05:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=CA0106 latency=64 maxlatency=20 mingnt=2 module=snd_ca0106
clevelandrock@ubuntu:~$ 
``````
clevelandrock@ubuntu:~$ sudo lshw -C multimedia
  *-multimedia            
       description: Audio device
       product: 82801JI (ICH10 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia
       description: Multimedia audio controller
       product: CA0106 Soundblaster
       vendor: Creative Labs
       physical id: 1
       bus info: pci@0000:05:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=CA0106 latency=64 maxlatency=20 mingnt=2 module=snd_ca0106
clevelandrock@ubuntu:~$ clear

clevelandrock@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: Intel [HDA Intel], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
clevelandrock@ubuntu:~$ 
```

---

### Post by khelben1979 on 2009-08-16
Try this:
```
sudo modprobe sb
```

and let us know if it works.

---

### Post by Cleveland Rock on 2009-08-16
```
clevelandrock@ubuntu:~$ sudo modprobe sb
[sudo] password for clevelandrock: 
FATAL: Error inserting sb (/lib/modules/2.6.28-15-generic/kernel/sound/oss/sb.ko): No such device
clevelandrock@ubuntu:~$ 
```

---

### Post by khelben1979 on 2009-08-16
Hmm, you wrote that you hear the drums at the login. If this is the case, the sound drivers are working.
Have you tried [alsamixer]("http://en.wikipedia.org/wiki/Alsamixer")gui?

```
sudo apt-get install alsamixergui
``` to install it if it's not in the system already. You will then be able to check all the volume meters.

---

### Post by Cleveland Rock on 2009-08-16
I don't hear the drums all the time; just some of the time. Also, I don't remember the last time I heard them.

As for alsamixergui, I got it, but I don't know what to do with it.

---

### Post by khelben1979 on 2009-08-16
Thanks for the screen dump. That does not look good, there should be a lot of meters to click on.

You can try:
```
sudo alsaconf
```

Then choose your sound card from the list. If your system lacks alsaconf, then the problem is that [the Alsa Sound System]("http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture") isn't installed correctly or that it's not installed at all.

---

### Post by khelben1979 on 2009-08-16
[Here's a page]("http://www.alsa-project.org/main/index.php/Matrix:Main#Drivers") with drivers which you can try to activate with either the modprobe or the insmod command.

[emu10k1]("http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1") should work, despite that your specific model ain't listed in there.

Try
```
sudo modprobe emu10k1
```

The easiest way is just to use alsaconf which I mentioned earlier.

---

### Post by Cleveland Rock on 2009-08-16
```
clevelandrock@ubuntu:~$ sudo alsaconf
sudo: alsaconf: command not found
clevelandrock@ubuntu:~$ 
```
Now we're getting somewhere, but I don't know how to install it.

---

### Post by khelben1979 on 2009-08-16
[Alsa Upgrade Script]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+script").

For myself I have always downloaded all the source packages [from the Alsa homepage]("http://www.alsa-project.org/main/index.php/Main_Page"), configured them up and installed them in the system, then I have used the script above and the sound was working after this. I have done this with both Ubuntu Hardy and Intrepid.

You can try to follow the instructions and if that don't work, you can do it my way first:

Download the 8 archives which you see in the upper right corner from the Alsa homepage. Unpack them in a folder on your harddisk. In the file path you do this:

sudo ./configure
sudo make
sudo make install

for each file archive and then go back to the Ubuntu upgrade script.

---

### Post by Cleveland Rock on 2009-08-16
Sorry, but I don't know what to do with *any* of the information in the last post. This is just day 2 with Linux for me, so give me a break! All I want is sound...

Edit: Also, I'm starting to have trouble just getting pages to load. and sometimes they won't even load at all. None of this makes sense; I didn't do anything to it! Things aren't looking so good for Ubuntu, but I'm still going to do everything I can to keep from going back to Windows.

---

### Post by khelben1979 on 2009-08-16
> **Cleveland Rock said:**
> Sorry, but I don't know what to do with *any* of the information in the last post. This is just day 2 with Linux for me, so give me a break! All I want is sound...

Okay... you can try this instead, after you've made a paus, I guess:

1. Open up [the Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager") and search for alsa.
2. Install the alsa packages that you find.
3. Reboot the computer.
4. Start the alsamixergui application and post a screen dump, as you did before, and let us see if you've got more volume meters this time.

Was that okay? (I'm going to sleep now)

---

### Post by Cleveland Rock on 2009-08-16
I did what you said, but alsaconf still doesn't work and the alsa mixer looks exactly the same as the last time I posted a screen dump.

Come on, guys, we can do this!

---

### Post by Cleveland Rock on 2009-08-16
Sorry for the bump, but I really need help.

Bump!

---

### Post by kostkon on 2009-08-16
I think it is a matter of PulseAudio using your Intel card as the default instead of your Audigy. That's why you are hearing sound only in the login screen (where ALSA is used directly without the sound passing through PulseAudio. PulseAudio runs only in the user's session, not system-wide).

Thus, install the *PulseAudio Device Chooser* utility using *Synaptic* to set your Audigy as the default.

More info [here]("http://ubuntuforums.org/showthread.php?t=1130384").

---

