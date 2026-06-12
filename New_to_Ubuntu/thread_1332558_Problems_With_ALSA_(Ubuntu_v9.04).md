---
title: "Problems With ALSA (Ubuntu v9.04)"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by lordofthedice on 2009-11-20
So, after accidentally opening the same program twice using Wine, I found that my sound no longer functioned at all. No sound or anything. So, I decided to restart my computer to see if that would solve my problem. Unfortunately, when I tried to restart, the computer froze and forced me to do a hard restart. Undoubtedly, this caused even more problems.

When the computer booted back up, I could hear the drum roll at he login screen, but afterwards everything was a crackling and popping static. After playing around with the sound settings a while, I google'd a bit and soon discovered that the problem was with my ALSA driver as I could switch things over to OSS and hear sound (or at least hear the tests on the sound settings screen.)

I found some people [here]("http://ubuntuforums.org/showthread.php?t=1239658") who seemed to have the same problem as me. Their solution was to go through the troubleshooting guide [here]("https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems"). I read ahead to someone mentioning that editing their /ect/modprobe.d/alsa-base.conf worked (they said "alsa-base.confadding", but I can't find that file, so I assume they mean .conf.) This person's problem was also more similar to mine as he mentions it happening after using a program in Wine.

Anyway, this corresponds to the part of the troubleshooting about configuring your driver to use the correct model for your chipset. I followed the instructions, uploading my system information to the website which you can find [here]("http://www.alsa-project.org/db/?f=db93a484e5d9fa4569b260a5e3e7582ec710ed21") as well as finding my ALSA-Configuration.txt which is [here]("http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=30499cf77d5628968a9347b3a6440a0064713eaf;hb=4c767126ddc90264b8d6584548f4aa859216f481"), though you might want to double-check this as it may be part of my problem.

So, I found my version number (1.0.18rc3), my loaded module (snd_hda_intel), and then my Codec (VT1708S). I then searched through the ALSA-Configuration.txt file for the. However, I must have missed something, because that codec is not listed in any form that I could recognize. Maybe this comes from not actually haveing an audio card and just using the onboard motherboard audio, but I don't know.

Anyway, I'd appreicate help finding the correct model name (I have 6 audio ports on my motherboard) or if someone has an alternative solution that might work, I'd appreciate it.

---

### Post by Zoot7 on 2009-11-25
You could give removing Pulseaudio a shot (if you haven't already), also what might be worth checking out is the Alsa Upgrade Script that's posted here:
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

Out of habit I've upgrading everything to Alsa 1.0.21 since it came out on account of it solving my audio problems.

---

