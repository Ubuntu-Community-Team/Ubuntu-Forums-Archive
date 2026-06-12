---
title: "view wmv files in ubuntu 9.04"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by i_karpas on 2009-11-28
I'm new to Linux, I've added applications to the 9.04 version but
I need  help, I have installed vlc   using these commands
       sudo apt-get install non-free-codecs
       sudo apt-get install libdvdcss2 gxine libxine1-ffmpeg vlc mplayer mencoder 
 but when I try 2 open a .wmv file by downloading the file the only choice I get is Movie Player,  I have tried to change this by opening Properties-->Custom
but then I don't know how to designate the vlc player,I have tried a search of the system(for vlc) & couldn't find it
    please help i_karpas

---

### Post by ankspo71 on 2009-11-28
Hi,

when selecting your player, browsing to and selecting /usr/bin/vlc should do the trick.

Also I think installing mozilla-plugin-vlc should help you view the files in VLC without downloading them first. I'm not certain though because it has been ages since I last viewed a .wmv file.
```
sudo apt-get install mozilla-plugin-vlc 
```

James

---

### Post by i_karpas on 2009-11-28
> **ankspo71 said:**
> Hi,

when selecting your player, browsing to and selecting /usr/bin/vlc should do the trick.

Also I think installing mozilla-plugin-vlc should help you view the files in VLC without downloading them first. I'm not certain though because it has been ages since I last viewed a .wmv file.
```
sudo apt-get install mozilla-plugin-vlc 
```

James
Hi  James
I carried out the command to load vlc, and found the directory
when asked for an application I entered ** vlc**
all that happens is that a small screen  (black) opens for about a second and nothing else
by the way the same happens with the app Movie Player
   i_karpas

---

### Post by Virtual Liberty on 2009-11-28
```
sudo apt-get install w32codecs gecko-mediaplayer

```

Restart your browser and let us know whether it solved your problem or not.

---

### Post by i_karpas on 2009-11-29
> **Virtual Liberty said:**
> ```
sudo apt-get install w32codecs gecko-mediaplayer

```

Restart your browser and let us know whether it solved your problem or not.
Hi Virtual Liberty
I tried the command, but I don't know how to designate geko as the application for opening the file, so far all the options I've tried (Movie Player, vlc) just open a  black screen but play nothing

---

