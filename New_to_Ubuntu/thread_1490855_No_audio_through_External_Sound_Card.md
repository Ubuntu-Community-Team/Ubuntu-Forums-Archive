---
title: "No audio through External Sound Card"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by SPARTAN-118 on 2010-05-22
Wow, it's been a long time since I've been here, and a long time since I've played with the *buntu family. But now let's get down to business:

Ubuntu cannot detect my sound card through PulseAudio. Poor choice of sound engine, really, but that's not the point.

Kubuntu, on the other hand, *did* detect my SC, but KDE is too slow on my PC, so now I've gone with Xubuntu.

Xubuntu *appears* to have detected my sound card in the mixer applet, but I can't get any sound through it. I wish there was a "test" button in the mixer itself, but right now I've been using Exaile to test it out.
I am using an external sound card because I have an old laptop, and currently have no way of building the sweet desktop I want to that has excellent on-board audio. :(
So now I'm stuck with the question: how can I set Xubuntu to use ```
matthew@matthew-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdc440000 irq 22
 [B]1 [default        ]: USB-Audio - USB Sound Device        
                      USB Sound Device         at usb-0000:00:1d.0-2, full speed[/B]
```as my default sound card?

Thanks in advance,
Matt.

**EDIT**: Oh, almost forgot: when I unplug the sound card and plug it back  in, my speakers (Logitech X-540s), which are on, make a sound (you know,  the sound when you plug in headphones to an iPod that's already on?).  Not sure if this matters, but I think it means that the system *is*  using them; I just can't get any Applets to do the same.

PS I'll give any other information needed, just tell me! :)

---

### Post by cariboo on 2010-05-23
Install padevchooser, it is in the repositories, it should allow you to select your device.

---

### Post by SPARTAN-118 on 2010-05-23
Oh, hey, Cariboo. 

Sorry to say this, but when I read this, I was utterly disappointed. Not to sound rude, but if Ubuntu, which uses PulseAudio and this particular package, couldn't select my soundcard, what makes you think Xubuntu using it would be any different? That's probably the very first thing I tried.
I *do* know how to use the Search function, you know. ;)

Anyways, what else would you suggest? Do you have much experience with the Xfce desktop environment? I could provide screenshots of my settings, and the output of certain commands in the Terminal, if it'd help.

---

### Post by SPARTAN-118 on 2010-05-27
I just tried installing Debian 5, but it couldn't even connect to the net, and the folder setup was weird (only Desktop in /home/[username]?). So I switched back to Xubuntu, but now I can say with absolute certianity that it's the distro's sound architechture (maybe ALSA, maybe PulseAudio).

In Debian audio worked fine. I could even play a test sound! (Something that BADLY needs to be implemented in ALL Linux OSes.)

Sound also works in the KDE desktop, as mentioned earlier, so it is definitely Xfce's sound setup, despite the fact that in the volume mixer it says "USB Audio   (ALSA mixer)". 

I realize most people have an internal sound card, and aren't as impatient and as foolish as me (bought a laptop w/printer and warranty combo for total of $800 (!), when I could have bought a *much* better desktop PC.)

---

### Post by SPARTAN-118 on 2010-05-27
I just tried installing Debian 5, but it couldn't even connect to the net, and the folder setup was weird (only Desktop in /home/[username]?). So I switched back to Xubuntu, but now I can say with absolute certianity that it's the distro's sound architecture (maybe ALSA, maybe PulseAudio).

In Debian audio worked fine. I could even play a test sound! (Something that BADLY needs to be implemented in ALL Linux OSes.)

Sound also works in the KDE desktop, as mentioned earlier, so it is definitely Xfce's sound setup, despite the fact that in the volume mixer it says "USB Audio   (ALSA mixer)". 

I realize most people have an internal sound card, and aren't as impatient and as foolish as me (bought a laptop w/printer and warranty combo for total of $800 (!), when I could have bought a *much* better desktop PC.) But could somebody *please* help me out?

---

