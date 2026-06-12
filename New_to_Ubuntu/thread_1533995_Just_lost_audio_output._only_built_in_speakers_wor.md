---
title: "Just lost audio output. only built in speakers work. No headphones, external speakers"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by DesiArnez6 on 2010-07-18
My only guess is that it was one of those auto updates that popup, since I cant remember doing anything else with the computer except for listening to music or watching Internet TV.

My laptop speakers work fine, just nothing will work with the external audio hole, so when I connect my headphones or external speakers I hear nothing

Under diagnostics, Everything  works 100% fine.

Dell said they were sending a flash drive to reinstall the OS, and I also have the Ubuntu 9.04, But wouldn't that get rid of all my files, bookmarks, music etc? I think I'd just uprade first... But if the problem still exists?

I feel there must be a way to restore sound to my outbound audio slot, that is not so drastic as reinstalling or upgrading the OS.

I'd appreciate any insight.


-Desi

---

### Post by lidex on 2010-07-18
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by petrus250 on 2010-07-18
I had a problem similar to this, just disable pulseaudio with
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get autoremove
if this happens in ubuntu obviously

---

### Post by DesiArnez6 on 2010-07-18
Here is the output from the terminal commands you gave me:
```


desiarnez6@dell-desktop:~$ uname -a
Linux dell-desktop 2.6.28-19-generic #61-Ubuntu SMP Wed May 26 23:35:15 UTC 2010 i686 GNU/Linux
desiarnez6@dell-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
desiarnez6@dell-desktop:~$ dpkg -l | grep "alsa"
ii  alsa-base                                  1.0.18.dfsg-1ubuntu8                 ALSA driver configuration files
ii  alsa-oss                                   1.0.17-1                             ALSA wrapper for OSS applications
ii  alsa-utils                                 1.0.18-1ubuntu11                     ALSA utilities
ii  bluez-alsa                                 4.32-0ubuntu4.1                      Bluetooth audio support
ii  gstreamer0.10-alsa                         0.10.22-5                            GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.40-0ubuntu3                      Enlightened Sound Daemon (ALSA) - Shared lib
ii  libpt2.6.1-plugins-alsa                    2.6.1-0ubuntu4                       PTLib audio plugin for the ALSA Interface
ii  libsdl1.2debian-alsa                       1.2.13-4ubuntu3                      Simple DirectMedia Layer (with X11 and ALSA 
ii  libsox-fmt-alsa                            14.2.0-1                             SoX alsa format I/O library
desiarnez6@dell-desktop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC269
desiarnez6@dell-desktop:~$ 
```


The make/model: Dell Vostro V13

---

### Post by lidex on 2010-07-18
> **petrus250 said:**
> I had a problem similar to this, just disable pulseaudio with
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get autoremove
if this happens in ubuntu obviously
Yeah, that's a little extreme, removing pulseaudio for a first step.

---

### Post by lidex on 2010-07-18
> **DesiArnez6 said:**
> Here is the output from the terminal commands you gave me:
```


desiarnez6@dell-desktop:~$ uname -a
Linux dell-desktop 2.6.28-19-generic #61-Ubuntu SMP Wed May 26 23:35:15 UTC 2010 i686 GNU/Linux
desiarnez6@dell-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
desiarnez6@dell-desktop:~$ dpkg -l | grep "alsa"
ii  alsa-base                                  1.0.18.dfsg-1ubuntu8                 ALSA driver configuration files
ii  alsa-oss                                   1.0.17-1                             ALSA wrapper for OSS applications
ii  alsa-utils                                 1.0.18-1ubuntu11                     ALSA utilities
ii  bluez-alsa                                 4.32-0ubuntu4.1                      Bluetooth audio support
ii  gstreamer0.10-alsa                         0.10.22-5                            GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.40-0ubuntu3                      Enlightened Sound Daemon (ALSA) - Shared lib
ii  libpt2.6.1-plugins-alsa                    2.6.1-0ubuntu4                       PTLib audio plugin for the ALSA Interface
ii  libsdl1.2debian-alsa                       1.2.13-4ubuntu3                      Simple DirectMedia Layer (with X11 and ALSA 
ii  libsox-fmt-alsa                            14.2.0-1                             SoX alsa format I/O library
desiarnez6@dell-desktop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC269
desiarnez6@dell-desktop:~$ 
```


The make/model: Dell Vostro V13
Follow the alsa-upgrade link in my sig to get v. 1.0.23. Once finished (after a reboot) use alsamixer to unmute and reset levels.

---

### Post by DesiArnez6 on 2010-07-19
I cannot find the script that the site you gave me said to download

---

### Post by lidex on 2010-07-19
> **DesiArnez6 said:**
> I cannot find the script that the site you gave me said to download
It's at the bottom of the first post as an attachment:
[http://ubuntuforums.org/attachment.php?attachmentid=156468&d=1273598001](http://ubuntuforums.org/attachment.php?attachmentid=156468&d=1273598001)

---

### Post by DesiArnez6 on 2010-07-19
Thx, I just realized that ;) so I'm going through the process now. Thank God for my favorite radio station "Radio Sky" the stream is [http://193.231.242.46:8000/live2.ogg.m3u](http://193.231.242.46:8000/live2.ogg.m3u)
Its is really helping me relax through this "experience" :)

---

### Post by Jakiejake on 2010-07-19
> **DesiArnez6 said:**
> Thx, I just realized that ;) so I'm going through the process now. Thank God for my favorite radio station "Radio Sky" the stream is [http://193.231.242.46:8000/live2.ogg.m3u](http://193.231.242.46:8000/live2.ogg.m3u)
Its is really helping me relax through this "experience" :)

Great, Great, Great So can you boot into another os (live cd?) and see if you can get sound from that

---

### Post by DesiArnez6 on 2010-07-19
Ok, I did everything, rebooted, opened alsamixer, still no external sound. AND, now my screen shrunk? I have abot 2 inches of black space on the right and left (from the shrinking?)

---

### Post by DesiArnez6 on 2010-07-19
Trying from a live CD sounds like an excellent idea, I think I'll try it  now

---

### Post by DesiArnez6 on 2010-07-19
I can't find the External CD/DVD Drive so I will have to look for it tomorrow to test with a Live CD

*As for the shrinking screen, the second reboot eliminated that problem and screen size is normal

Downside, still no audio out put :( Now what do I do?

---

### Post by DesiArnez6 on 2010-07-20
So, I still cant find my external cd/dvd player, so i bought another one. Hopefully I'll find it within 30 days so I can return the second one back. So, more delay on using the Ubuntu Live DVD to help me test until I find my external CD/DVD player, or my second one arrives.

---

### Post by DesiArnez6 on 2010-07-31
Just wanted to update. It appears that after I upgraded alsa, for some reason external audio was muted in the Volume Control. After raising it, external sound worked fine :)

---

### Post by lidex on 2010-07-31
Excellent. If all is well please mark thread solved.

---

