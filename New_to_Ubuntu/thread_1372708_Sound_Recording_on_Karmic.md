---
title: "Sound Recording on Karmic"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by danroduw06 on 2010-01-04
I try to avoid posting questions in these forums because I can usually find the solution to my problem by just browsing. However, since I downloaded Karmic Koala on my laptop I have lost the ability to record audio.I can't record audio along with my built in webcam at all. On the last version of Ubuntu I did not have this problem. I have searched for the solution everywhere to no avail. Can anyone help?

---

### Post by dzon65 on 2010-01-05
Which audio are you trying to record?If it's streaming audio there are several options.The easiest one IMO is rhythmbox.Add the record plugin.It's very easy to record then,just rightclick on the item.
You'll find more plugins here,I've installed the equalizer as well.
[http://live.gnome.org/RhythmboxPlugins/ThirdParty](http://live.gnome.org/RhythmboxPlugins/ThirdParty)

---

### Post by themusicalduck on 2010-01-05
This might seem a bit obvious, but have you checked the pulseaudio settings? If you right click on the volume control at the top right and click preferences, there is a tab called input. I think the default might actually be for input to be disabled. At least if you look there you can see if the input is detected, enable it or mess with the levels a little to see if you can get anything to come through.

---

### Post by Jenkins1 on 2010-01-05
If you go Applications > Acessoires > terminal 
and type alsamixer
then check to see if the mic sliders are turned up. you navigate between each slider with the left and right arrows and change the slider with the up and down arrows.

---

