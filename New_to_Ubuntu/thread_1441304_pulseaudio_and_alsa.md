---
title: "pulseaudio and alsa"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by His on 2010-03-28
I just posted this in the multimedia and video section, but then realized the beginner talk might be a better place for this post, so here it is.

I have few questions:

1) What is the difference between Pulse and Alsa? Or is that really an answerable question? Does one do things the other doesn't do? My understanding is that they are two different ways of doing the same thing.

2) Is one better?

3) If they are just two different ways of doing the same thing, why are they both installed?

Thanks. By these questions, I'm hoping to figure out how to resolve some audio issues. It's mostly with my microphone, sound is usually fine, but my internal mic is buggy.

---

### Post by lidex on 2010-03-28
[ALSA]("http://www.alsa-project.org/main/index.php/Main_Page")

[PulseAudio]("http://pulseaudio.org/")

---

### Post by sandyd on 2010-03-28
> **His said:**
> I just posted this in the multimedia and video section, but then realized the beginner talk might be a better place for this post, so here it is.

I have few questions:

1) What is the difference between Pulse and Alsa? Or is that really an answerable question? Does one do things the other doesn't do? My understanding is that they are two different ways of doing the same thing.

2) Is one better?

3) If they are just two different ways of doing the same thing, why are they both installed?

Thanks. By these questions, I'm hoping to figure out how to resolve some audio issues. It's mostly with my microphone, sound is usually fine, but my internal mic is buggy.
**Extremely shortened version of**
> **lidex said:**
> [ALSA]("http://www.alsa-project.org/main/index.php/Main_Page")

[PulseAudio]("http://pulseaudio.org/")
ALSA stands for AdvancedLinuxSoundArchetecture. This sound system is the standard sound system that is used in ubuntu systems. Its been used for a number of years now, and it replaces OSS. It generally allows multiple connections, while OSS only allows one.

Pulseaudio is a new implementation of a sound server. It tries to combine several sound servers into one. IMO, it is currently severly broken for some people, and works for others. This is due to a problem with ubuntu's implementation of pulseaudio, not pulseaudio itself.

Take your pick.

---

