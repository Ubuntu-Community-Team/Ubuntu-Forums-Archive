---
title: "Dummy Output. Lost sound"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by nnjond on 2010-10-22
Hi,

My sound was working fine. Now I've lost it and the Pulse audio gui claims it has a Dummy Ouput. If I understand correctly, the below indicates my sound card has not been detected.

nnjond@nnjond-den:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfdf78000 irq 22
 1 [Socialize      ]: USB-Audio - VF0640 Live! Cam Socialize
                      Creative Labs VF0640 Live! Cam Socialize at usb-0000:00:02.1-1, high speed
nnjond@nnjond-den:~$ 

I have tried to follow the advice below but ran into a problem:


 Make the sound card being recognized: => Purge alsa-base and pulseaudio, eg:

sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/nnjond/.gvfs
      Output information may be incomplete.
Terminating processes: 4842lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/nnjond/.gvfs
      Output information may be incomplete.
 6746lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/nnjond/.gvfs
      Output information may be incomplete.
 6763lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/nnjond/.gvfs
      Output information may be incomplete.
 6780lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/nnjond/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 6796lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/nnjond/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 6814(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/nnjond/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 6814(pulseaudio). 
Unloading ALSA sound driver modules: snd-seq-midi snd-seq-midi-event snd-seq snd-hda-codec-realtek snd-hda-intel snd-usb-audio snd-hda-codec snd-pcm snd-hwdep snd-usbmidi-lib snd-rawmidi snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-realtek snd-hda-intel snd-usb-audio snd-hda-codec snd-pcm snd-hwdep snd-usbmidi-lib snd-rawmidi snd-timer snd-seq-device snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-midi snd-seq-midi-event snd-seq snd-hda-codec-realtek snd-hda-intel snd-usb-audio snd-hda-codec snd-pcm snd-hwdep snd-usbmidi-lib snd-rawmidi snd-timer snd-seq-device snd-page-alloc.
nnjond@nnjond-den:~$ 

Can anyone advise me on my next move please?

---

