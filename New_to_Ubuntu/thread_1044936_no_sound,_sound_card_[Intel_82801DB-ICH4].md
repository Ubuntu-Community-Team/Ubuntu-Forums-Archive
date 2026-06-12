---
title: "no sound, sound card [Intel 82801DB-ICH4]"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by eoeo on 2009-01-19
So I just installed Ubuntu 8.10 on my laptop about 1 week ago, and everything is working automatically except for the sound which is totally absent.  I saw this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302411"), which seems to apply to my laptop model, sound card (Intel 82801DB-ICH4), and sound module (snd-intel8x0).   is there something else I can try besides wait for this bug to be updated.  Here's what I tried so far

________________
First
I check permissions.  Under System>Administration>Users and Groups, I checked "Use audio device" under User Priviledges for eo and root

I verified that I was a member of the audio group:
```
grep 'audio' /etc/group
```

I got the feedback:
audio:x:29:pulse,eo,root

It appeared I was a member of the audio group but correct me if I am wrong.

____________________________
Second
I used alsamixer at the terminal to adjust the volume, and make sure that mute is off.  Alsamixer was only showing one or two bars to adjust, unlike other screen shots which show 5-6 bars. 

**no sound**

________________
Third
people on the forums said it was important in alsamixer to turn off "external amplifier", as well as "headphone jack sense" and "line jack sense", but for some reason I couldn't do that in alsamixer.  I clicked on the volume icon in the upper right corner of the screen, opened Volume Control, and went to Preferences.  That way I was able to check "headphone jack sense" and "line jack sense" and "external amplifier", and then make sure those were unchecked under the "Switches" tab.   

___________________________
Fourth

```
aplay /usr/share/sounds/alsa/Front_Center.wav
```

I got the feedback:
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

but no sound

____________________________________
Fifth
I checked sound device assignment, saw that my soundcard was assigned to card 0 

```
cat /proc/asound/cards
```

I got the feedback:
0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at irq 9

Should I do something else at this step?

__________________________________________
Sixth
The system is recognizing my sound card

```
aplay -l
```

I got the feedback:
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

________________________________________
Seventh

Find the sound module.
My sound module (snd-intel8x0) is installed.

```
lspci -v 
```

I got the feedback:
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Sony Corporation Device 81c0
	Flags: bus master, medium devsel, latency 0, IRQ 9
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
	Memory at e0100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0


__________________
Eighth
I manually started the sound module.

```
sudo modprobe snd-intel8x0
```

There was no feedback or error after issuing that command at the terminal
still no sound

___________________
Ninth
Look for conflicting sound modules.

```
lsmod | grep pcsp
```

I got the feedback:
pcspkr 		10624  0

Forums suggested to blacklist certain modules that could be interfering with the main sound card.  I didn't see too many modules listed here, so I decided not to blacklist anything.

________________
Tenth

I read on the [comprehensive sound guide]("http://ubuntuforums.org/showthread.php?t=205449"), that "Basically, if you have an intel8x0 module, you can get AC'97 working by the code:

```
sudo nano /etc/modprobe.d/alsa-base
``` 

and adding this as the last line: "options snd-intel8x0 ac97_quirk=3"

well I tried that but no banana
__________________________


By the way my computer is a Sony Vaio, model PCG-4E1L

is anyone else having this problem?

---

### Post by spiderbatdad on 2009-01-19
judging from the confirmations in your post...perhaps a mute button or keyboard volume controls are down...lol. sorry. clueless on this.
Perhaps test the various sound devices in sytem>>preferences>>sound.

---

### Post by eoeo on 2009-01-20
i have sound now!

sorry for crowding up the forums with my noob talk!  

there was a "Sound Effect" button at the bottom right corner of my Sony Vaio model PCG-4E1L, those pretty lights were confusing me, orange light means mute, no light means sound

---

### Post by mgalle on 2009-08-28
No noob talk... your post helped me a lot (option 10 for me): maybe I would have found it elsewhere, but this was quite fast.
thanks

---

### Post by call4david on 2010-02-15
For my Sony Vaio I got it to work by:

1.  Install PulseAudio Software from the Ubuntu Software Center
2. Going to Applications -> Sound & Video and selecting PulseAudio Volume Control
3. Select the Configuration Tab
4. Set Internal Audio Profile: Analog Surround 4.0 Output + Analog Stereo Input

I also have the PulseAudio Applet and Sound Icon on my task bar.

Dave:popcorn:

---

