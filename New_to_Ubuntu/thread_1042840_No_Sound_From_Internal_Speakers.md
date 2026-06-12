---
title: "No Sound From Internal Speakers"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by zanknits on 2009-01-18
Hi all! 

I'm sorry to dredge this topic up, since I know it's been talked about before, but I've been searching Google for hours and I haven't had any luck yet.

I installed Ubuntu on my brand-new, fresh out of the box HP Pavilion dv4-1225dx laptop today. I ran Windows first to make sure everything worked (including the internal speakers), but I didn't partition my computer when I switched to Ubuntu - I just took Microsoft completely off. 

Anyway, I can't get sound to play out of my internal speakers. My headphone jack works fine, though. I tried to follow the troubleshooting guide ([https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)) but I got lost at the "is your sound card supported?" part. I couldn't find my soundcard on the list, but then again I'm not sure what I'm looking for.

Here's what the computer said my soundcard was when I did the lspci thing:
> 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: Hewlett-Packard Company Unknown device 30fb
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at d2500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

Then the troubleshoot guide started talking about manually installing the drivers, but I don't know how to find out what the driver is. I think my sound card has to be supported - after all, I do get sound out of the headphones - but I really am not very familiar enough with the inner workings of computers to know what's really going on.

(ps - the sound doesn't work for anything from the internal speakers - no startup sounds, no beeps, no music)

Thank you so much for helping me out! I know this is such a newbie problem, but I really do appreciate your time!

---

### Post by linux_tech on 2009-01-18
Please post output of:
```
cat /proc/asound/card0/codec#* | grep Codec
```
```
aplay -l
```

---

### Post by zanknits on 2009-01-18
For cat /proc/asound/card0/codec#* | grep Codec
> Codec: IDT 92HD71B7X
Codec: Generic 11c1 ID 1040


And aplay -l
> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by concerto on 2009-01-28
This is a stupid question but did anyone report this problem to the 
HP Linux forum?  I looked but didn't see anything about this.


HP Resource Center Forums
[http://forums11.itrc.hp.com/service/forums/home.do?admit=109447626+1233127655264+28353475](http://forums11.itrc.hp.com/service/forums/home.do?admit=109447626+1233127655264+28353475)


I'm installing Linux now on my HP DV4-1155se so it looks like i'm about to have the same problem.  :(

---

### Post by zanknits on 2009-01-31
Update:

I've upgraded to Intrepid, but I'm still not having any luck with getting sound from the internal speakers. 

This is the report from aplay -l:
> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


And from lspci:
> 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at d2500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
	Subsystem: ATI Technologies Inc RS780 Azalia controller
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d2410000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


Of course now that I've switched to Intrepid, every once in a while in order to get sound from my headphones I have to 'killall pulseaudio', then go into the sound preferences and switch everything to 'HDA ATI SB STAC92xx Analog'.

If anyone has any suggestions, I am desperate! I would even be willing to switch operating systems at this point if Debian or OpenSuse or something can just give me sound.

---

### Post by ryofire on 2009-02-03
> **zanknits said:**
> Hi all! 

I'm sorry to dredge this topic up, since I know it's been talked about before, but I've been searching Google for hours and I haven't had any luck yet.

I installed Ubuntu on my brand-new, fresh out of the box HP Pavilion dv4-1225dx laptop today. I ran Windows first to make sure everything worked (including the internal speakers), but I didn't partition my computer when I switched to Ubuntu - I just took Microsoft completely off. 

Anyway, I can't get sound to play out of my internal speakers. My headphone jack works fine, though. I tried to follow the troubleshooting guide ([https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)) but I got lost at the "is your sound card supported?" part. I couldn't find my soundcard on the list, but then again I'm not sure what I'm looking for.

Here's what the computer said my soundcard was when I did the lspci thing:


Then the troubleshoot guide started talking about manually installing the drivers, but I don't know how to find out what the driver is. I think my sound card has to be supported - after all, I do get sound out of the headphones - but I really am not very familiar enough with the inner workings of computers to know what's really going on.

(ps - the sound doesn't work for anything from the internal speakers - no startup sounds, no beeps, no music)

Thank you so much for helping me out! I know this is such a newbie problem, but I really do appreciate your time!

Same issue same laptop etc etc. So bump. Ive tried about 20 potential solutions today and none of them worked.

---

### Post by ryofire on 2009-02-09
[http://yourenotabowler.blogspot.com/2009/01/sound-warz.html](http://yourenotabowler.blogspot.com/2009/01/sound-warz.html)

solved. *yawn* thanks to the blog above.

add the line
> 
options snd-hda-intel model=dell-m4-1


to the file

/etc/modprobe.d/alsa-base


Now if only that suspend fix was still working for me :(

---

### Post by garretwp on 2009-02-10
Thank you very much. This has fixed the sound issues with the dv4-1225dx laptop!

- Garrett

---

### Post by mal2104 on 2009-02-13
Thanks for the help.  Does anyone else notice that after doing this the sound out of the speakers isn't as good as inside of vista?  I'm going to keep looking for a better solution.  If you do fix that suspend bug too, post it

---

### Post by ryofire on 2009-02-23
You could be right, but I don't use vista enough to notice. What I have noticed however is that the sound is unnoticeable at half volume, and seems quieter in Ubuntu even at full volume. 

Considering that I spent 1/2 a week looking for a fix though. I'm happy.

---

### Post by dim4iksh on 2010-11-13
same problem different laptop i have lg p1 jack laptop and my internal speakers doesn't work

---

### Post by squGEIm on 2011-10-10
I had the sam problem... This worked for me:

1. go to terminal
2. do this:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
3. add this to the end of the file:
```
options snd-hda-intel model=mbp3
```
4. Save and restart.

Hope it works.

---

