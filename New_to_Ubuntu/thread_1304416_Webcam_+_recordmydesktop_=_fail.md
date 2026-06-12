---
title: "Webcam + recordmydesktop = fail"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Bölvaður on 2009-10-29
( Im guessing the problem is with gstreamer being clogged by audio recording so the videofeed from the webcam that also uses gstreamer doesnt work)

I am trying to record a how-to and also have a life video of my self in the lower corner of the screen via webcam.

The problem is that Cheese (the only program I have been able to make the webcam show up in) uses gstreamer to show the video.
Showing webcam on it's own is no problem.

I also record my desktop via gtk-recordMyDesktop which works perfectly on it's own.

But combined it doesn't work. When I have the webcam showing me on screen there are big problems with audio. I am unable to record sound like normally (pulse). After a test I saw that Audiocity was unable to start recording any sound for about 20 seconds and then suddenly started. But with gtk-recordMyDesktop there is no indication of anything being wrong except that the video will not render and recordMyDesktop will stay in 100% cpu until killed.

Also if I have any program that would record audio open I am unable to get video feed from my webcam.
The camera is detected and Cheese does not complain about not being able to connect like if it would be unplugged.

---

