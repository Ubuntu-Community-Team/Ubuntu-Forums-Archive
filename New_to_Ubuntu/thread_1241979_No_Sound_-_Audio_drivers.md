---
title: "No Sound - Audio drivers ?"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by D_frag on 2009-08-16
Hi all 

I have an HP 6730b and i just installed Ubuntu 9.04 and i am not getting any sounds i have tried to listen to online radios or even youtube .. I would really appreciate it if someone can point me to a thread or a solution if anyone encountered something similar 

When i do lspci this is the audio device :

Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller

The driver for XP is the ADI SoundMAX 1984A


cheers

---

### Post by jbrown96 on 2009-08-16
In a terminal try ```
alsamixer
``` One of your primary channels is probably muted (master, PCM, front, speaker, headphone) use the arrows to navigate and turn them up and m to unmute. Esc to exit

---

### Post by D_frag on 2009-08-17
I have tried alsamixer and unmuted all channels but i found that still i cannot hear any sounds .. any other ideas ??

---

### Post by Kezz Kezz on 2009-08-17
I'm having the same issue, I think my audio is this:

02:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)

All the sound options are on and turned up , I've tried a few different tutorials for installing drivers but it's not having any so far. I've pretty much resigned myself to buying a new sound card later down the line.

---

### Post by Malta paul on 2009-08-17
You could try going to System>Preferences>sound then try the options and 'test' till you get a sound.

Also go to Applications>sound & video>volume control and set to 'Alsa mixer'  then adjust PCM

[Is your BIOS is set for audio?] 

Have fun :)

---

### Post by kambrik on 2009-08-17
I had the same problem.. You do use alsamixer and you disable or mute the very last option in the list (i forget what its named).

---

### Post by Sir Jasper on 2009-08-17
Hi jbrown96,

Just to say I liked your contribution and found your ¨m¨ option very helpful.

My regards

---

### Post by SSovine on 2009-08-17
When I run lspci, I get both these among the results:

[I]00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

02:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X[/I]

I tried the method for selecting options in System>Preferences>Sound and using test.  The only driver I was able to get sound using was the following:

*Dell Sound Blaster Live! EMU10K1X Front (OSS)*

I was able to get sound, but the sound was extremely distorted on the test sound, and when playing an .mp3 file in the sound player.  

If anyone knows what to do in this situation, advice would be greatly appreciated!

Also, my Sound Blaster Live! sound card is not a 5.1 card, it is only a stereo card.

---

### Post by SSovine on 2009-08-18
I found this guide to setting up Pulseaudio in Jaunty:

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

I followed the instructions and now sound is working great!

---

### Post by D_frag on 2009-08-18
I still can't use my sound ! I have tried the muting the last channel in the alsamixer and i tried testing using the system > preferences > sound and i still cant get it to work ! 

Has anyone had similar problems and is using an HP6730b ... I cant use an OS without sound !!

---

### Post by bagle on 2009-08-18
maby your sound card just bloke or somthing. try ssslovaks  post that has a link to a possible fix.:twisted::twisted::twisted::shock:

---

### Post by kambrik on 2009-08-22
Two things; verify that you have the speakers plugged into the correct port (usually green), and also mute/disable using the alsamixer the "External" option.

---

### Post by mgmiller on 2009-08-22
I recently had the same problem setting up 2 computers for others that both had the same configuration as yours.  The manufacturer used a mobo that had integrated sound, but used a pci card soundblaster as an "upgrade".  It's not obvious because they block the extra sound ports on the back so you only see one set.

The solution is to go into the BIOS and disable the onboard sound card.

The soundblaster will remain as the only sound card in the system.

When I did this, the sound started up with the next boot without any other  tweaking.

---

### Post by ratss on 2009-08-22
I've been trough this bfore.. 
I just smply backup my .deb and any imprtant files with APToncd, then reinstall ubuntu with clearly format in 1 drive... in the end everything works perfectly in only 2 hrs and require 2 blank cd's:popcorn:

---

### Post by piyushverma82 on 2009-08-22
I had the same problem with my laptop, it is a problem about something like external amplifier , search for a check box about ext. amp in sound prefence and uncheck it.

---

### Post by SSovine on 2009-08-23
I was never able to get any sound using ALSA alone, but using Pulseaudio, I am getting sound on nearly everything.  The exception there is that I can't get my sound card configured with JACK, using the DAW Ardour.  Using the link I posted above you should be able to get Pulseaudio working.

---

### Post by mgmiller on 2009-08-23
I'm not talking about a laptop.  I am referring to a machine where lspci will give a result like this:
> When I run lspci, I get both these among the results:

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

02:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X

These machines have an audio chipset built into the mobo that the manufacturer has chosen to not use.  They have added a sound card to a pci slot and use that.  In windows, if you don't add the driver for the built in sound, there are no conflicts because it won't work without the driver, but in Linux, both drivers get added and both cards try to run at the same time resulting in all kinds of inconsistent sound errors.

The best solution is to disable the on board sound card in BIOS if it's output jacks are not available on the back of the case.  If they are, you can choose which sound card to use.  Leave it enabled and remove the one from the pci slot, or disable the onboard and use the add on card.

Which ever solution you choose, to avoid problems with pulse audio, you should try to run with only 1 sound card in the machine.

It may be possible to get both cards working by doing a lot of tweaking to pulse audios config. but it's not worth the trouble.

---

### Post by sherif.mousa on 2009-08-30
Hi D_frag,

I also have HP 6730b, and i also faced the same problem but now, the sound card is working.
Just try to add this line:

options snd-hda-intel model=mobil

to the file:

/etc/modprobe.d/alsa-base.conf

It worked for me . . . 
Good Luck
__

---

