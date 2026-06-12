---
title: "No mp3 playback"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by adityak28 on 2010-05-16
Hi,
I'm new to linux and I've installed kubuntu 10.04 recently. I'm  following the guide at [http://kubuntuguide.org/Lucid](http://kubuntuguide.org/Lucid) to set-up the system.  I've installed the kubuntu-restricted-extras package however I do not  get any sound while playing mp3s. The sound system is working as I get  the kde tune when I start up. I have tried playing mp3s in amarok,  audacious, kaffeine and vlc. None of them work. 

I opened system settings -> multimedia. It shows four devices and  only the one which says 'ALC883(analog)' works in all categories  (notifications, music, video, etc etc) when I click test. However  sometimes I get a notification saying that the device doesn't work. I'm  confused!

Another thing I noticed was that the mp3s play when Dolphin shows a  preview of the file when it is selected. I mean that there is a preview  part in the right hand part of the window. When I press play there, the  mp3s play. But there is no sound when I play movies and mp3s in amarok,  audacious, vlc or kaffeine

The motherboard I'm using is Gigabyte M61PME-S2P. Its an nForce 430  motherboard with integrated graphics and sound.

---

### Post by kellemes on 2010-05-16
Open the Terminal, and execute the following command:
```
sudo apt-get install kubuntu-restricted-extras
```

Or open KPackageKit from the system-menu and search and install kubuntu-restricted-extras.

---

