---
title: "Newbie, Lost sound on update to 9.10"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by readerbee on 2010-01-04
I'm a newbie (on a big learning curve) & since updating from the 9.04 Jaunty to the 9.10 Karmic, have no sound. I have tried to first resolve the problem myself, by following several threads covering the subject here & except for a 'force reload' command that works only as long as I kept the puter running.. have found no fix. Even todays system updates did nothing. I'm now to the point where I fear reading of someone elses shared problem & implementing same since I'm concerned that some of the ineffective commands used may in fact, now be a new part of my problem. I can't help but to wonder if in fact I may have deleted something that's actually necessary.

I'd really appreciate it if someone knowledgeable could walk with me through this problem. I no longer know what more to do & could really use the support. Please, let me know what information is needed from me so that we can begin resolving this matter today.

Thanks ever so much (in advance) to whatever kind soul responds.

---

### Post by FCS tech on 2010-01-04
I'm a newbie also. I updated when 9.10 came out. Last night I had sound this morning not.
So you're not alone. Hopefully someone knows something to help us.

---

### Post by readerbee on 2010-01-04
I'm going to try helping this along. 

Posted below is a screenshot of the commands I've used with temporary success:

When I enter: **alsamixer** to the terminal screen, this is the result I get .

In addition, I have als included in the attached, the only commands that have worked for me (so far) to get sound back temporarily (until I shutdown the puter). I will next post the results of each command used in that attachment, as I again use it.

---

### Post by readerbee on 2010-01-04
RESULTS from 1st command:

ritxxxxx@system76-pc:~$ sudo apt-get install asoundconf-gtk && asoundconf-gtk[sudo] password for ritxxxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
asoundconf-gtk is already the newest version.
The following packages were automatically installed and are no longer required:
  libnumber-compare-perl libdigest-sha1-perl libnet-ip-perl libnet-dns-perl
  clamav libfile-find-rule-perl clamav-base libclamav6 libdate-calc-perl
  libcarp-clan-perl libtext-glob-perl clamav-freshclam libconfig-tiny-perl
  libtommath0 binutils-static libdigest-hmac-perl libbit-vector-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sh: /usr/bin/asoundconf: not found
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!
ritxxxxx@system76-pc:~$ 

=====

RESULTS from the 2nd command:

ritxxxxx [note: edited out my full name] @system76-pc:~$ sudo /sbin/alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ritxxxxx/.gvfs
      Output information may be incomplete.
Terminating processes: 1493lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ritxxxxx/.gvfs
      Output information may be incomplete.
 2160lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ritxxxxx/.gvfs
      Output information may be incomplete.
 3519lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ritxxxxx/.gvfs
      Output information may be incomplete.
 3549lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ritxxxxx/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 3582lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ritxxxxx/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 3619(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ritxxxxx/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 3619(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

End of Terminal response.

The results seem to indicate problems, but in truth - this is greek to me. I've tried looking for insightful info about this in the 'Beginning Ubuntu Linux' book but its not helping. I really need someone to dialogue with.

For the time being, until I shutdown the puter - the result of these commands temporarily restores sound. If I reboot, it will be gone again.

The only other thing I can think to doother than ask for help here, is to call System 76, but that's a last resort. Please let me know what other info is required in resolving this dilemma. Thanks again.

---

### Post by readerbee on 2010-01-05
Bump.. Please, I need the help. If I said something wrong (my apologies, I apparently am not communicating very effectively) bring it to my attention, but don't ignore me. 

FCS - I don't know how successful I'm going to be here.. you may want to read some of the threads already posted. They can be found by doing a search. I did this, but without success which is why I created a new thread for my situation. Hopefully you'll have better luck.

---

### Post by bodhi.zazen on 2010-01-05
In alsamixer or your sound mixer (graphical) turn the volume of your front speaker up =)

---

### Post by readerbee on 2010-01-06
I would if I could, but I can't.. it won't let me change anything.

---

### Post by khopek on 2010-01-07
When you're in alsamixer in Terminal, you need to use your keyboard to adjust sound. :D It took me a bit to figure this out as well the first time, but the arrow keys are your best friends.

As far as the System->Preferences->Sound..I have no options anymore to change everything to Alsa...

---

### Post by bodhi.zazen on 2010-01-07
You can do it graphically with pavucontrol - PulseAudio Volume Control

Open PAVC and change to alsa.

---

### Post by kronictokr on 2010-02-14
try this, has various fixes included, works like a charm

[http://swiss.ubuntuforums.org/showthread.php?t=1395089](http://swiss.ubuntuforums.org/showthread.php?t=1395089)

---

