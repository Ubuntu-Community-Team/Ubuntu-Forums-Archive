---
title: "Plugins"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by Grandpapop on 2010-10-10
Sir,  When I go to a certain site on the internet I get a popup that says I need a plugin.  I hit the button to look for that plugin and it goes out and then it comes back and says it can't find a useable plugin.  A person on here told me to install:
ffmpeg
adobe-flashplugin
sun-java6-bin
sun-java6-jre
sun-java6-plugin
sun-java6-fonts

I installed all of them and I still get the same notice when I go to the site that I need a plugin and I hit the button and it comes back and says it can't find a useable plugin.  Anyone have any more ideas on what I can do.  Thanks  Grandpapop

---

### Post by madmax75 on 2010-10-10
> **Grandpapop said:**
> Sir,  When I go to a certain site on the internet I get a popup that says I need a plugin.  I hit the button to look for that plugin and it goes out and then it comes back and says it can't find a useable plugin.  A person on here told me to install:
ffmpeg
adobe-flashplugin
sun-java6-bin
sun-java6-jre
sun-java6-plugin
sun-java6-fonts

I installed all of them and I still get the same notice when I go to the site that I need a plugin and I hit the button and it comes back and says it can't find a useable plugin.  Anyone have any more ideas on what I can do.  Thanks  Grandpapop

What exact plugin is it complaining about? Since it's not seem to be Flash or Java, it's probably complaining about some audio/video codec (like wmv or mp3). Ubuntu does not install certain proprietary (non-free) multimedia codecs as a default, so you have to install them yourself. I think this might be the problem.

Consult this:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

It will explain to you how you can get certain multimedia formats to play.

---

