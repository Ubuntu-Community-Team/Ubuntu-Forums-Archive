---
title: "Destroyed my sound settings in Jaunty"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-10-25
I realised I was quite stupid in making this post in other threads and I should just have started a new one. Anyway...

I made a mess of things. Basically, I added some repo's that totally destroyed my dependencies and I had to re-install a lot of packages (including alsa and pulse). I also had to re-install my kernel and numerous other things. One of the main things was that I installed an updated version of alsa-utils that did not contain asoundconf, so, when I reinstalled the older version of alsa-utils (the one containing asoundconf) all the settings were erased and my laptop's sound-card was not recognised.

In between doing all this my sound configuration got messed up. Before adding the repo everything was fine. So, I assume if I were to re-install jaunty at this point everything would work fine. But, of course, I'd rather not re-install everything.

What the basic commands show me:

```

$ aplay -l
aplay: device_list:217: no soundcards found...

```

```

$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

```

$ lspci
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 30a5
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

I've done everything in these guides: 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Nothing has worked for me. In fact I've done everything twice I think!

I also followed this guide ([http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)) a while back to remove pulseaudio and use alsa. At the time the guide worked fine and I have since used the computer without any problem. I'm confident that this guide did not cause my problem. However, due to my re-installation of all the packages the settings made in this guide MAY be causing problems now. In any case I have no idea!

From, what I can see my soundcard exists (indeed it is a fairly standard one from what I can tell), but, aplay -l does not recognise it or the driver is not loading. Anyway, like I said I did everything in those four guides and the "Comprehensive sound guide" suggested recompiling alsa and re-installing all the drivers. I even did that but no luck! Any help would be much appreciated.

---

### Post by NCLI on 2009-10-25
If I were you, I'd do a reinstall. Far simpler than retracing everything you've done. If you don't format your Ubuntu partition when reinstalling, you will keep your files.

---

### Post by abhiroopb on 2009-10-25
I agree it would probably be the best thing to do at this point. However, if someone can help me "reset" the sound then that may simply be easier overall. I have a lot of settings for various things and redoing all that would take time as well.

---

### Post by abhiroopb on 2009-10-25
Here is some more information:

```

$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/abhiroop/.gvfs
      Output information may be incomplete.
Terminating processes: 16943lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/abhiroop/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/abhiroop/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/abhiroop/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-usb-audio snd-usb-lib snd-hwdep snd-pcsp snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-usb-audio snd-usb-lib snd-hwdep snd-pcsp snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

```

```

$ speaker-test

speaker-test 1.0.18

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default
Playback open error: -2,No such file or directory

```

Obviously before I had these problems this would work fine and I'd hear "left speaker", "right speaker" etc.

---

