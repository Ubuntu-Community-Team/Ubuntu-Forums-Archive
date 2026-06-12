---
title: "camerabin for cheese 3.0.0"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by astrob0t on 2011-05-29
[SIZE=2][COLOR=black]got this error when opening cheese 

One or more needed GStreamer elements are missing: camerabin,

 can [/COLOR][/SIZE][SIZE=2][COLOR=black]someone help me?[/COLOR][/SIZE]

---

### Post by jtarin on 2011-05-29
Try installing ```
sudo apt-get install libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev
```
and then
```
sudo apt-get install gstreamer-plugins-good gstreamer-plugins-bad gstreamer-plugins-bad-multiverse gstreamer-plugins-ugly gstreamer-plugins-ugly-multiverse
```

---

### Post by duke.tim on 2011-05-29
I would try installing ubuntu-restricted extras

```
sudo apt-get install ubuntu-restricted-extras
```

And if that didn't work gstreamer-ffmpeg 
```
 sudo apt-get install gstreamer0.10-ffmpeg

```

---

### Post by astrob0t on 2011-05-30
> **jtarin said:**
> Try installing ```
sudo apt-get install libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev
```and then
```
sudo apt-get install gstreamer-plugins-good gstreamer-plugins-bad gstreamer-plugins-bad-multiverse gstreamer-plugins-ugly gstreamer-plugins-ugly-multiverse
```

thanx for the reply.i tried out ur solution but my newly installed gnome3 session crashed and now it shows everything installed but still cheese app wont work.

> **duke.tim said:**
> I would try installing ubuntu-restricted extras

```
sudo apt-get install ubuntu-restricted-extras
```And if that didn't work gstreamer-ffmpeg 
```
 sudo apt-get install gstreamer0.10-ffmpeg

```

this wont work either

---

### Post by jtarin on 2011-05-30
> **aviatsit said:**
> thanx for the reply.i tried out ur solution but my newly installed gnome3 session crashed and now it shows everything installed but still cheese app wont work.



this wont work either[URL="http://www.linuxquestions.org/questions/debian-26/how-do-i-get-apt-get-to-completely-uninstall-a-package-237772/"]Then I would suggest removing the applications you installed if they are not helping your experience.
[/URL]

---

### Post by astrob0t on 2011-05-30
> **jtarin said:**
> [URL="http://www.linuxquestions.org/questions/debian-26/how-do-i-get-apt-get-to-completely-uninstall-a-package-237772/"]Then I would suggest removing the applications you installed if they are not helping your experience.
[/URL]
some more help to get cheese and my integrated camera working would have been appreciated..

thanks for the replies though..

---

### Post by jtarin on 2011-05-30
> **aviatsit said:**
> some more help to get cheese and my integrated camera working would have been appreciated..

thanks for the replies though..You made the decision to upgrade to 11.04. If you want to get this particular application running you have three choices that I can think of.Maybe someone else has something better to offer you:
1.downgrade 
2.Wait for the application to be updated for 11.04.
3.Contact the developers of Cheese and ask for help.

---

### Post by astrob0t on 2011-05-30
> **jtarin said:**
> You made the decision to upgrade to 11.04. If you want to get this particular application running you have three choices that I can think of.Maybe someone else has something better to offer you:
1.downgrade 
2.Wait for the application to be updated for 11.04.
3.Contact the developers of Cheese and ask for help.
sry for some misunderstanding..my apologies..i purged all the gstreamer libraries and installed again..now it works..
actually the camerabin plugin was in the gstreamer-plugin-bad category..
but as mentioned earlier, my system had crashed while installation and in the next session it showed all of them as installed.. so i couldn't figure it out .. so as per ur previous solution ,i purged and reinstalled successfully..now it works..

cheers mate!!

---

### Post by jtarin on 2011-05-30
> **aviatsit said:**
> sry for some misunderstanding..my apologies..i purged all the gstreamer libraries and installed again..now it works..
actually the camerabin plugin was in the gstreamer-plugin-bad category..
but as mentioned earlier, my system had crashed while installation and in the next session it showed all of them as installed.. so i couldn't figure it out .. so as per ur previous solution ,i purged and reinstalled successfully..now it works..

cheers mate!!Good !!

---

