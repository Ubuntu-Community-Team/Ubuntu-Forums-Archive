---
title: "Music and Video players"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by mllelinotte on 2009-03-26
i am completely new to Ubuntu and know absolutely nothing.
I have been messing with it for about 2 days. Right now all i want to do is get a music player and a video player to work. the players that come already installed do not work despite the fact that they retrieved the necessary codecs and installed them.   i have read forums followed links, and i cant get anything to work. Can anyone tell me how to get Ubuntu to play music and video files?   Thanks.

---

### Post by billgoldberg on 2009-03-26
Go to applications, accessories, terminal and enter (copy/paste) this command:

```
sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

It will ask for you password, just type it blindly (you won't see what or how many digits you type) and press enter.

During installing, a EULA for Java will pop up, press tab and enter to get rid of it.

This should install everything you need on the audio and video front.

Also know there are other video and audio players available.

Another good audio player is "banshee" and a good video player is "vlc".

Both can be install for Applications, Add/remove (make sure to select "all available sources" from the drop-down menu on top).

Hope this helped.

---

### Post by clive littlewood on 2009-03-26
Hi

Welcome to Ubuntu and the forums.

As you now realise Ubuntu IS different from Windoze.

An excellent guide to get you started is the free pocket guide at:

 [http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

Hope that helps, if you need any further help the please ask  :)

Clive

---

### Post by feelshift on 2009-03-26
Have you added [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") to your repository?
If not, assuming that you use the latest version of Ubuntu (8.10 - to find out go to System -> About Ubuntu) type this in terminal (Applications -> Accesories -> Terminal)
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
``` Type your password when requested.
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
``` Press 'y' when requested to install the key.
```
sudo apt-get install ubuntu-restricted-extras vlc
```
The latest command should install all you need for audio & video playback. If you want to install more programs System -> Administration -> Synaptic Package Manager.

---

### Post by mllelinotte on 2009-03-27
Thank you so much! music is working well. 
I did install the VLC player, but it is not working. When i import a video the screen opens for a split second then VLC closes itself. i have tried to play regular DVD movies, mpg and wmv files so far. All with the same results. the Ubuntu Movie Player does the same thing. Any idea what i need to get them running?
thanks again!

---

### Post by SunnyRabbiera on 2009-03-27
are you running desktop effects?
I do know some cards dont render video properly with desktop effects.

---

### Post by mllelinotte on 2009-03-28
the Desktop effects are set on normal. 
Is there something i need to do? I am new to all this so not sure how to proceed.

---

### Post by Zalbor on 2009-03-28
Try opening a terminal (Applications>Accessories(I think)>Terminal) and type "vlc" into it.
Try opening a video file again, and see if any output appears in the terminal. Paste it here, it might help see what's happening.

---

### Post by mllelinotte on 2009-03-28
i did as you said. Here is what it said in Terminal when the VLC player closed itself:

QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  83
  Current serial number in output stream:  84

---

### Post by ubumania on 2009-03-28
I don't know about that output you posted but, as was said above, it sounds like the desktop effects. I had the same sort of thing happen and got around it by disabling the widget layer in ccsm. Try running vlc with desktop effects off and if it works ok... .

---

### Post by SunnyRabbiera on 2009-03-28
Indeed, I learned from others about the video card issues.
Do you have a special video card such as nvidia or ATI?

---

### Post by zachthejones on 2009-03-28
make sure you've installed the codecs to play commercial DVDs. I did a blog on it [here]("http://linux.zachjones.net/?p=103").

---

### Post by mllelinotte on 2009-03-29
Thanks. turning off desk effects worked!

---

