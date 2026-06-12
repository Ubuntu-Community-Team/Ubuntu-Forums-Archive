---
title: "Easier Volume Control"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by Zenmij on 2010-04-20
Posting this here as I am not sure where best to ask.

Whenever I need to adjust the volume I click the icon top right which opens volume control. To adjust my headphone volume I need to switch devices to Intel 82801DB-ICH4 (Alsa Mixer). There I have Master Mono, Headphone, Line-In, Microphone.

When I adjust my Speaker Volume, the master mono level on that switch won't work so I need to switch to Playback: Intel 82801DB-ICH4 (Pulseaudio Mixer). I also have a device: SigmaTel (OSS Mixer) but I have never adjusted that.

Has anyone got any tips on how to 'streamline' this process? Do I need so many devices with different levels? Is there an optimum device/service I could adjust all levels with and get rid of the others? Or optionally a better interface to interact with all these levels.

Very many thanks.

---

### Post by uRock on 2010-04-20
I know this doesn't help much now, but I think things will work better for you in Lucid. I am testing it and changing from headphones to surround sound is working much better.

---

### Post by Zenmij on 2010-04-20
Thats in beta right? Thanks for the heads-up. I might be willing to try 10.04

---

### Post by P4man on 2010-04-20
you can change what the volume control.. ahm controls in system > preferences > sound. Then change it somehwere near the bottom, think its called "default mixer" (cant be more precise as im on Lucid currently).

You shouldnt have to use alsamixers though, you'd be better off using pulseaudio for everything.

---

### Post by Zenmij on 2010-04-20
the only problem with that is, pulseaudio has no levels for my headphones, I have to switch to alsa to do it.

---

