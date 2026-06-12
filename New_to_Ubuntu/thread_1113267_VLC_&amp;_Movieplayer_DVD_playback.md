---
title: "VLC &amp; Movieplayer DVD playback"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by funkdified on 2009-04-01
Hey guys, when I try to open a DVD in VLC I get the sound track from the main menu sequence repeating and no video. When I try to open a DVD in movieplayer i get the window opening to the DVD aspect ratio with a black screen then giving up after a few milliseconds and ceasing the operation. I should note that I have all of the gstreamer codecs added using add/remove. Also, no problems playing DVDs using VLC when I boot into XP.

Thanks ahead!

---

### Post by kansasnoob on 2009-04-01
Have you installed the Medibuntu repo and libdvdcss2?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

NOTE: Don't forget the GPG key.

Feel free to ask for more specific instructions if needed.

---

### Post by philinux on 2009-04-01
Click the medibuntu link below.

---

### Post by kansasnoob on 2009-04-01
BTW I prefer DVD playback in Totem Xine which is not installed by default so go to terminal and run:

```
sudo apt-get install totem-xine
```

Then again you may prefer VLC or some version of mplayer. Choices, choices, so many choices!

---

### Post by funkdified on 2009-04-02
aww.. cool thanks guys.. i will give all this a try in the morning. these forums r amazing.

---

### Post by funkdified on 2009-04-03
i am running the newest version of intrepid ... i ran the following in the order listed:

```


sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

 sudo apt-get install libdvdcss2


```

still the same exact issues described in my original post! any clues?

---

