---
title: "Graphics messed up"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by Cmac90 on 2010-05-11
I installed Ubuntu 10.04 64-bit several days ago and it has been working great, speed has been amazing, and everything has been working rock solid till about 5 mins ago. I installed an adobe flash from the ubuntu software center so i could view youtube videos. it installed and it played the videos perfectly. I shut down the computer to go somewhere else and when i turned my computer back on it tells me something is wrong with my graphics card now and that it needed to enter into low graphics mode. My resolution was typically 1440x900 in a 16:10 ratio. now i am getting a 1024x768 in a 4:3 ratio. Did that flash player mess things up?

---

### Post by KinKiac on 2010-05-11
Its possible the flash player messed something up.  Im assuming anyway, im not exactly a pro myself but id start with removing flash and then rebooting.  See if that fixes your video.  You could also try removing a reloading your video drivers(before or after removing flash, depending on the results).  You also might have better luck installing flash from the adobe website, might be an updated version there that hasnt made it to the repos yet, Im not sure, Ive always just downloaded from Adobe and havent had a problem, well other than the known issues with flash on linux anyway.

---

### Post by Cmac90 on 2010-05-11
the reason why i went to the software center was because adobe only offers the flash player for 32 bit and since i was running 64 bit it wouldnt work. but ill give it a try and see how it goes with removing and reinstalling

---

### Post by Cmac90 on 2010-05-11
that worked, if you are using 64 bit 10.04 dont install adobe flash from software center

---

### Post by GSF1200S on 2010-05-11
> **Cmac90 said:**
> that worked, if you are using 64 bit 10.04 dont install adobe flash from software center

Wow- I don't know how thats possible. Maybe someone can explain to me HOW installing flash has anything to do with video drivers? Are you sure that was the issue? Perhaps an update or something triggered a failure of your video drivers?

Anyways, you can still watch flash on your computer without that package (and even though ill be discussing the .mozilla folder, chrome will work too because it looks there).

Go here:
[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)
and download the plugin.

After you get it downloaded, open the tarball you downloaded with the archive manager (should be able to double click on the tarball to do so). Then, extract the libflashplayer.so to your home folder. Then, right click>cut and go to your .mozilla folder (/home/username/.mozilla  make sure to enable "Show Hidden Files" in the view menu). Create a folder inside .mozilla called 'plugins' and place the the libflashplayer.so in that folder. So, eventually libflashplayer.so will have a final address of:
```
/home/username/.mozilla/plugins/libflashplayer.so
```
Open firefox and flash will work fine :)

---

