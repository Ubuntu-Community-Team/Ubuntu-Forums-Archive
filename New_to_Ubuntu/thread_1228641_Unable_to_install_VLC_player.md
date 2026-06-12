---
title: "Unable to install VLC player"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by Nisal on 2009-08-01
i tried to install VLC in this way but i got this error can any one help me please ?

[IMG]http://i28.tinypic.com/2lsxzqp.png[/IMG]

---

### Post by Liolikas on 2009-08-01
sudo apt-get install vlc

If you want to install vlc.

---

### Post by Big_astur on 2009-08-01
Not sure where u get that code from but are you not sure it's:

```
sudo apt-get install vlc vlc-plugin-* mozilla-plugin-vlc
```
Notice the space between the * and the m from mozilla

---

### Post by kansasnoob on 2009-08-01
> **Nisal said:**
> i tried to install VLC in this way but i got this error can any one help me please ?

[IMG]http://i28.tinypic.com/2lsxzqp.png[/IMG]

Your command is wrong. Should be:

```
sudo apt-get install vlc mozilla-plugin-vlc
```

But, IMHO the easiest way to accomplish such things is using Synaptic. For instance open Synaptic and click on Search, then type vlc.

You can then select the packages you want and you'll be informed of what dependencies need to be met.

---

