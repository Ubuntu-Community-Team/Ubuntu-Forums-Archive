---
title: "No sound from adobe flash player"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by tonsil on 2010-05-27
I've just installed kubuntu and I have sound working. I installed restricted extras and they work fine too, however I can't listen to a radio station through firefox which requires adobe flash. It thinks it is playing but no sound comes out. I've uninstalled flashplugin-installer and installed adobe flash manually, but nothing changed. It is streaming, and apparently video is working too, but no sound. Please help!

---

### Post by lovinglinux on 2010-05-27
Have you checked if the PCM volume slider is all the way up?

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

Also, go to "System Settings >> Computer Administration >> Multimedia" and move Pulseaudio to the top of all lists there. If you don't have Pulseaudio, then install it. to do that open a terminal and run the following command:

```
sudo apt-get install pulseaudio
```

---

### Post by lkraemer on 2010-05-27
Try going to the Top Right Menu then Left Click on
SPEAKER -> SOUND PREFERENCES -> APPLICATIONS and slide the volume UP
for that Application.

lk

---

### Post by lovinglinux on 2010-05-27
> **lkraemer said:**
> Try going to the Top Right Menu then Left Click on
SPEAKER -> SOUND PREFERENCES -> APPLICATIONS and slide the volume UP
for that Application.

lk

Please notice the thread prefix, it's [COLOR="DeepSkyBlue"]**[kubuntu]**[/COLOR]. So the OP is not using Gnome.

---

### Post by Maxquig on 2010-05-27
I had the same problem. The PCM Slider was all the way down.  The default setting should be half way up or all the way up.

---

### Post by tonsil on 2010-06-02
Thanks for those suggestions. I installed google chrome, thinking maybe it's a problem with Firefox. Chrome started playing it without problems. When I tried it with Firefox again it was playing it too. So I really don't know what to say or what the problem was, but I am happy it's working :)

---

