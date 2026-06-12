---
title: "Help!My laptop cant play .avi files"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by numerouno.zubair on 2009-07-16
im just a newbie for ubuntu and my laptop cant play .avi files.
can anyone help me with his.
thank you

---

### Post by allenbradley on 2009-07-16
Have you installed the non-free codecs? You can get them from the [medibuntu]("http://www.medibuntu.org/repository.php") webpage. The instructions are on the page, so post back if you have further doubts.

---

### Post by Finalfantasykid on 2009-07-16
I'm not sure if .avi files were included in this, but I'm pretty certain that I can view .avi files, so this is probably what made it work...

```
sudo apt-get install ubuntu-restricted-extras
```

Type that in the terminal and you should be able to play all sorts of extra media files.  If you already have this, then maybe search in the synaptic package manager for .avi

---

### Post by csabo2 on 2009-07-16
another option, use apt to install vlc. itll grab everything you need.

---

### Post by Elep.Repu on 2009-07-16
> **csabo2 said:**
> another option, use apt to install vlc. itll grab everything you need.

Yeah. use:
```
sudo apt-get install vlc
```
in terminal.

---

### Post by ~sHyLoCk~ on 2009-07-16
```
sudo apt-get install mplayer
sudo apt-get install smplayer
```

---

### Post by binbash on 2009-07-16
sudo apt-get install vlc

---

### Post by vinutux on 2009-07-16
Install Gstreamer bad and ugly plugins

**Alt+F2** Type **synaptic** or **[COLOR="DarkGreen"]Sysytem>Administration>synaptic pakage manger[/COLOR]**

Then search and mark these plugins for installation

[B][COLOR="Red"]gstreamer0.10-plugins-bad

gstreamer0.10-plugins-bad-multiverse

gstreamer0.10-plugins-ugly

gstreamer0.10-plugins-ugly-multiverse
[/COLOR][/B]

.

---

### Post by carml on 2009-07-16
> **vinutux said:**
> Install Gstreamer bad and ugly plugins

**Alt+F2** Type **synaptic** or **[COLOR="DarkGreen"]Sysytem>Administration>synaptic pakage manger[/COLOR]**

Then search and mark these plugins for installation

[B][COLOR="Red"]gstreamer0.10-plugins-bad

gstreamer0.10-plugins-bad-multiverse

gstreamer0.10-plugins-ugly

gstreamer0.10-plugins-ugly-multiverse
[/COLOR][/B]

.

+1 Then you can choose whatever player you want.

---

### Post by t0p on 2009-07-16
> **vinutux said:**
> Install Gstreamer bad and ugly plugins

**Alt+F2** Type **synaptic** or **[COLOR="DarkGreen"]Sysytem>Administration>synaptic pakage manger[/COLOR]**

Then search and mark these plugins for installation

[B][COLOR="Red"]gstreamer0.10-plugins-bad

gstreamer0.10-plugins-bad-multiverse

gstreamer0.10-plugins-ugly

gstreamer0.10-plugins-ugly-multiverse
[/COLOR][/B]

.

That's certainly one way of doing it. Alternatively you could just do 

```
sudo apt-get install ubuntu-restricted-extras
```

A lot less typing than what you suggest, and it will install everything you listed plus a whole lot more. Still, you probably know best, eh?

---

### Post by scrooge_74 on 2009-07-16
It is easier is you just follow the Multimedia guide here in the forum.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by 3rdalbum on 2009-07-16
Note: AVI is not a video format, it's just a "container" format. In other words, AVI just sets the format by which some video and audio tracks can be included in the same file - it is not concerned with the compressor used in those video and audio tracks.

So an AVI file could contain h.264 video, or VC1 video, or DivX video, etc.

Out of the box, Ubuntu can read AVI files, but if you don't have the actual video decompressor needed then you would need to obtain it. If your AVI file contained an Ogg Theora video track and a PCM Wave audio track, then Ubuntu would be able to play it out-of-the-box.

If you are still having trouble with your files, please include details of what video and audio codecs are used in the files.

---

### Post by vinutux on 2009-07-16
> **3rdalbum said:**
> Note: AVI is not a video format, it's just a "container" format. In other words, AVI just sets the format by which some video and audio tracks can be included in the same file - it is not concerned with the compressor used in those video and audio tracks.

So an AVI file could contain h.264 video, or VC1 video, or DivX video, etc.

Out of the box, Ubuntu can read AVI files, but if you don't have the actual video decompressor needed then you would need to obtain it. If your AVI file contained an Ogg Theora video track and a PCM Wave audio track, then Ubuntu would be able to play it out-of-the-box.

If you are still having trouble with your files, please include details of what video and audio codecs are used in the files.


yeh....but newbies...don't want much details......anyway  your appreciate your effort.... good work and thanks 4 info

---

