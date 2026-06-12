---
title: "Sounds gone funny..."
date: 2009-04-17
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-04-17
It appears between shutting down my pc last night and turning it on today that the sounds got mucked up:( I now only have a static sound coming from my speakers instead of startup and shutdown sounds and the same for music and videos...

Using Ubuntu 8.10 64bit

---

### Post by linux_tech on 2009-04-17
Try stopping pulseaudio and restart alsa

```
sudo killall pulseaudio

sudo alsa force-reload
```

Then under System->Preferences->Sound,  adjust settings to ALSA

---

### Post by kamitsukai on 2009-04-17
I get this error and now I have now sound :)

```

carl@carl-desktop:~$ sudo killall pulseaudio
[sudo] password for carl:
pulseaudio: no process killed
carl@carl-desktop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/carl/.gvfs
      Output information may be incomplete.
Terminating processes: 13917lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/carl/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/carl/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/carl/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

```

---

### Post by kamitsukai on 2009-04-17
Ok fixed the problem with this command:
```
alsamixer -Dhw
```

It appears that for some reason PCM was set to 0....

_Found Info in this Bug Report:_
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275392](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275392)

---

