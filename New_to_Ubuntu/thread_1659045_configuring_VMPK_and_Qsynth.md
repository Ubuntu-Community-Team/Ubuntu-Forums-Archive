---
title: "configuring VMPK and Qsynth"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by virtdave@mcn.org on 2011-01-03
I installed VMPK (Virtual MIDI Piano Keyboard), and am trying to play notes from it thru my USB earphones--the earphones are working (at least, with Skype).  When I click on a piano key in VMPK, the small green pilot light at the lower left corner in Qsynth flashes, but there's no sound via the earphones.  Any hints?

---

### Post by cchhrriiss121212 on 2011-01-04
Qsynth requires a soundfont in order to make sounds, there are plenty free ones out there on google. Anything in .sf2 format will work.
If you already have loaded a soundfont, please post what settings you are using.

---

### Post by virtdave@mcn.org on 2011-01-08
In Qsynth: 
MIDI tab: Enable MIDI Input box checked
              ALSA Sequencer Client ID: Qsynth1
Audio tab: Audio driver: alsa
Soundfonts tab: SFID 1; Name /usr/share/sounds/sf2/FluidR3_GM.sf2; Offset 0

In VMPK: -->Edit -->Connections: "Enable Thru on MIDI Output" checked
Input MIDI Connection <blank>
Output MIDI Connection FLUID Synth (Qsynth1):0

---

### Post by cchhrriiss121212 on 2011-01-09
I usually use qsynth with jack, but I have just had success with these settings using ALSA only:

VMPK:
In Connections unchecked both boxes, fluid synth as output

Qsynth:
In setup>MIDI, use alsa_seq driver, client ID:pid

Use channels to select the soundfont, some only have a limited range of a few notes.

---

### Post by virtdave@mcn.org on 2011-01-09
Tried what you suggest, but still no sound via headphones.  Perhaps if I use jack? What settings should I try with jack, perhaps that will do it.....

---

### Post by cchhrriiss121212 on 2011-01-09
I don't think jack will help as it can only use one sound device at a time, and I think your USB phones will count as a separate device. Could you post the result of aplay -l from a terminal?

---

### Post by virtdave@mcn.org on 2011-01-09
card 0: ICH7 [Intel ICH7], device 0: Intel ICH [Intel ICH7]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH7 [Intel ICH7], device 4: Intel ICH - IEC958 [Intel ICH7 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by cchhrriiss121212 on 2011-01-09
Under qsynth setup>audio, try typing in hw:1 as the audio device.

---

### Post by virtdave@mcn.org on 2011-01-09
Thanks for your patience.....here's what I get:

p, li { white-space: pre-wrap; } Qsynth1: Failed to create the audio driver (alsa).
 
 Cannot continue without it.


and in the Qsynth log:



p, li { white-space: pre-wrap; } [COLOR=#FF0000]13:59:23.289 Qsynth1: Failed to create the audio driver (alsa). Cannot continue without it.[/COLOR]
 fluidsynth: warning: Failed to pin the sample data to RAM; swapping is possible.
 fluidsynth: error: The "hw:1" audio device is used by another application

---

### Post by cchhrriiss121212 on 2011-01-09
> fluidsynth: error: The "hw:1" audio device is used by another application
Did you have anything else open when trying this out? Shut down anything using sound.

If this still doesn't work try using hw:1,1 instead of hw:1.

---

### Post by virtdave@mcn.org on 2011-01-09
Rats.  the hw:1,1 doesn't work either.  As far as I can determine, the only device using sound is the USB headphone/microphone I use for Skype, and even with Skype not running I can't get any sound out of VMPK/Qsynth.  As I noted in my first post, I do get a flash of the pilot light in the lower left corner of the Qsynth window when I hit a key on VMPK, but no sound.......the mystery persists.

---

### Post by cchhrriiss121212 on 2011-01-10
So even when not running any other program, qsynth will tell you that hw:1 is in use?

---

### Post by virtdave@mcn.org on 2011-01-10
so it seems--the only other program using sound I've got installed (that I know of) is Skype, and even when I completely close Skype, I get the warning that hw:1 is used by another program.  In fact, if I look at System-->Preferences-->Sound, in the Applications tab, I'm informed that "No application is currently playing or recording audio".
 I bet there's a way of finding out what program Qsynth thinks is using hw:1 might be--any idea of how to determine this?
Of course, I've got Firefox running (so I can use this forum), and Open Office is running, but could they be the culprits?

---

### Post by cchhrriiss121212 on 2011-01-10
It is best to close everything you can, skype also may be running in the background somewhere. Check system monitor on the processes tab to find out, I am not sure as I have only ever used it on Windows.

---

### Post by virtdave@mcn.org on 2011-01-10
In System-->Administration-->System Monitor, under the Processes tab, everything is 'sleeping', and skype does not appear there (I turned it off, to see if that helped, and as I note above, it does not....phooey).
I assume there's some program or other which has 'reserved' hw:1 and thus blocked it as far as Qsynth goes, but I've no clue how to find out which program that might be....

---

### Post by cchhrriiss121212 on 2011-01-11
It should not be possible for anything to reserve a device like this. Try setting the headset as primary output under the system>sound menu, then starting qsynth without the hw:1 argument.

---

### Post by virtdave@mcn.org on 2011-01-11
Major breakthrough.....I had not selected, in Qsynth, a channel (thought one was selected by default) :redface: and having done so, VMPK/Qsynth now plays thru the headphones!!.  The sound is remarkably tinny and scratchy, but it beats dead silence...
Thanks again for your help and patience....if you do know a way to improve the quality of the sound (it may be the best one can hope for on relatively cheapo earphones, but it's better when I use Skype), I'd be interested, but really you've done a lot for me....

---

### Post by cchhrriiss121212 on 2011-01-11
Sound quality is limited by the weakest link in the audio chain, which may or may not be the headphones. It might depend on the soundfont you are using. To test this, try it out through your speakers and then through the phones, then compare.

---

### Post by virtdave@mcn.org on 2011-01-11
Yeah, the sound is crackly on the speakers too--I've loaded soundfounts
FluidR3_GS and Fluid R3_GM.  Can't notice a difference between them.  Any suggestions for a niftier soundfont?
(edited as below):
Weird--I added another soundfont (musecore-soundfont-gm) using Synaptic Package manager, and although Qsynth is still using FluidR3_GM, the sound is now very good....I think this case is closed, thanks for your help.

---

### Post by cchhrriiss121212 on 2011-01-11
If you want more soundfonts there are some good recommendations here:
[http://ubuntuforums.org/showpost.php?p=9341430&postcount=61](http://ubuntuforums.org/showpost.php?p=9341430&postcount=61)
Have fun!

---

### Post by avacado on 2011-03-19
Thanks guys - SOLVED
Setting a channel in Qsynth worked for me too.
Double click channel in Qsynth, choose one at random, 
make sure VKMP on the same channel, Sweet.

---

### Post by doogiekd on 2012-10-17
thanks virtdave, 
that was all i needed to get it working!

---

