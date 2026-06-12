---
title: "Help with audio (Pulse Audio) 11.04"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by hunter99507 on 2011-05-08
I am running 11.04 and I need help with my audio. It seems like every 10 or so times i start up ubuntu their is no audio.  The temporary fix for it is to restart the computer and it works fine (up until 10 restarts or so). 

Also I have had these same issues with 10.10 as well. I am using pulse audio and i have restarted it but it still doesnt work.

```
killall pulseaudio
```

Can someone help? Thanks

---

### Post by hunter99507 on 2011-05-08
I figured I would add more information


```
cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
Codec: Conexant ID 2c06
Codec: Nvidia MCP77/78 HDMI

```

---

### Post by hunter99507 on 2011-05-08
Ok after more research I figured out a better fix instead of restarting my computer.

```
sudo alsa force-reload
```

I am no expert in ubuntu, but im learning.  So this is a temporary fix, but i am still looking for a solution.  Anybody have one?

---

### Post by hunter99507 on 2011-05-14
Sorry for the bump but its almost been a week with no answer. Thanks

---

### Post by 5149.5 on 2011-05-14
I really struggled with pulseaudio. I spent two days trying every fix I could google. I finally ran across a post that slammed pulseaudio for being what it is and advised to just remove it. I promptly did exactly that and alsa does everything I need. Good riddance to the overly complicated, bloated piece of dung that pulse audio is.

---

### Post by nikamech on 2011-05-20
I've been wrestling pulseaudio for over a year.  Sometimes it doesn't load my sound card, sometimes it does.  
I telecommute from Europe to the USA, so my VoIP phone is pretty important to me.

Thanks for the alsa force-reload command.  It's the first time I've seen that, and it seems to work like a charm.

---

