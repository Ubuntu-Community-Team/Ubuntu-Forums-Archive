---
title: "DVDs will not play"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-01-14
I can not get any DVDs to play properly. I installed ubuntu-restricted-extras, Medibuntu, and VLC. But when I try and play a DVD all I can watch is everything leading up to the main menu. I can scroll trough the menu with no problems. The problems only start when I try and watch deleted scenes, extra content, or the main movie. I have attached a screen shot of what it looks like. 

What can I do to fix this? VLC works perfectly in Windows :-(

---

### Post by RichardLinx on 2009-01-14
Try installing 'ogle'. It's available in synaptic.

---

### Post by Dr Small on 2009-01-14
Do you have libdvdcss installed? Looks like it can't decrypt it.

---

### Post by RichardLinx on 2009-01-14
Have you tried playing any other DVD's? It's strange that It's able to load the menu but unable to play the DVD it's self. It's also possible that you need to install some additional libraries (though I can't remember which ones specifically). I think It was something along the lines of "libdvdcss". You should also try installing kaffeine - It's quite a reliable video player, I've had more luck with kaffeine then I've had with VLC for Linux.

EDIT: Hah! Dr Smalls reply just confirmed that I did remember correctly, It was "libdvdcss". You know for someone that hasn't had any sleep I think I did pretty well. :)

---

### Post by Twitch6000 on 2009-01-14
VLC just needs libdvdcss and the other dvd codecs installed so it can play dvd's properly. 

Just go to the package manager and look for libdvdcss or in the terminal type sudo apt-get install libdvdcss

---

### Post by slughappy1 on 2009-01-14
Yes libdvdcss2 is installed. Yes I have tried multiple DVDs with the same exact problem. I have tried: Totem, VLC, gxine, MPlayer, and now OGLE. All have the same problem of being able to see the menu perfectly, but not the actual movie. Gxine and OGLE actually crashed when the movie was loaded.

---

### Post by kansasnoob on 2009-01-14
> **slughappy1 said:**
> I can not get any DVDs to play properly. I installed ubuntu-restricted-extras, Medibuntu, and VLC. But when I try and play a DVD all I can watch is everything leading up to the main menu. I can scroll trough the menu with no problems. The problems only start when I try and watch deleted scenes, extra content, or the main movie. I have attached a screen shot of what it looks like. 

What can I do to fix this? VLC works perfectly in Windows :-(

Since you already have the Medibuntu repo installed run from terminal:

```
sudo apt-get install libdvdcss2
```

But still, I've found Xine to be far superior at DVD quality. I use Totem Xine. Go to System > Admin > Synaptic and search for totem:

[ATTACH]99816[/ATTACH]

---

### Post by kansasnoob on 2009-01-14
> **slughappy1 said:**
> Yes libdvdcss2 is installed. Yes I have tried multiple DVDs with the same exact problem. I have tried: Totem, VLC, gxine, MPlayer, and now OGLE. All have the same problem of being able to see the menu perfectly, but not the actual movie. Gxine and OGLE actually crashed when the movie was loaded.

Try something simple like:

```
sudo apt-get -f install
```

to resolve unmet dependencies.

---

### Post by RichardLinx on 2009-01-14
It could even be old "junk" packages causing the problem, try running the following:

```
sudo apt-get autoclean
```

```
sudo apt-get autoremove
```

---

### Post by slughappy1 on 2009-01-14
```
sudo apt-get -f install
``` does nothing. I installed totem-xine, but I don't see another application in the Sound & Video tab. Is it an add-on to Totem?

---

### Post by slughappy1 on 2009-01-14
I run autoclean and autoremove every so often. But I ran them again just in case, and there was nothing for them to do.

---

### Post by peakshysteria on 2009-01-14
How did you install [Medibuntu]("https://help.ubuntu.com/community/Medibuntu")?

---

### Post by kansasnoob on 2009-01-14
> **slughappy1 said:**
> ```
sudo apt-get -f install
``` does nothing. I installed totem-xine, but I don't see another application in the Sound & Video tab. Is it an add-on to Totem?

Yes. It just allows Xine to play under Totem. You'll notice from my screen shot that I also have the totem-plugins-extra package installed.

Thinking of two other things I do (especially since its a menu thing)!

#1. Go to synaptic and search "sun-java6". I install all sun-java6-* except for sun-java6-doc and sun-java6-source!

#2. I go all out on "free" gstreamer by running from terminal:

```
sudo apt-get install --reinstall gstreamer*
```

---

### Post by FireflyCalvin on 2009-01-14
> **slughappy1 said:**
> ```
sudo apt-get -f install
``` does nothing. I installed totem-xine, but I don't see another application in the Sound & Video tab. Is it an add-on to Totem?

**Comprehensive Multimedia & Video Howto from Ubuntu-Freak**

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I thought this guide was helpful in validating my media setup.

---

### Post by RichardLinx on 2009-01-14
Hmm.. My guess is that a dependancy didn't install correctly and It's causing these issues. If It were me I would just completely remove all the related codecs and then reinstall them. 
I'm guessing you've probably also installed a bunch of media players you don't even plan on using... It might be a bit troublesome but if you don't mind uninstalling and reinstalling your media codecs It could be the easiest fix.

---

### Post by Mariane on 2009-01-15
I had the same thing with vlc when I tried to do 
"open file". I never got anywhere. Then I realised 
there was an "open disk" option and this one works 
much better. It launches the movie, I can access 
subtitles menus before, etc. 

So my advice would be to try all possible options 
on a media player before giving up on it. Also, there 
are two places you can find the disk, one in /dev and 
one wherever it's been mounted. Picking one instead 
of the other might make a difference. 

I'm no expert, I just fiddle around. 

Mariane

---

