---
title: "Audio works in shell, but not X"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by abeisgreat on 2009-11-25
So I have this laptop, I built the OS from Ubuntu Server 9.10. No desktop manager, so it drops me to a shell on login. When I run 
```

mplayer Energy.mp3

```
in the shell, it runs, and plays the audio fine.
However, when I run the same command, from a uxterm after running
```

startx

```
I get no audio. Mplayer just sits, not advancing.
Why would this possibly be? If it helps, I am using openbox w/ uxterm.

Thanks,
Abe

---

### Post by openuniverse on 2009-11-25
.

---

### Post by nothingspecial on 2009-11-25
Do you have anything sert to start running when you start openbox?

The reason I ask is that if I run sueezeslave on my box (same set up as yours actually), no other audio will work untill I kill it, even if it`s not playing anything.

---

### Post by renkinjutsu on 2009-11-25
I remember this happening to me in Jaunty.. If i switched from framebuffer to X, audio from the framebuffer stops..

I couldn't find a fix for it... (although, the workaround was to log in, through GDM) .. Fortunately, this problem was fixed for me in 9.10.. i suspected pulseaudio was the culprit, so i never installed pulseaudio on my minimal install.. i'm only running on ALSA, and everything's working great

---

### Post by abeisgreat on 2009-11-25
Here is a screenshot of what is happening. The only things that load with Openbox is tint2 and nitrogen --restore. I am trying somethings now, and we shall see if they work. About GDM, I'll try that, if i have to. But GDM is so dang big, I miss slim.

---

### Post by openuniverse on 2009-11-25
.

---

### Post by abeisgreat on 2009-11-25
> **openuniverse said:**
> presumably it does the same with other mp3's? have you tried any other console players? (only asking, wouldn't try to switch you away from mplayer.)

I tried using VLC (not a console one, but regardless it should work) I've got it to the point where I can use pavucontrol to see my soundcard, and the application, but it shows no noise.

And yes, I've tried a few mp3s

---

### Post by VertexPusher on 2009-11-25
> **abeisgreat said:**
> Why would this possibly be?
Take a look at MPlayer's console output. Look for messages starting with "AO:". That's where MPlayer tells you which audio output driver it is using.

My guess is that it uses ALSA when you run the system in text-only mode because PulseAudio is started up along with X. ALSA works, PulseAudio doesn't.

---

### Post by abeisgreat on 2009-11-25
> **VertexPusher said:**
> Take a look at MPlayer's console output. Look for messages starting with "AO:". That's where MPlayer tells you which audio output driver it is using.

My guess is that it uses ALSA when you run the system in text-only mode because PulseAudio is started up along with X. ALSA works, PulseAudio doesn't.

That was not it, but regardless, thanks.

I ended up working around my issue. By fiddling around, and eventually I got to the point where the machine would load, display the audio in pavucontrols, but be set on dummy output. To force it to find my card I had to edit a file in /etc/pulse like this fellow said
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500/comments/14](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500/comments/14)

It works for now, thanks for the help everybody!

---

