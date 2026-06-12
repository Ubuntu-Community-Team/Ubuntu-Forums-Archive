---
title: "need vlc on hardy. help me get it"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by beanco on 2009-08-08
I have just upgraded to hardy, yeah, I know I shoudl have done it earlier...

but now I am here and I need VLC, how can I get it?

Command line is the way I prefer to go.

thanks all!

Robi

---

### Post by credobyte on 2009-08-08
```
sudo apt-get install vlc

```

---

### Post by beanco on 2009-08-08
> **credobyte said:**
> ```
sudo apt-get install vlc

```

ooopps, I forgot to add that I already tried that


```
rob@rob-desktop:~$ sudo apt-get install vlc
[sudo] password for rob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vlc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  vlc-nox libvlc0
E: Package vlc has no installation candidate
```

Thanks 

robi

---

### Post by credobyte on 2009-08-08
Can you show us the contents of the following file ?
```
/etc/apt/sources.list
```

---

### Post by Liolikas on 2009-08-08
That s*: means Ubuntu do not have native vlc!

You have to edit your sources.lst file but i do not know exactly how.
Show it here.

---

### Post by beanco on 2009-08-08
rob@rob-desktop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
rob@rob-desktop:~$ sudo su -
root@rob-desktop:~# /etc/apt/sources.list
-su: /etc/apt/sources.list: Permission denied

---

### Post by credobyte on 2009-08-08
> **beanco said:**
> rob@rob-desktop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
rob@rob-desktop:~$ sudo su -
root@rob-desktop:~# /etc/apt/sources.list
-su: /etc/apt/sources.list: Permission denied

```
sudo gedit /etc/apt/sources.list
```

---

### Post by longtom on 2009-08-08
too late....ignore

---

### Post by credobyte on 2009-08-08
Anyway, I feel that I'll need to leave in a few minutes, so ..

Open sources.list ( as previously shown ) and add these lines ( if not already there):
```
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse

deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

```Then update & install:
```
sudo apt-get update && sudo apt-get install vlc
```

---

### Post by beanco on 2009-08-09
credobyte,

I tried your last command and get this


Cannot set local to  ".


Any ideas?

thansk

robi

---

### Post by swong on 2009-08-09
Have you tried these instructions [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by steveneddy on 2009-08-09
Open up Synaptic Package Manager

System --> Administrator --> Synaptic Package Manager

Look for vlc

right click, mark for installation

on top, click the Apply green check mark

---

### Post by beanco on 2009-08-10
I tried to open up VLc again and it works..

i get that error message, but then, behind it VLc starts running. I close the error message window and watch whatever I want...

thansk

robi

---

### Post by andrew.46 on 2009-08-10
Hi beanco,

> **beanco said:**
> I have just upgraded to hardy, yeah, I know I shoudl have done it earlier...

but now I am here and I need VLC, how can I get it?

I have a deep suspicion that some of your troubles relate to the fact that you have *upgraded* rather than done a clean install. Perhaps things have improved a little in recent times but for myself I will not go down the upgrade road for any Linux distro.

I have in fact just done a clean install of Hardy on Virtualbox and by default main, universe, restricted and multiverse repositories are enabled and apt-cache shows a multitude of options for vlc:

```

andrew@skamandros:~$ apt-cache search vlc
dvd95 - DVD9 to DVD5 converter
getstream - DVB streaming application
hdhomerun-config - Configuration utility for Silicon Dust HD HomeRun
libvcdinfo-dev - library to extract information from VideoCD (development files)
libvcdinfo0 - library to extract information from VideoCD
mythbuntu-lirc-generator - Mythbuntu Lirc Configuration Generator
pidgin-mpris - sets your available message to your currently playing track
videolan-doc - documentation for the VideoLAN streaming solution
vls - lightweight MPEG and DVD video streaming server
freeplayer - wrapper around vlc for French ADSL FreeBox
x264 - video encoder for the H.264/MPEG-4 AVC standard
[B][COLOR="Red"]libvlc0 - multimedia player and streamer library
libvlc0-dev - development files for VLC
mozilla-plugin-vlc - multimedia plugin for web browsers based on VLC
vlc - multimedia player and streamer
vlc-nox - multimedia player and streamer (without X support)
vlc-plugin-alsa - dummy transitional package
vlc-plugin-arts - aRts audio output plugin for VLC
vlc-plugin-esd - Esound audio output plugin for VLC
vlc-plugin-ggi - GGI video output plugin for VLC
vlc-plugin-glide - Glide video output plugin for VLC
vlc-plugin-pulse - Pulseaudio audio output plugin for VLC
vlc-plugin-sdl - SDL video and audio output plugin for VLC
vlc-plugin-svgalib - SVGAlib video output plugin for VLC[/COLOR][/B]
wxvlc - dummy transitional package

```

Probably this advice is a little late since you have already upgraded...

Andrew

---

### Post by beanco on 2009-08-10
Andrew,

Yeah, I too would have gone that way but it was not me that did it and I trusted the IT guy... he did run checks on several applications to make sure they were running and fixed any problems...

I forgot to tell him to check vlc... so that was my fault.

Robi

---

