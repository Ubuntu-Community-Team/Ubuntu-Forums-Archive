---
title: "Prevent Pulseaudio from starting"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2009-02-02
Recently I've noticed that when I have pulseaudio running, only one program can use my sound card at a time.  If I'm watching a video on youtube and try to open an mp3 with Totem, I won't get any sound from totem, or vise versa.

However, if I open the System Monitor and kill the pulseaudio process, all my programs can play sound simultaneously, with no adverse effects.

So I want to set it so that Pulseaudio will not start when I boot up my computer.

First I went to System > Preferences > Sessions and disabled it there.  That didn't work.

Then I used Boot Up Manager and disabled it there.  That didn't work either.

So how do I prevent this thing from starting?  Can I just uninstall it through Synaptic?

---

### Post by mgmiller on 2009-02-02
Go To System > Preferences > Sound and look on the Devices tab.  There will be drop downs for "Sound Events" "Music & Movies" and "Audio conferencing".  By default, these are all set to "Autodetect".  

What you need to do is click the drop down and select a different sound service from the list and then click test to see if it works.  The may be a large list of possibilities, try each one in turn till you find one that works well.  Sometimes, just clicking the "Alsa" choice is all you need.

When, you're done, just click close and the choices you made will persist between reboots till you change them to something else.

Good luck

---

### Post by sad_iq on 2009-02-02
I hope your soundcard has Hardware mixing if you're gonna try this, or else better stick to pulseaudio:
 [http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/)

That worked for me, however you should try to fix pulseaudio first:
[http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio](http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio)

---

### Post by kostkon on 2009-02-02
I assume that you have Ubuntu 8.04. Am I right? I believe it would be more wise to try first to better setup PulseAudio. If you setup it you'll be able to play many sounds at the same time.

Before removing PulseAudio totally you should, indeed, know for sure that your card has a hardware mixer. Because, if it does not have, after removing it, you will still have the same problem. You will only be able to play one sound at a time (there are chances that your card can only play one concurrent sound, or maybe two, or very few).

---

### Post by sydbat on 2009-02-02
How do you check if your sound card has a hardware mixer?

---

### Post by kostkon on 2009-02-02
> **sydbat said:**
> How do you check if your sound card has a hardware mixer?
Do a little research about your card, for example manuals, or even the ALSA info about it, etc.


I have to say that, actually, ALSA has a software mixer (albeit very simple when compared to PulseAudio). The problem is that many programs bypass the ALSA mixer (dmix) and try to use the card directly. That's why it is useful that your card has a hardware mixer. Unfortunately, these programs also don't work with PulseAudio.

So why use PulseAudio then? Eh, for the many advantages that is offers.

The most important and usually not advertised much, it is that it produces much better sound than dmix.

---

### Post by stoogiebuncho on 2009-02-02
Your responses sent me on a research frenzy where I discovered that PulseAudio and ALSA are a twisting tree of complexity where each leaf is a unique problem with it's own unique solution.

I've looked at the guides to setting up Pulseaudio, and at this point I am a little too scared to try them.  They are long and complex, and involve doing a lot of things that I don't understand and wouldn't know how to reverse.  Plus, it seems like even after configuring Pulseaudio, you still have to configure a lot of your own programs to use Pulseaudio correctly.

I did, however, find something that works for me.

I tried going to System > Preferences > Sound and changing everything to Alsa, but that didn't work at first.  HOWEVER, after I went into Synaptic and installed the alsa-firmware and alsa-firmware-loaders packages.  Then I changed everything to ALSA again and this time it worked.

It seems that the problem is that Ubuntu has only recently started using PulseAudio, and many of the programs are still set up to use ALSA, creating problems.  So I expect that in time this will work a little smoother out of the box.

Thanks for your help, everyone.

---

