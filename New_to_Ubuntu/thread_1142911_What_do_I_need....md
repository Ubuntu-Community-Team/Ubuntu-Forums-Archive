---
title: "What do I need..."
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Jancarel on 2009-04-29
Dear Ubuntu Friends,

What do I need to play this video:

[http://geschiedenis.vpro.nl/artikelen/16369422/](http://geschiedenis.vpro.nl/artikelen/16369422/)

(Click on the text that says "Kolibrie...")

With Windows (XP) this works fine. With Ubuntu the player opens and shows the first farme of the video. Ther is no way I can get this video to play. Do I need a special codec, or player...

Thank you for your help...

Jan

---

### Post by NESFreak on 2009-04-29
hi jan, first make sure you've got the w32codecs.
for a guide installing ALL codecs look here

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

tried the video myself and it just doesn't work in totem. You could copy the link and open it in another mediaplayer like for instance vlc. Or you could read part 2/5 of the link i gave you and replace your browsers mediaplayer.

NESFreak

---

### Post by kansasnoob on 2009-04-29
Install the Medibuntu repo:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I've had trouble with that, "Any Ubuntu Release and keyring" script so choose the proper Medibuntu for your release version and then be sure to install the GPG key!

Then **for 32 bit** run the following command from terminal:

```
sudo apt-get install libdvdcss2 w32codecs realplayer
```

For 64 bit run:

```
sudo apt-get install libdvdcss2 w64codecs realplayer
```

then restart Firefox.

---

