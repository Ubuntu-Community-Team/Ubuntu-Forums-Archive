---
title: "Sound stopped working"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by SSRMNM on 2010-03-15
Sounds and music worked nicely earlier, but when I installed some audio drivers for WinXP on my other drive, all sounds are gone. Now there's just a "pop" instead of a sound :\

---

### Post by Li18nxBoy on 2010-03-15
I had a problem like this, try running:

sudo alsa force-reload

---

### Post by SSRMNM on 2010-03-15
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/morten/.gvfs
      Output information may be incomplete.
Terminating processes: 1662 1992 2020lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/morten/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/morten/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/morten/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

Didn't work :\

---

### Post by allenbradley on 2010-03-15
To get pedantics out of the way, did you max out all volumes in alsamixer?

---

### Post by thegod_slayer on 2010-03-15
first you need to check in synaptic that all your alsa drivers are installed or not.
if not then either you can uninstall all the alsa drivers and reinstall them
or you can just reinstall ubuntu

---

### Post by SSRMNM on 2010-03-15
> **thegod_slayer said:**
> or you can just reinstall ubuntu
I'll probably just do that :)

---

