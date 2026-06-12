---
title: "Problem with .WMV audio..."
date: 2009-04-14
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-04-14
I'm trying to watch back a windows Media video file but I dont get any sound from mplayer and totem reports that it cant find a suitable audio codec and I get the following error from VLC

------------------------------------------------------------------------------------------------------------------------------
[COLOR="Red"]No suitable decoder module:[/COLOR]
VLC does not support the audio or video format "wmap". Unfortunately there is no way for you to fix this.
------------------------------------------------------------------------------------------------------------------------------

I've googled the problem and I found [this thread]("http://88.191.250.119/viewtopic.php?f=14&t=51471&start=0") on the VLC Official forums which mentions about DMO or Direct Media Object 

[http://wiki.videolan.org/Dmo](http://wiki.videolan.org/Dmo)

it mentions how to get this working under Linux but it doesen't really go into any great details like what it means by loader switch?

---

### Post by steve101101 on 2009-04-14
try this thread .. [http://ubuntuforums.org/showthread.php?t=537065](http://ubuntuforums.org/showthread.php?t=537065)

---

### Post by kamitsukai on 2009-04-14
> **steve101101 said:**
> try this thread .. [http://ubuntuforums.org/showthread.php?t=537065](http://ubuntuforums.org/showthread.php?t=537065)

I have the win32 codecs installed...

---

### Post by steve101101 on 2009-04-14
try this ... [http://ubuntuforums.org/showthread.php?t=958265](http://ubuntuforums.org/showthread.php?t=958265)

---

### Post by kamitsukai on 2009-04-14
I'm using ubuntu 64 bit could that be causing the problem? and I though I had win32 codecs but I tried the command 

"sudo apt-get install w32codecs" and I get the following error:

```
carl@carl-desktop:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
carl@carl-desktop:~$


```

---

### Post by Elfy on 2009-04-14
```
sudo apt-get install w64codecs
```

---

### Post by kamitsukai on 2009-04-14
> **forestpixie said:**
> ```
sudo apt-get install w64codecs
```

Just tried that but the audio still doesent work I assume this is because win64 codec's package doesn't contain the same as win32?

---

### Post by kamitsukai on 2009-04-14
So the obvious question now is how do I install win32 codec's in Ubuntu 64 bit? and why do I have to mess around like this? it's not this annoying in Ubuntu 32 bit!!!!!!!

---

