---
title: "no sound"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by jbumgar on 2010-03-29
I don't have any sound in 9.10.  Seems like 9.04 was a better version.

---

### Post by mikeyphi on 2010-03-29
Don't take this the wrong way!!

I was caught out at first because the install leaves sound 'muted' by default - otherwise everything else seems the same as before.

---

### Post by jbumgar on 2010-03-29
No insult taken my friend.  I tried the suggestion but still no sound.  Am now going to be real brave/stupid and upgrade to the beta.

---

### Post by n0dix on 2010-03-29
At least you can post some specifications of your hardware and software.

---

### Post by lidex on 2010-03-29
There are some generic sound issues recurring in Karmic. This page addresses them:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

### Post by NightwishFan on 2010-03-29
Also ensure a mixer was not silenced by mistake. Run this in a terminal.
```
alsamixer -c0
```

---

### Post by Agent ME on 2010-03-29
I've had a similar problem since upgrading to 9.10. Running "sudo alsa force-reload" in a terminal would fix it for me, but each time I reboot I have to do it again. Haven't really looked around yet for a real fix. (There was a new alsa update today and I haven't rebooted yet, so maybe that fixed it. Haven't checked yet.)

EDIT:
> **lidex said:**
> There are some generic sound issues recurring in Karmic. This page addresses them:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
Awesome, I added the [Ubuntu audio dev PPA](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa) as it recommended, and now sound works right from booting up! Now if only it could also get my right microphone to work.

---

### Post by Tynut on 2010-03-30
8.10 Intrepid

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mom/.gvfs
      Output information may be incomplete.
Terminating processes: 5515lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mom/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mom/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mom/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mom/.gvfs
      Output information may be incomplete.
Terminating processes: 5515lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mom/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mom/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mom/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
mom@mom-laptop:~$ 
snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
mom@mom-laptop:~$ 

Who can help with this? I think I have tried everything

---

### Post by jbumgar on 2010-03-30
alsamixer -c0  fixed it.  Many thanks.  Also it reset the volume down but that was no big thing.

---

