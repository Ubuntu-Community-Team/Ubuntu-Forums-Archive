---
title: "Sound stopped - volume icon missing"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-03-10
While trying to get Blueman to work with a headset and Skype (and without chaning any lines in the OS files), my sound has gone bye-bye. I was chaning the Sound Devices from Default to headset. And back to Default.

ALSO, my volume control panel icon is gone gone gone.

Please see the attached screenshot. I tried System/Preferences/Sound and chose a test and got zilch. I googled audiotestsrc and got 1 hit, but not the one for me and the rest are about "bug" which I don't have as sound was working fine, yesterday (literally yesterday

How can I do a "clean install" of ALSA?

---

### Post by Mark_in_Hollywood on 2009-03-12
As of the time I read this post, 19 people have looked at it and I have Zero replies.

Googleing around I found:
[B]
Fix for "no sound" issue in Ubuntu 8.10 (Intrepid Ibex)[/B]
[http://onlyubuntu.blogspot.com/2008/11/fix-for-no-sound-issue-in-ubuntu-810.html](http://onlyubuntu.blogspot.com/2008/11/fix-for-no-sound-issue-in-ubuntu-810.html)

following that post, I did:

mark@Lexington-19:~$ sudo killall pulseaudio
[sudo] password for mark: 
pulseaudio: no process killed
mark@Lexington-19:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mark/.gvfs
      Output information may be incomplete.
Terminating processes: 13498 13502lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mark/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mark/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mark/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.


and then go to System>Preferences>Sound and change everything to ALSA

I didn't do that, I set all Sound configs to Autodetect and that restored sound. In Skype I had to select the first hardward and that fixed that problem.

I got the panel icon volume control back in Add/Remove

Thanks.

---

### Post by martrn on 2009-03-12
I might get told not to put this in here because it says 'Absolute Beginner Talk', but you asked.

> **Mark_in_Hollywood said:**
> How can I do a "clean install" of ALSA?

See :- 
[URL="https://help.ubuntu.com/community/SoundTroubleshooting"]
https://help.ubuntu.com/community/SoundTroubleshooting[/URL]

Scrolldown to the section where it says "ALSA driver Compilation" and follow this guide through.

Type :-

sudo apt-get install build-essential 
sudo apt-get install linux-headers-$(uname -r) 
sudo apt-get install alsa-source
sudo apt-get install module-assistant

sudo dpkg-reconfigure alsa-source

// Here you have a big (nice) blue screen where you can rebuild your alsa kernel modules (drivers).  You need to take note of your sound card and ensure it is selected.

From there try :
lspci -v | less
sudo modprobe snd-nameofsoundcard

Err. thats from greping my bash history.
You make need to 'sudo apt-get install' anything if it complains about something being missing.

Hope that helps.

---

