---
title: "Audio trouble in Ubuntu"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by STDRuler on 2010-11-10
I am definitely an absolute beginner when it comes to Ubuntu and Linux, so please go easy on me!

My trouble with the audio is that I can adjust the sound level in the default music player for the music only, but for games, youtube and any other sound that isn't coming from the music player when I try to adjust my systems volume it doesn't actually go up or down. Basically it just sounds muffled at the same volume level when I go down and then cuts off before it's down the whole way. Opposite when I go up, it starts to sound more clear.

Is this common or normal? It's a little bit annoying. I can adjust youtube videos with the sound on the youtube player, but when I try with my system sound or the hardware buttons on my computer it just does what I explained up there. Any idea?

---

### Post by sandyd on 2010-11-10
> **STDRuler said:**
> I am definitely an absolute beginner when it comes to Ubuntu and Linux, so please go easy on me!

My trouble with the audio is that I can adjust the sound level in the default music player for the music only, but for games, youtube and any other sound that isn't coming from the music player when I try to adjust my systems volume it doesn't actually go up or down. Basically it just sounds muffled at the same volume level when I go down and then cuts off before it's down the whole way. Opposite when I go up, it starts to sound more clear.

Is this common or normal? It's a little bit annoying. I can adjust youtube videos with the sound on the youtube player, but when I try with my system sound or the hardware buttons on my computer it just does what I explained up there. Any idea?
run
```

alsamixer
```
in a terminal.
see if adjusting volume levels there work.

---

### Post by STDRuler on 2010-11-10
When I adjust it under 'master' it has the same problem. However, when I adjust the volume under 'PCM', it adjusts it how it should. It doesn't change the sound, just makes it quieter or louder. Is there anyway to only adjust that without having to open a terminal each time? (i.e. with the hardware buttons on my laptop?)

thanks for the reply.

---

### Post by sandyd on 2010-11-10
> **STDRuler said:**
> When I adjust it under 'master' it has the same problem. However, when I adjust the volume under 'PCM', it adjusts it how it should. It doesn't change the sound, just makes it quieter or louder. Is there anyway to only adjust that without having to open a terminal each time? (i.e. with the hardware buttons on my laptop?)

thanks for the reply.

not sure, I don't use ubuntu (much less gnome....)
however probably one of the forum members will know how to fix the volume button maps on your computer.

---

### Post by STDRuler on 2010-11-10
I found this:

[http://www.linuxquestions.org/questions/suse-novell-60/master-volume-control-doesnt-work-only-pcm-does-461609/](http://www.linuxquestions.org/questions/suse-novell-60/master-volume-control-doesnt-work-only-pcm-does-461609/)

I have almost an identical situation to him. The solution in that thread didn't work for me though. I installed kmix and when I right click to select a master channel, there is only one option that is already selected. :(

---

### Post by STDRuler on 2010-11-13
Sorry for double post ..any help would be greatly appreciated.

I don't know if this is correct, but I've come to the conclusion that I need to somehow change the master volume (aka what my keyboard volume adjusts) to adjust only the PCM volume. Any ideas?

---

### Post by zawmai on 2010-11-13
> **STDRuler said:**
> I found this:

[http://www.linuxquestions.org/questions/suse-novell-60/master-volume-control-doesnt-work-only-pcm-does-461609/](http://www.linuxquestions.org/questions/suse-novell-60/master-volume-control-doesnt-work-only-pcm-does-461609/)

I have almost an identical situation to him. The solution in that thread didn't work for me though. I installed kmix and when I right click to select a master channel, there is only one option that is already selected. :(
I think the reason why KMIX doesn't work for you is because you're using Gnome, which is what Ubuntu normally uses. I think KMIX was intended for KDE. Kubuntu uses KDE. Google what Gnome and KDE is. Sorry this is just for your interest. Hope you solve your problem.

---

### Post by STDRuler on 2010-11-13
I knew there was a difference, I didn't exactly what. I was just trying everything I found that someone had a similar problem. But thank you for pointing it out.

I did finally fix it. 
I typed this:
> $ sudo gedit /etc/modprobe.d/alsa-base

which popped a text file, in which i typed:
> options snd-hda-intel model=gateway-m4

and saved and restarted. That fixed the volume problem but it made everything sound really flat and tinny. So I installed the pulseaudio-equalizer. Now everything is fixed! woo

---

