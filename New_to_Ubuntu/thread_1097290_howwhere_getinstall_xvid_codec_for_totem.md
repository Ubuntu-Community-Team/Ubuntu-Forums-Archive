---
title: "how/where get/install xvid codec for totem?"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by mishkin on 2009-03-15
I installed a windows xvid codec in wine in an attempt to get a scene sync fix to work (it didn't)

now I uninstalled said codec and totem isn't playing standard def xvids anymore

I imagine there is more than one option

I tryed sudo apt-get install xvid lol

---

### Post by taurus on 2009-03-15
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by mishkin on 2009-03-16
thx that worked (it installed a bunch of stuff in addition too)

---

### Post by oldos2er on 2009-03-16
I think the xvid codec is in libxvidcore4, which is why "sudo apt-get install xvid" didn't work. Just FYI.

---

### Post by .:Justus:. on 2009-03-16
> **mishkin said:**
> thx that worked (it installed a bunch of stuff in addition too)

This isn´t exactly on topic but you might want to look into vlc, it can play basically any movie file and it´s a bit more simple.

```
sudo apt-get install vlc
```

---

### Post by mishkin on 2009-03-18
I already have vlc in fact i had a really hard time making totem default again

I only use vlc when I need to fix sync or use subs

I like totem because it buffers (instead of no video for x secconds it waits before playing) and also because you can do do not show controls and there is no titlebar or seek bar or anything so I can maximize my work space while keeping the tv show as big as possible

---

### Post by sabme on 2009-10-06
searched synaptic for 'xvid' and got:

  avifile-xvid-plugin

installed it and my xvid movies now play

---

### Post by dasking on 2011-02-02
> **taurus said:**
> ```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```
  
didnt work for me caused the locking sequence to quit working
:lolflag:

when that happened i restarted the pc and works fine

---

