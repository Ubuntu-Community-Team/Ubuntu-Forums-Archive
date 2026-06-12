---
title: "ALSA, Sound, Pulseaudio...."
date: 2009-05-05
forum: New to Ubuntu
---

### Post by zbrukas on 2009-05-05
Hi all ubuntuers.

This is my 1st post in ubuntu forums, although i'm working w ubuntu for a time now.

My problem is: No Sound. But it's strange because i've followed some upgrade guides and pulseaudio guides and alsa guides and the problem isn't solved.

I've upgraded from Intrepid to Jaunty last month and after the upgrade the sound stopped working. Since then, i followed a guide in ubuntuforuns about the upgrade, i reinstalled the packages, i reinstalled alsa... still the same.

Pulseaudio captures the sound (playback is working with all the programs). The Master volume is 100%. I've got installed Gnome Alsa mixer, padevchooser, pavucontrol etc.

I can't do much, so any help is appreciated (because i can't work without music :P :P) 

thanks in advance

---

### Post by jobbesat on 2009-05-05
Did you [this]("http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html")?

---

### Post by zbrukas on 2009-05-05
yes i did it before doing the ubuntuforuns guide

---

### Post by Durden on 2009-05-05
I wish there was a simple answer to this. I've found PulseAudio to be so horrendous and buggy that I've returned to Windows Vista as my main desktop OS until they get their act together. PulseAudio should never have been included in it's present state. It's absolutely unforgivable Ubuntu would make Pulse the default the way it has.

That said I do get it to work but it takes a ton of configuring and tweaking to do so and it inevitably breaks again or just flat out stops working, usually when using Rythmbox and a flash video in Firefox.

I wish I could be more helpful but trying to nail down Pulse problems is like shooting at a moving target 10 miles away. There are just so many problems that it could literally be anything.

Perhaps disable Pulse and just go the ALSA route? I've done this too.

---

### Post by Ptero-4 on 2009-05-05
Perhaps just remove pulseaudio and go back to alsa.

---

### Post by zbrukas on 2009-05-05
how do i disable it? also, how do i make alsa default sound card and all that stuff?

---

### Post by Ptero-4 on 2009-05-05
go to aptitude and remove this packages
```

p   gnome-volume-control-pulse      - GNOME media utilities - gnome-volume-contr
p   gstreamer0.10-pulseaudio        - GStreamer plugin for PulseAudio           
p   libpulse-browse0                - PulseAudio client libraries (zeroconf supp
p   libpulse-browse0-dbg            - PulseAudio client libraries (zeroconf supp
p   libpulse-dev                    - PulseAudio client development headers and 
p   libpulse-mainloop-glib0         - PulseAudio client libraries (glib support)
p   libpulse-mainloop-glib0-dbg     - PulseAudio client libraries (glib support)
i A libpulse0                       - PulseAudio client libraries               
p   libpulse0-dbg                   - PulseAudio client libraries detached debug
p   libpulsecore9                   - PulseAudio sound server core              
p   libpulsecore9-dbg               - PulseAudio sound server core detached debu
p   libsdl1.2debian-pulseaudio      - Simple DirectMedia Layer (with X11 and Pul
p   pulseaudio                      - PulseAudio sound server                   
p   pulseaudio-dbg                  - PulseAudio sound server detached debugging
p   pulseaudio-esound-compat        - PulseAudio ESD compatibility layer        
p   pulseaudio-esound-compat-dbg    - PulseAudio ESD compatibility layer debuggi
p   pulseaudio-module-gconf         - GConf module for PulseAudio sound server  
p   pulseaudio-module-gconf-dbg     - GConf module for PulseAudio sound server d
p   pulseaudio-module-hal           - HAL device detection module for PulseAudio
p   pulseaudio-module-hal-dbg       - HAL module for PulseAudio sound server deb
p   pulseaudio-module-lirc          - lirc module for PulseAudio sound server   
p   pulseaudio-module-lirc-dbg      - lirc module for PulseAudio sound server de
p   pulseaudio-module-x11           - X11 module for PulseAudio sound server    
p   pulseaudio-module-x11-dbg       - X11 module for PulseAudio sound server deb
p   pulseaudio-module-zeroconf      - Zeroconf module for PulseAudio sound serve
p   pulseaudio-module-zeroconf-dbg  - Zeroconf module for PulseAudio sound serve
p   pulseaudio-utils                - Command line tools for the PulseAudio soun
p   pulseaudio-utils-dbg            - PulseAudio command line tools detached deb
p   vlc-plugin-pulse                - PulseAudio plugin for VLC                 
p   xmms2-plugin-pulse              - XMMS2 - pulseaudio output plugin

```
The only one that will remain is libpulse0. After that reboot and alsa will be running your soundcard.

---

### Post by zbrukas on 2009-05-06
uninstalled it all except libpulse0. still no sound... this is quite unusual, my mom's computer also upgraded and has sound

EDIT: when i shutdown, the splash screen bar goes till half and then it passes to text. it shows that alsa is trying to shutdown but it stays indefinitely and doesn't shut. maybe it can help solving the problem...

---

### Post by Don1500 on 2009-05-06
FINALLY!!! I now have one less reason to go back to Windows! I have all the sound I need and I can record ANYTHING!

Thanks!

---

### Post by linuxvacuum on 2009-05-10
Here is Ptero-4's command:

```
sudo apt-get remove gnome-volume-control-pulse gstreamer0.10-pulseaudio libpulse-browse0 libpulse-browse0-dbg libpulse-dev libpulse-mainloop-glib0 libpulse-mainloop-glib0-dbg libpulse0 libpulse0-dbg libpulsecore9 libpulsecore9-dbg libsdl1.2debian-pulseaudio pulseaudio pulseaudio-dbg pulseaudio-esound-compat pulseaudio-esound-compat-dbg pulseaudio-module-gconf pulseaudio-module-gconf-dbg pulseaudio-module-hal pulseaudio-module-hal-dbg pulseaudio-module-lirc pulseaudio-module-lirc-dbg pulseaudio-module-x11 pulseaudio-module-x11-dbg pulseaudio-module-zeroconf pulseaudio-module-zeroconf-dbg pulseaudio-utils pulseaudio-utils-dbg vlc-plugin-pulse xmms2-plugin-pulse
```

I did not have many of these packages with the default installation of Jaunty, so I entered this :
```
sudo apt-get remove gstreamer0.10-pulseaudio libpulse-browse0 libpulse0 libpulsecore9 pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils
```

But it will free more than a 100 megs of space, so don't accept. libpulse0 is linked with many other important packages. I tried this instead:
```
sudo apt-get remove gstreamer0.10-pulseaudio libpulse-browse0 libpulsecore9 pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils
```

without libpulse0 and 12.6MB were freed. I will update if it worked out for me too.

---

### Post by lkraemer on 2009-05-11
Here is a link to a posting on how to fix PulseAudio.
I normally just Open a Terminal window and use:

```

killall pulseaudio

```
instead, but want to try the fix in the future.

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

lkraemer

---

### Post by zbrukas on 2009-05-11
i've uninstalled all the pulseaudio pkgs except libpulse0. i'm working with alsa only. the problem now is that sometimes it gives sound, and sometimes doesn't. like i'm playing a music in rhythmbox and when the music ends and it passes to the next music, sound's gone. does somebody know a alsa troubleshooting thread?

---

### Post by linuxvacuum on 2009-05-11
Thanks Ptero-4 for the solution! Now I wonder why pulseaudio isn't removed in the default installation since it crashes so often and adds an overhead to ALSA which works perfectly?

---

### Post by finer recliner on 2009-05-11
for those upgrading to jaunty and then having sound problems, try deleting your ~/.pulseaudio directory and then restart pulseaudio. that solved my quirky problems :)

---

### Post by KagetsukiZero on 2009-05-11
First off one other possibility is your user account doesn't have permissions to use the sound system. This is an attribute/permission that seems to have been added recently, and I had a problem recently with a user not being able to play sound. I guess if you have a lot of remote users logging in and playing random things maybe that will help stop your server from all the sudden blaring random sounds. Anyway, check your user account permissions.

As for ALSA vs PulseAudio, as I understand it ALSA has problems with multiple streams from different applications being played simultaneously. It's a fault of its design and as the design of PulseAudio was better it looks like many people were looking to PulseAudio as a better future solution. You may want to note we had OSS before ALSA, and the transition from OSS to ALSA was equally as uncomfortable if not perhaps worse. It should also be noted the performance of PulseAudio seems to be quite different depending on device and which applications you are using. When you are using Pulse for example and an application only supports ALSA you can get strange things happening.

I myself have had extensive problems with PulseAudio in terms of recording/using the microphone or line in. Playback on the other hand has been flawless lately and has easily outperformed ALSA alone. It would seem Pulse needs more developers, and if possible development from the sound hardware industry.

---

### Post by zbrukas on 2009-05-20
i think i found it.

for those others that have the same problems...

check in your alsa mixer for a label named Independent HP. I has to be OFF, otherwise it won't work. then re-install pulseaudio.

i guess that it went OFF in the intrepid / jaunty transition...

---

