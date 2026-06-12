---
title: "Help with eKiga incoming call (pulseaudio or network problem?)"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by davidonlaptop on 2008-07-22
Hello!

I am trying to configure eKiga/Gizmo (call-in) and Skype (call-out) to work together with pulseaudio (or something else as long as the sound card can be shared).

eKiga used to work (via STUN server), but Skype was only working when the file /etc/asound.conf was empty and no flash application were playing. So I followed these guides :

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900) (part A,C)
[http://www.pulseaudio.org/wiki/PerfectSetup#ALSAApplications](http://www.pulseaudio.org/wiki/PerfectSetup#ALSAApplications)

(and upgraded my kernel from 2.6.24-16-generic to 2.6.24-19-generic, hardy 8.04).

And now Skype works great, but I can't receive any call on eKiga/Gizmo. I get no ring, and no error. I can play sounds in eKiga (Preferences / General / Sound Events / play), but if I do :

```
arecord -D plughw:0,0 -c 1 -r 8000 -f S16_LE - | aplay -D plughw:0,0 -c 1 -r 8000 -f S16_LE -
```

while another application is using the sound card, it says : "aplay: main:546: audio open error: Device or resource busy"...

How to know if the problem is coming from pulseaudio / Gizmo network / kernel upgrade / conflicting files / etc ?

I've spent a 4h+ reading on this, and I am humbly a confused...

Also, is there a simpler setup? Is pulseaudio really necessary to share the sound card between applications?

Thanks,

David

---

