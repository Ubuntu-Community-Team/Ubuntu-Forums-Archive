---
title: "gstreamer0.10-plugins-ugly"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by hifly1231 on 2009-01-06
I use soundconverter to convert all my downloaded audio to mp3.  In order to do this, I have to have  gstreamer0.10-plugins-ugly-multiverse installed.  However, when I clean up my Ubuntu 8.10, this is always listed as an orphaned package.  Soundconverter won't convert to mp3 without it.  Is there any way to stop it from being detected as orphaned?  Thanks!!!

---

### Post by Tim Sharitt on 2009-01-06
If it was automatically installed, seting it to manually installed may help.

Open a terminal and do:
```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```
That should give you a message saying that it has been set to manual install.

---

### Post by hifly1231 on 2009-01-08
> **Tim Sharitt said:**
> If it was automatically installed, seting it to manually installed may help.

Open a terminal and do:
```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```
That should give you a message saying that it has been set to manual install.

It's still listing as an orphaned file.  Any other suggestions?

---

