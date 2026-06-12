---
title: "sudo deborphan | xargs sudo apt-get -y remove --purge"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by hifly1231 on 2009-02-01
How do I get ***sudo deborphan | xargs sudo apt-get -y remove --purge*** to stop detecting ***gstreamer0.10-plugins-ugly-multiverse*** as orphan and removing it?  This is driving me **_CRAZY_**!!!  I tried setting up the orphan shortcut in Synaptic, but it doesn't seem to detect everything like running ***sudo deborphan | xargs sudo apt-get -y remove --purge*** in terminal.  Thanks!!!

---

### Post by alexmaco on 2009-02-01
My guess is that it's detecting it as orphan because it's just recommended/suggested by other packages. You could either try installing something that requires it (I have oggconvert and ubuntu-restricted-extras that require it), or hack it something like (beware, I haven't tried this so I don't know if it  works (though it should)):

```
sudo deborphan | grep -xv "gstreamer0.10-plugins-ugly-multiverse" | xargs sudo apt-get -y remove --purge
```

I recommend trying to install the ubuntu-resticted-extras first of all.

Hope this helps.

---

