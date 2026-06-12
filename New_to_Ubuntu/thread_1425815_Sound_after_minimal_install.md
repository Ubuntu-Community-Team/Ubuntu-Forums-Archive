---
title: "Sound after minimal install"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by pall111 on 2010-03-09
Hey, After a minimal install i have no sound. On a regular install I have sound... 

When I open mixer I get...

GStreamer was unable to detect any sound devices some sound system specific GStreamer packages may be missing. it may also be a permission problem.

Help? :3 

Thanks.

---

### Post by undecim on 2010-03-09
do you have alsa-base installed?

---

### Post by pall111 on 2010-03-09
> **undecim said:**
> do you have alsa-base installed?

No, should i?

---

### Post by undecim on 2010-03-09
> **pall111 said:**
> No, should i?

That is how you get your sound.

---

### Post by pall111 on 2010-03-09
> **undecim said:**
> That is how you get your sound.

This is the second time you've helped me, thank you.

Ok so i install alsa-base but still mixer doesn't work..

---

### Post by undecim on 2010-03-09
Maybe you need gstreamer0.10-alsa? It's installed on mine as a dependency for listen. (I'm on 9.10 minimal, btw)

---

### Post by pall111 on 2010-03-09
> **undecim said:**
> Maybe you need gstreamer0.10-alsa? It's installed on mine as a dependency for listen. (I'm on 9.10 minimal, btw)

Allready installed :/

Anything else you can recommend. I'm on a eee pc 700 btw...

---

### Post by ankspo71 on 2010-03-09
[LEFT]Hi,
In 9.10 pulseaudio is the default sound server. I couldn't get the alsa sound server to work by itself in 9.10 mini like I could in the 9.04 mini. so try installing 'pulseaudio' if you haven't already.
Hope this helps.
[/LEFT]

---

### Post by pall111 on 2010-03-09
> **ankspo71 said:**
> [LEFT]Hi,
In 9.10 pulseaudio is the default sound server. I couldn't get the alsa sound server to work by itself in 9.10 mini like I could in the 9.04 mini. so try installing 'pulseaudio' if you haven't already.
Hope this helps.
[/LEFT]

It worked i think, i don't get a error message anymore... brb :p

BAWWW! still no sound.. My sound card doesn't seem to be detected... It is listed as Dummy output (pulseaudio mixer) in mixer.. So i need drivers? right?

Should i remove alsa? :/

---

### Post by pall111 on 2010-03-09
Bump :) I really need to fix this i have college tomorrow.

---

### Post by undecim on 2010-03-09
See if you have any profile options with the application pavucontrol under the "Configuration"

Also, if you just installed pulse, log out and log back in to make sure that it has access to the sound card (i.e. that it isn't being taken by another app)

---

### Post by pall111 on 2010-03-10
Bump I'm searching but i can't find anything :/

---

### Post by pall111 on 2010-03-12
C'mon some ones gotta know?

---

### Post by ankspo71 on 2010-03-12
What type of audio are you trying to play? That might determine what codec packages you need. You might be only lacking some gsteamer packages. Also, Ubuntu uses a command line player called canberra-gtk to play all system sounds (I think), but I know it uses canberra-gtk to play at least the login sound. To get that player and system sounds you would need to install gnome-session-canberra and ubuntu-sounds.

Here are my notes from the last time I built off of a mini install (gnome). 
I think this was for Karmic (it looks like it). This is a stripped down gnome version of Ubuntu.
```
Minimal (Ubuntu-Gnome) Installation.
Required before installing any packages:
sudo apt-get update

Required:
[ gnome-core gdm ] 

Semi Required:
[ x11-xserver-utils  gnome-utils gconf-editor file-roller gdebi gnome-system-tools x11-utils fast-user-switch-applet network-manager-gnome update-manager synaptic]

Audio:
[ pulseaudio gnome-session-canberra ubuntu-sounds ]

Appearance:
[ gnome-themes-ubuntu ubuntu-artwork usplash-theme-ubuntu human-theme tangerine-icon-theme gnome-screensaver ] 

3rd Party Drivers:
[ jockey-gtk ]

3D effects:
[ compiz emerald compizconfig-settings-manager simple-ccsm ]

Sort of recommended:
[ gcalctool f-spot xterm tsclient evince gconf-editor brasero firefox epiphany-browser ]

Extras for general installing packages from source code:
[ binutils cmake dpkg-dev g++ gcc gtk-sharp2 build-essential]

Lightweight Considerations:
xfburn htop xfce4-taskmanager xfce4-terminal terminator gtk2-engines-xfce
```*** in order for 3D effects to work, I think compiz required x11-xserver-utils or x11-utils (or something like that)

---

### Post by pall111 on 2010-03-12
> **ankspo71 said:**
> What type of audio are you trying to play? That might determine what codec packages you need. You might be only lacking some gsteamer packages. Also, Ubuntu uses a command line player called canberra-gtk to play all system sounds (I think), but I know it uses canberra-gtk to play at least the login sound. To get that player and system sounds you would need to install gnome-session-canberra and ubuntu-sounds.


So far i'm just testing with vlc and some random avi files :/ 

Like i said when i go on mixer only dummy cards are displayed.

---

### Post by pall111 on 2010-03-14
Dammit, i need help with this!

---

### Post by pall111 on 2010-03-16
Guys? This is the ubuntu forums right?! 

I still cannot get it to work! I even installed ubuntu on a virtual machine and installed the same packages from that onto my minimal install, still no success. I know some one must no the answer to this... 

Currently doing a clean minimal install.

---

### Post by lidex on 2010-03-16
Let's see the output of this terminal command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by lidex on 2010-03-16
Along with your clean minimal install you'll need these packages:
```
alsa-base
alsa-utils
alsa-oss
gstreamer0.10-alsa
libasound2
libasound2-plugins
```

---

### Post by masdjo on 2010-11-16
Have you 'UNMUTE' the audio channel ?
Do thhese step :
1. Open terminal
2. Type : alsamixer
3. Type letter 'M' until you get green colour on each channel and adjust volume
Mute show with MM , unmute displayed 00 with green background.
4. and lets getparty :P

I've tried this way with my Ubuntu 10.10 minimal (CLI) install + LXDE

---

