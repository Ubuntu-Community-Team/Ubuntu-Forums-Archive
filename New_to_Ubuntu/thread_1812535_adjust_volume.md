---
title: "adjust volume"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by Robicika on 2011-07-26
Hello!  Can somebody help me please?  I dont know how to adjust volume in xubuntu 11,04?  Thanks in advance!

---

### Post by ajgreeny on 2011-07-26
Do you not have a volume icon in your panel?  It is normally there.

If not in your system, you may need to add it, which I think you can do with a right click on the panel and choosing panel properties.  I'm not on xubuntu at the moment and can't remember the details, but that's a good place to start.

---

### Post by Robicika on 2011-07-26
There is not on the panel, so I'm confused, I tried to add it, but it isn't on the list, so I dont know what to do! :(

---

### Post by mikejonesey on 2011-07-26
as a temp fix till you get this sorted;

```
alsamixer
```

---

### Post by ajgreeny on 2011-07-26
> **Robicika said:**
> There is not on the panel, so I'm confused, I tried to add it, but it isn't on the list, so I dont know what to do! :(
Next time I boot to xubuntu I'll look into it and report back, though I suspect others will already have answered.

Actually, I am wondering if the volume control is included as part of another applet as it is in gnome, eg notification-area or indicator-applet.  I just can't remember; sorry.

Worth a quick look though!

---

### Post by mikejonesey on 2011-07-26
> **ajgreeny said:**
> Next time I boot to xubuntu I'll look into it and report back, though I suspect others will already have answered.

Actually, I am wondering if the volume control is included as part of another applet as it is in gnome, eg notification-area or indicator-applet.  I just can't remember; sorry.

Worth a quick look though!

in xubuntu doesnt the sound control default to the icon tray at the bottom? (try drag n drop to systray bar)...

---

### Post by Robicika on 2011-07-27
The alsamixer works, but can somebody help me to put it on the panel? I had gnome but it was too slow, so I installed xubuntu-desktop, now it work fine... but the sound volume adjusting missing.

---

### Post by XubuRoxMySox on 2011-07-27
Right-click on the panel, choose **Add New Item**, and select **Mixer** from the list. 

-Robin

---

### Post by Robicika on 2011-07-27
There is no mixer on the list.

---

### Post by ajgreeny on 2011-07-27
OK, I booted into xubuntu 11.04 and found that the volume control icon is part of the **indicator-plugin** which includes other icons as well, eg message icon.

So right click on an empty part of the panel, either top or bottom, go to panel properties/preferences (I have now booted back into ubuntu and can't remember how it is described) then to Add to panel and in the list you'll the indicator applet.

Done!

---

### Post by Robicika on 2011-07-28
The indicator-plugin was not installed at me, so I installed it, now it is on the list, but when I choose it some icons on the panel (like KNemo) disappear, and nothing else, the panel is the same only without knemo, I tried to restart the X-session, then the computer, nothing...

---

### Post by XubuRoxMySox on 2011-07-28
I'm so sorry for all the trouble you're having!

For *me* the problem turned out to be PulseAudio (the default sound server in Xubuntu since Lucid). Removing PulseAudio and replacing it with good ol' tried-and-proven ALSA fixed all the sound issues on my 'puter.

I don't know if you've reached the point where this is necessary, but I offer it for others as well who are having persistent sound issues with Xubu. Purge PulseAudio from your 'puter and replace it with ALSA. How I did it: Clicky [here]("http://robinsrantsandraves.wordpress.com/2011/07/27/replacing-pulseaudio-with-alsa-in-ubuntu/")!

-Robin

---

