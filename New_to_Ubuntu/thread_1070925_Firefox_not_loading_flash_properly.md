---
title: "Firefox not loading flash properly"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Glurf on 2009-02-15
Firefox won't load flash videos anymore. Sometimes it won't load the flash at all, a grey box will be in place of where it should be, sometimes it will stop working in the middle of the video, but in the last few weeks, I've had to use Opera to watch any videos. I don't want to switch to Opera, so does anyone know whats wrong with my Firefox? I haven't messed with any settings, and I'm using the Adobe flash player, not Gnash or any other forms. Thanks in advance for any help.

---

### Post by kansasnoob on 2009-02-15
> **Glurf said:**
> Firefox won't load flash videos anymore. Sometimes it won't load the flash at all, a grey box will be in place of where it should be, sometimes it will stop working in the middle of the video, but in the last few weeks, I've had to use Opera to watch any videos. I don't want to switch to Opera, so does anyone know whats wrong with my Firefox? I haven't messed with any settings, and I'm using the Adobe flash player, not Gnash or any other forms. Thanks in advance for any help.

So, Flash did work well in Firefox at one time?

What version of Ubuntu are you using? (ie: 8.04, 8.10)

What version of Firefox? (ie: 3.06)

What version of Flash? You can see by going to Tools > Add-ons > Plugins in the Firefox toolbar.

Consider "Extensions"! Quite often older extensions don't work properly with Firefox updates which is one reason I use the Mozilla build of Firefox by installing Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

Using Ubuntuzilla it really is easy. Just download Ubuntuzilla to desktop (or wherever) and then double click the icon/folder. Ubuntuzilla should then install to synaptic.

Then go to terminal and run:

```
ubuntuzilla.py -a install -p firefox

```

After answering a few simple questions you should have the true Mozilla build of Firefox which will notify of updates to Firefox and most Extensions.

---

