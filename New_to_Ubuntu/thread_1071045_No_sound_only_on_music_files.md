---
title: "No sound only on music files"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by twitch213 on 2009-02-15
So i have had ubuntu for awhile now and i am fairly please with it as a whole but i do have a single problem. My music in my songbird library wont play. My movies work, mt photos work but music will not play from any music player on my computer. I have sound for videos on youtube and music from myspace works. But anything on my computer will not play at all.

---

### Post by twitch213 on 2009-02-15
Does anyone know what is wrong?

---

### Post by neu2buntu on 2009-02-15
list what type of audio you have tried eg  .ogg .mp3 .wav etc or cd in tray. it it possible that you may need to install restricted codecs

---

### Post by twitch213 on 2009-02-15
Well lets start with the one that bugs me the most. .mp3

---

### Post by Crafty Kisses on 2009-02-15
Did you update recently?

---

### Post by twitch213 on 2009-02-15
Fully updated. :confused:

---

### Post by neu2buntu on 2009-02-15
right goto > system > administrtaion > software sources > ubuntu software tab .. and tick all boxes on
except cdrom next open terminal > applications > terminal and type in ```
sudo apt-get update
``` and then ```
sudo apt-get install ubuntu-restricted-extras
``` this will pull in .mp3 support . not sure if u have to reboot after this .try playing an mp3 now and if it wont play reboot and try again

---

### Post by twitch213 on 2009-02-15
It didnt work

---

### Post by TCSnyder on 2009-02-15
have you tried an .ogg yet?

---

### Post by twitch213 on 2009-02-16
.ogg?

---

### Post by jeterfan1 on 2009-02-16
it's an open audio format -- there's a sample .ogg file in the Examples folder on the desktop. will it play at all?

---

### Post by jeterfan1 on 2009-02-16
sorry, in the Examples folder in your Home folder. there's some .ogg video and audio files which came pre-loaded in there

---

### Post by neu2buntu on 2009-02-16
did the ubuntu-restricted -extras package download and install ref "it didnt work" or if not what was the error in the terminal when you ran the command . this really should work it always has for me ...   i think you may also have to goto > system > admin > software sources and do this also (as well as my first instruction)... i will start over again 
[1] open tab "ubuntu software" tick all but not cdrom
[2] open tab "third party software" tick all/any
[3] open tab "updates" and tick all4 boxes for updates and at bottom "release upgrade" choose "normal releases"
[4] open > applications > terminal . and type these next 2 commands followed by your password and enter ```
sudo apt-get update
``` and then ```
sudo apt-get install ubuntu-restricted-extras
```   hopefully this will do it

---

