---
title: "Plug-ins"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by Grandpapop on 2010-09-28
Sir:  I am trying to go to a site on the internet and there is a box that comes up and tells me I need a plug-in and if I want it to find the plug-in?  I punch yes and it goes out and looks.  Then it comes back and says it can't find suitable plug-in.  In this case what do I do, I sure would like to use the site.  Thanks Grandpapop

---

### Post by TeoBigusGeekus on 2010-09-28
Which site is this?
The plugin is probably flash, but let's just be sure...

---

### Post by madmax75 on 2010-09-28
What sort of plugin is it asking for?

Ubuntu does not install proprietary/closed source codecs by default (Linux Mint is better in this instance I believe).

Check your Ubuntu Software Center (Applications -> Ubuntu Software Center), or your Synaptic Package Manager (System -> Administration -> Synaptic Package Manager).

Search and install **ubuntu-restricted-extras**. This should give you many extra audio and video codecs. Also install **ffmpeg**.

I would also advice you to install **adobe-flashplugin**, and also **sun-java6-bin**, **sun-java6-jre**, **sun-java6-plugin** and **sun-java6-fonts**. These will enable you to use sites that require Flash or Java.

---

### Post by sandyd on 2010-09-28
Heres a list of plugins that DON'T work at least. These are hopeless either because
1. They don't run in Linux
2. They don't run in firefox (not much of thse...)

List:
Shockwave
Active X
Windows Media Streams & such (if you haven't installed medibuntu)

---

### Post by Tibuda on 2010-09-28
> **madmax75 said:**
> Check your Ubuntu Software Center (Applications -> Ubuntu Software Center), or your Synaptic Package Manager (System -> Administration -> Synaptic Package Manager).


Or just click [here](apt://ubuntu-restricted-extras).

---

