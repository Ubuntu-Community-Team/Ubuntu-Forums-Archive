---
title: "dvds won't play"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by jalehtor on 2008-12-22
Having no luck playing dvds on Totem/Intrepid. Installed libdvdread3 package and libdvdcss2 library. I used the instructions on this forum, and the Medibuntu rep. I put a dvd in, turn on Totem, the player on the computer makes some sounds then quiets down, and the play button on Totem does not wake up. Do I need to do something to activate Totem? I'm sure I'm missing something :confused:

---

### Post by SlidingHorn on 2008-12-22
> **jalehtor said:**
> Having no luck playing dvds on Totem/Intrepid. Installed libdvdread3 package and libdvdcss2 library. I used the instructions on this forum, and the Medibuntu rep. I put a dvd in, turn on Totem, the player on the computer makes some sounds then quiets down, and the play button on Totem does not wake up. Do I need to do something to activate Totem? I'm sure I'm missing something :confused:

do you have the restricted extras installed?

sudo apt-get install ubuntu-restricted-extras

---

### Post by igknighted on 2008-12-22
> **jalehtor said:**
> Having no luck playing dvds on Totem/Intrepid. Installed libdvdread3 package and libdvdcss2 library. I used the instructions on this forum, and the Medibuntu rep. I put a dvd in, turn on Totem, the player on the computer makes some sounds then quiets down, and the play button on Totem does not wake up. Do I need to do something to activate Totem? I'm sure I'm missing something :confused:

Totem can be flaky... I would try using VLC (sudo apt-get install vlc) or mplayer (sudo apt-get install gnome-mplayer).  You can also make totem use the xine backend instead (sudo apt-get remove totem-gstreamer && sudo apt-get install totem-xine)

---

### Post by jalehtor on 2008-12-22
> **SlidingHorn said:**
> do you have the restricted extras installed?

sudo apt-get install ubuntu-restricted-extras

I'm in the process of doing that. The problem is that I'm now frozen on  Configuring sun-java6-jre. It wants me to read and OK the agreement, but when I press enter nothing happens. How do I OK this so that it keeps reloading? I am embarrassed to be asking this question :(

---

### Post by igknighted on 2008-12-22
> **jalehtor said:**
> I'm in the process of doing that. The problem is that I'm now frozen on  Configuring sun-java6-jre. It wants me to read and OK the agreement, but when I press enter nothing happens. How do I OK this so that it keeps reloading? I am embarrassed to be asking this question :(

Tab key lets you select the button, then enter to click it.

---

### Post by jalehtor on 2008-12-22
> **igknighted said:**
> Tab key lets you select the button, then enter to click it.

Thank you! It finished downloading, but still no dvd, either on totem or vlc. On vlc I get this message:
Playback failure:
DVDRead could not open the disk "/dev/dvd".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/dvd'. Check the log for details.


er...this is very, very embarrassing...is it possible that I wouldn't notice the fact that I don't have a dvd player installed on my swap shop computer...yes it is. I missed something as obvious as that. Can we forget the existence of this shameful thread, please? On the plus side...there is no plus side to this.

---

### Post by bumanie on 2008-12-22
Go to the medibuntu site and follow the instructions re installing multi-media codecs - it's basically copy and paste into terminal, hitting enter between each command. Look [here]("https://help.ubuntu.com/community/Medibuntu"). Don't forget the pgp key.

---

