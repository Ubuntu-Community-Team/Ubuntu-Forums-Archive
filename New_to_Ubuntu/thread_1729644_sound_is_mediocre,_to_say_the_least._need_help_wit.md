---
title: "sound is mediocre, to say the least. need help with drivers and config."
date: 2011-04-15
forum: New to Ubuntu
---

### Post by Longshankss on 2011-04-15
Hi, I run ubuntu 10.10 and is generally very satisfied. Except I have this small problem with sound configuration, and it increasingly becoming more frustrating. I have a 3 year old dualcore (t9300) laptop, with a nvidia 8600m gt, and realtek soundcard. And a surround reciever hooked via the analog headphone jack.
Now, when i play h264 video files, the "fx" is very loud, and the dialouge is very low. So when watching an action-flick I have to sit and turn up the volume so I can hear the dialouge, and turn it down when action occurs. 
Is there some drivers I need to install?
Is there any equalizer software or procedure I can use?
Tried pulse, but I can't seem to wrap my head around where to begin and what not. I guess I can't figure out what to install.

I am a newbie in linux, and does not know jack about code and the tech, so I urge responders to kinda treat me as a Forrest Linux :) If I am to check some thing in the console, please write excactly what to do, as I dunno anything. 
I would also like to urge others with the same problem, not to interject with "me too", but instead read the answers and see if it helps you in any way, and if only a similar problem, to start their own thread, thank you.

---

### Post by d2btoo on 2011-04-15
Both vlc and [s]mplayer has equalizer. ;)

---

### Post by Longshankss on 2011-04-15
I am aware of that. I like to use xbmc, cause the quality of picture, sound and subs are just that much better. Admittedly sound-balance in sm/vlc is ever so slightly better, but still the problem remains, as the sound is not as rich as in xbmc. I also tried fidling with the equalizer on the reciever, but it does not help, nor does the equalizer in the players. :(
The difference between the "fx" and the "dialouge" is ridiculous.

---

### Post by madjr on 2011-04-15
hm, first lets diagnose the problem.

how is the sound without the surround receiver?

what about with headphones?

does it sound correctly or still sounds low on dialogues and loud on action scenes?

---

### Post by Longshankss on 2011-04-15
I should mention all 3 players is set to 5.1 channels. The receiver handles this fine, and sound is present on all 5 speakers. If I switch to stereo channels, the two rear channels mute (duh). And since I do not own 5.1 headphones, and in-pc speakers are stereo only, I would imagine it to be redundant... But I'll give it a go.
There. Tried your suggestions, but alas, no change. Even tried switching the to stereo, but no such luck there either. Readsomewhere about a fix, but it was all jiberish to me.

---

### Post by Longshankss on 2011-04-15
And now vlc's sound is all jerky and what not. Am not a happy camper....

---

### Post by Fraoch on 2011-04-15
First of all, the headphone jack is bad, bad, bad!  They have a small amplifier in line with the connection so you're amplifying sound that's already amplified.  That will sound pretty crappy no matter what you do and no matter what software is supplying it.  It's much better to use a "line out" if you have one - even better to use a digital out, but a laptop is unlikely to have one.  A "line out" connection is (more or less) unamplified and is supplying a signal at a voltage level that a receiver would expect, so it will sound a lot better.  A headphone connection will have lots of noise and distortion.  If you really do have to use it, turn the volume at the laptop down as much as possible and increase it at the receiver.

Secondly, what you're describing sound like a typical Dolby Digital/DTS decoder artifact.  How is the sound encoded in those files?  Dolby Digital or DTS?  Both these formats have special codes which give decoders data as to how to properly decode dialog versus effects, I believe it's called "dialog pre-emphasis".  If it's decoded "flat", i.e. evenly across the spectrum, the effects overwhelm the dialog as you're describing.

The problem is so common that many receivers *connected digitally* have controls to overcome this - controls for "dialog enhancement" or "night mode" that emphasize dialog at the expense of effects, decreasing the overall dynamic range in favour of a more even volume.

Connected via an analog connection though, these controls are usually not available.

There's a somewhat kludgy fix you can do that is available to all receivers - turn up the centre channel speaker.  Just give it +2 or +3 dB above the others.  This control is available in the setup routine of almost all receivers.

In software though, there's not much you can do.  Check to see if there's some sort of dialog pre-emphasis/"dialog enhance" or "night mode" setting for the decoding.  Generally only commercial Windows-only drivers that come with expensive soundcards have such controls.  Otherwise, look around for an equalizer.

---

### Post by Longshankss on 2011-04-15
I've tried the fiddle with the equalizer presets on the receiver, but that doesn't help. I have no digital output sources, only firewire, usb, headphone and line in(!). Turned down the volume on the PC, and up on the receiver = nothing. Isn't there a fix, an equalizer, software, SOMETHING? In my search on the forums, poor sound management is a very common problem for many. Not to be snotty, but how come no solution exists??? And what about the pulse? How is it different than alsa? If better, how(what) do I install, and configure?

---

### Post by madjr on 2011-04-15
> **Longshankss said:**
> Readsomewhere about a fix, but it was all jiberish to me.

do you have the link?

---

### Post by madjr on 2011-04-15
i wonder if this only happens with h264 video files.

have you tried converting or looking at other formats?

maybe you also want to try your sound system on another computer and see if it has the same problems (hooked via the analog headphone jack.)

i say this because i also have a 5.1 hooked to the pc and i havent really encountered this problem (yet).

but i do experience this constantly with some cable channels on some movies, so sometimes you just have to try to avoid the cause of the problem.

---

### Post by Longshankss on 2011-04-15
Well no. It is not only the h264 files, but also xvid with dolby 5.1, actually everything ac3/dolby 5.1. DTS plays without problems. I looked in the repo and found that i have "**libdca0**" installed, to handle DTS encoded files, so why is there not an equivalent dolby decoder? I do not wanna have to convert! Can't afford to buy a new computer! Apologize for the outburst, just frustrating, thats all. I mean, if "the masses" want better sound management, why hold back? As far as the link to the before mentioned fix, used to have it, but had to reinstall ubuntu :( Sorry

---

### Post by Longshankss on 2011-04-15
And what about **ardour**? Or the **system-wide Pulseaudio equalizer** ?
How do I use pulse? what do I install, and how du I configure it to run best?

---

### Post by madjr on 2011-04-15
after lots of reading and searching i came with these:

[http://www.avsforum.com/avs-vb/showthread.php?t=622358](http://www.avsforum.com/avs-vb/showthread.php?t=622358)


[http://ubuntuforums.org/showthread.php?t=818256](http://ubuntuforums.org/showthread.php?t=818256) (i suggest vote on the bug report too if you can)


[http://forum.xbmc.org/showthread.php?t=76640](http://forum.xbmc.org/showthread.php?t=76640)


going to bed now, hope that helps.

---

