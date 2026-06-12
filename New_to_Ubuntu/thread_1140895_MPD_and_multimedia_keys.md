---
title: "MPD and multimedia keys?"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by lbelloq on 2009-04-28
Gentlemen:

I recently discovered mpd and started to use it in Jaunty. mpd + Sonata works OK, but I have the following problem:
Each time I configure ALSA output with
```
audio_output {
        type                    "alsa"
        name                    "Sound Card"
        options                 "dev=dmixer"
        device                  "plug:dmix"
}
```
in /etc/mpd.conf, mpd plays my music alright, but the volume keys on my multimedia keyboard do not affect mpd's volume output (they do affect GNOME's volume control nevertheless).
If I try to configure mpd with Pulseaudio with this:
```
audio_output {
        type    "pulse"
        name    "My MPD PulseAudio Output"
        server  "localhost"   # optional
        sink    "alsa_output" # optional
}
```
mpd does NOT play my music. Sonata just shows the track as stopped even if I doubleclick it.
What I want to do is to have mpd obey the standard audio output in GNOME, like, if I press VOLUME_DOWN in my keyboard, mpd lowers the volume as Banshee does it (may I say that Banshee has no problem with my keys; all of them work perfectly, and GNOME shows the notifications correctly when using the volume keys).
What should I configure? I can post files' contents if needed, and feel free to ask if my question is not clear enough.

Cheers,
Léster

---

### Post by mcduck on 2009-04-28
I don't think MPD has any built-in support for multimedia keys, and changing the audio output settings sure has no effect on that.

Some MPD clients, however, support multimedia keys. But if you really want to be able to use the keys without any client running I suggest using xbindkeys to bind the multimedia keys to MPC commands.

****
edit: In addition, you should check two things:

First, what mixer channel MPD is configured to use.

And second, what mixer channel(s) you have configured Gnome's volume control to adjust.

---

### Post by lbelloq on 2009-04-28
Thanks a lot for your suggestion.
What I did finally was to configure mpd with ALSA, and make GNOME control ALSA output volume with the multimedia keys (instead of Pulseaudio's output). Not really elegant, but works, and now I'm enjoying SKY.FM in Sonata.
Thanks again.

---

