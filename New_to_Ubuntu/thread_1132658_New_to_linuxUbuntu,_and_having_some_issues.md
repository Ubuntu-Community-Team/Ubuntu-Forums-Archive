---
title: "New to linux/Ubuntu, and having some issues"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by Speedwagon on 2009-04-22
Over the years, I've toyed with other OSes, and inevitably end up back at Windows.  Never really been a big fan of Windows, but nothing else has ever been quite so convenient.  So I'm trying to like Ubuntu now, but I have a few problems.

First, I did get the OS installed fine.  But I run a Soundblaster X-Fi card, and Ubuntu/linux doesn't seem to like it at all.  And if I can't get sound, I'm not going to use the OS.  So I either need drivers that work(searching hasn't revealed anything promising), or a sound card that will work fine with linux.

Second, I rather like my Logitech mouse buttons, especially the 'back' button I use for surfing the web.  How do I make these buttons work in Ubuntu?

Other than that, seems to be fine.  Though I haven't tried much in the OS, due to lack of sound.

---

### Post by Peter09 on 2009-04-22
in a terminal type
```
lshw -C sound
```

and post the output.

Also check that sound is set up ok by right clicking on the speaker icon in the top panel and select open volume control

---

### Post by billgoldberg on 2009-04-22
People claim this worked for them:

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Try it out.

Here is a list of cards that work well with ALSA:

[http://alsa.opensrc.org/index.php/Alsa_Preferred_Soundcards](http://alsa.opensrc.org/index.php/Alsa_Preferred_Soundcards)

Ubuntu now uses PulseAudio but Alsa is still available.

---

### Post by Speedwagon on 2009-04-22
> **Peter09 said:**
> in a terminal type
```
lshw -C sound
```

and post the output.

Also check that sound is set up ok by right clicking on the speaker icon in the top panel and select open volume control

The volume control has the red 'no' symbol on it, and tells me no plugins/devices found when I try to open it.

> WARNING: you should run this program as super-user.
  *-multimedia UNCLAIMED  
       description: Audio device
       product: Creative Labs
       vendor: Creative Labs
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0



> **billgoldberg said:**
> People claim this worked for them:

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Try it out.

Here is a list of cards that work well with ALSA:

[http://alsa.opensrc.org/index.php/Alsa_Preferred_Soundcards](http://alsa.opensrc.org/index.php/Alsa_Preferred_Soundcards)

Ubuntu now uses PulseAudio but Alsa is still available.

I'll have to take a look at that right now.

---

### Post by kpkeerthi on 2009-04-22
Pulseaudio just channels the sound to ALSA. If your card is supported by ALSA, it should work in Ubuntu/Pulseaudio setup. Otherwise, you have to try the opensound (OSS) option.

---

### Post by kpkeerthi on 2009-04-22
X-Fi is not supported by ALSA according to 
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

---

### Post by Lunx on 2009-04-22
> **Speedwagon said:**
> 

Second, I rather like my Logitech mouse buttons, especially the 'back' button I use for surfing the web.  How do I make these buttons work in Ubuntu?



Cordless mouse? If so it seems odd that it doesn't just work, mine worked normally from day one, no configuration needed. The cordless keyboard was a bit different though, stuffed up on me when I was running XP and couldn't ever get it to connect, tried it again in Ubuntu and no joy there either but guessing it's probably something I'm doing wrong when trying to reset it.

---

### Post by Speedwagon on 2009-04-22
> **Lunx said:**
> Cordless mouse? If so it seems odd that it doesn't just work, mine worked normally from day one, no configuration needed. The cordless keyboard was a bit different though, stuffed up on me when I was running XP and couldn't ever get it to connect, tried it again in Ubuntu and no joy there either but guessing it's probably something I'm doing wrong when trying to reset it.

No, it's a corded G5.  And my side button doesn't work, which makes me annoyed at it.

Also, I tried enabling the onboard audio(on the M/B), and that seems to work just fine.  So I guess I could sell this X-Fi, and buy something that would be better between linux and windows.

Having another issue though that I forgot about.  I have a D-link wireless card, and I get HORRIBLE connection with it in Ubuntu.  It connects, but says the speed is 1 Mb/s, and frequently just plain stops when using the internet.  Just hooked up a cable to the router, and now everything is fast as can be at 100 Mb/s with no issues.  I'm assuming I need to update a driver for the card to get it to work properly? 

edit: Apparently I am not alone in my network issue:  [http://ubuntuforums.org/showthread.php?t=1126449&highlight=dwa-552](http://ubuntuforums.org/showthread.php?t=1126449&highlight=dwa-552)

---

