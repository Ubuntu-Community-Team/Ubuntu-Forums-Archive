---
title: "HP DV7 - Think I broke it!"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by laidback82 on 2009-11-05
Brand new to ubuntu and probably annoying people here by asking real dumb questions.

I have finally managed to get DVDs to play on my HP DV7 laptop. However, the only sound I'm getting comes from the base speaker at the bottom. 

In an effort to fix this I first did this:

sudo gedit /etc/modprobe.d/alsa-base
[I]options snd-hda-intel enable_msi=1

[/I]This caused my computer to freeze. Also - my alsa-base file seemed empty - is this normal?

I restarted and went to alsa-base.conf intending to do the same thing. However, once I edited the file it wouldn't allow me to save it. Told me I didn't have the necessary permissions.

Interestingly, I wasn't asked for my password when I opened alsa-base.conf.

I went back to alsa-base to delete what I'd done there (again, not asked for password) and again it wouldn't allow me to save changes.

Aaaarghh! Help!

PS - it's 9.10

I'm an idiot. I'm not posting again in this forum until I've had a long hard talk with myself about asking really stupid questions before thinking them through. All fixed now.

---

### Post by phillw on 2009-11-05
> I'm an idiot. I'm not posting again in this forum until I've had a long hard talk with myself about asking really stupid questions before thinking them through. All fixed now.

Yeah, sudo sucks  :lolflag:

Phill.

---

