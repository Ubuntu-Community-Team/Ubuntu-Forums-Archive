---
title: "iPod Touch Help"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by NastyT23 on 2009-12-11
> **LuisGMarine said:**
> Hello,

Have you tried managing your ipod with other applications other than this ifuse?  If so try out banshee or rhythmbox.  If you still continue to have other pograms other than rhythmbox detect your ipod, try this:

Disconnect your ipod from the PC, open up terminal by going to **Applications > Accessories > Terminal ** once there type in this into the window 
```
killall -9 nautilus
```

Connect your iPod, wait about a minute then hit Alt + F2 and type in **nautilus** to start it up again.  Now your iPod should be recognisable by other apps other than rhythmbox.


I'm having the same issue and i tried what you said and still no luck, any suggestions. While plugged in it shows up as just a camera.
I need to access the file system to transfer an .ipa file to my iphone. it's a 1.4GB file and wirelessly just doesn't cut it (says it'll take about 11 hours) I don't have a strong wireless connection.

---

### Post by LuisGMarine on 2009-12-11
> **NastyT23 said:**
> I'm having the same issue and i tried what you said and still no luck, any suggestions. While plugged in it shows up as just a camera.
I need to access the file system to transfer an .ipa file to my iphone. it's a 1.4GB file and wirelessly just doesn't cut it (says it'll take about 11 hours) I don't have a strong wireless connection.

I would open up your own thread about this.  I currently have no idea where to go, but opening up your own thread would open up the issue to the whole community.

I can tell you that it might be something with the actual ipod not being supported, to the file system.  It could even be some of the settings Ubuntu is using to mount it.

---

