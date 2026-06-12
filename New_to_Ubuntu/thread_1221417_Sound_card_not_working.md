---
title: "Sound card not working"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by gshockxc on 2009-07-23
There's got to be a way to figure this out.  I have been using my Jaunty right along with no issues.  Everything was working great.  Around Sunday or Monday this week, I installed some updates.  I don't know what they were, and it never gives a description anyway.  It's the update notifier that runs in the panel.

Anyway, sound just doesn't work anymore.  I have no idea how to troubleshoot, or if I can just reinstall the sound drivers.  Can anyone help?

Thanks.

---

### Post by jbrown96 on 2009-07-24
Try ```
alsamixer
``` in a terminal. Maybe you are lucky enough to just have a channel muted or turned down all the way. Pay attention to channels such as master, pcm, front, and headphone. 

If that doesn't work, try the multimedia configuration in System Settings. You should be able to choose some type of analog output and if you hover over it, it should say the output modes it will choose. You want one that will try alsa. Save and then restart. 

Another problem that I had on Fedora recently was a muted channel. Alsamixer didn't report it, but kmix had muted it. In your system tray open up the mixer. There should be a few volume sliders; my headphone channel was muted, but wasn't listed -- I had to add the channel, then I saw that it was muted. 

If that still doesn't work, post the output of ```
lspci | grep Audio
``` so we know what your hardware is.

---

### Post by gshockxc on 2009-07-24
> **jbrown96 said:**
> Try ```
alsamixer
``` in a terminal. 

I hadn't tried the Alsamixer in the terminal window before.  But it showed that everything was turned on, and not muted.

My first attempt to fix this problem led me to the Multimedia settings in System Settings.  In the Device Preference tab, I have three output devices listed: 
[LIST=1]
[*]Audigy SE [SB0570](CA0106)
[*]CA01016, CA0106 (Side Speakers)
[*]PulseAudio
[/LIST]

If I check the box for "Show dvanced devices", then I get variants of the same ones I already listed

[LIST=1]
[*]Audigy SE [SB0570](CA0106)
[*]CA01016, CA0106 (Side Speakers)
[*]PulseAudio
[*]Audigy SE [SB0570](CA0106)#1
[*]Audigy SE [SB0570](CA0106)#2
[*]Audigy SE [SB0570](CA0106)#3
[*]CA01016, CA0106 (Center and Subwoofer speakers)
[*]CA01016, CA0106 (Rear speakers)
[*]PulseAudio  /home/gshockxc/.pulse/4f45fac5b5fdc8025c4611a649ddb110:runtime/nativealsa_output.pci_1102_7_sound_card_0_alsa_playback_0
[/LIST]

So that's the interesting stuff that I found on my own before posting.  Your code didn't work for me, but I did get the output  of 
```
 
lspci -nn| grep audio

```

Result: 
```

05:06.0 Multimedia audio controller [0401]: Creative Labs CA0106 Soundblaster [1102:0007]

```

I think the sound card somehow got turned off in one of the update installs that I did.  But I don't know how to get to the code to turn it back on.  

Based on the last output device listed in the Multimedia settings
...pci_1102_7_sound_card_0_alsa_playback_0
This tells me that the sound card is turned off, and it's not using ALSA for playback.  Those values should both be "1" shouldn't they?

Thanks for your help.

---

### Post by gshockxc on 2009-07-24
> **gshockxc said:**
> 

I think the sound card somehow got turned off in one of the update installs that I did.  But I don't know how to get to the code to turn it back on.  



Here's something.  I found this in the Synaptic History,

Commit Log for Mon Jul 20 17:14:07 2009


Installed the following packages:
gstreamer0.10-pulseaudio (0.10.14-1ubuntu0.1)
libpulse-browse0 (1:0.9.14-0ubuntu20.2)
libpulsecore9 (1:0.9.14-0ubuntu20.2)
libspeexdsp1 (1.2~rc1-1)
pulseaudio (1:0.9.14-0ubuntu20.2)
pulseaudio-esound-compat (1:0.9.14-0ubuntu20.2)
pulseaudio-module-hal (1:0.9.14-0ubuntu20.2)
pulseaudio-module-x11 (1:0.9.14-0ubuntu20.2)
pulseaudio-utils (1:0.9.14-0ubuntu20.2)

There were no updates for almost two weeks prior to this, and it was right after this update that my sound stopped working.

Should I remove all of the Pulseaudio packages?  I think it's interfering with ALSA.

---

### Post by wizard10000 on 2009-07-24
I had this problem also.  Before you start digging around with sound I strongly suggest you check out policykit and make sure you still have rights to access your soundcard.

Had problems on my shiny new Core i7 machine with two different soundcards.  Installed 64-bit Jaunty three times and each time when I ran upgrades I lost sound.  aplay -l would say "no soundcards detected".  I also lost my TV tuner card and the ability to shutdown, hibernate or reboot the system from within X.

Anyway, I found that although policykit said I had access to the soundcard and so on, I didn't - permissions looked like this:

Anyone: No
Console: No
Active Console: Yes

Okay, you'd think I'd be able to use the soundcard but it didn't work. Had to set 'console' to yes to get the hardware working again.

I added this to existing bug #370982.

Hope it works for you -

---

### Post by gshockxc on 2009-07-24
Sweet.  Thanks for the info.  That helps a lot.  I wasn't about you reinstall, but I was tempted.  I knew that it had to be tied to the updates somehow.  My sound card is pretty old (circa 2001).

I'll look into this later today.

---

### Post by gshockxc on 2009-07-26
> **wizard10000 said:**
>  aplay -l would say "no soundcards detected".  

I tried 
```

aplay -l 

```
in a terminal windown, and here's the result:

```

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
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

```

Seems like everything is set up OK.  How to I check the permissions on Policykit?

Thanks.

---

### Post by gshockxc on 2009-07-29
Still having issues with sound.  I don't know how to look into the details of what's causing this.  How do I check Policykit?  I can't seem to find it.  How can I take screenshots so I can show what's going on?  I've checked all the mute buttons, and everything is unchecked.

Any help would really be appreciated.  This is getting pretty frustrating because I'd really like to be able to play my music and videos.

Thanks.

---

### Post by wizard10000 on 2009-07-30
> **gshockxc said:**
> Still having issues with sound.  I don't know how to look into the details of what's causing this.  How do I check Policykit?  I can't seem to find it.  How can I take screenshots so I can show what's going on?  I've checked all the mute buttons, and everything is unchecked.

Any help would really be appreciated.  This is getting pretty frustrating because I'd really like to be able to play my music and videos.

Thanks.

If aplay is showing a sound card when logged on as a normal user the problem most likely isn't policykit.  Sorry -

---

