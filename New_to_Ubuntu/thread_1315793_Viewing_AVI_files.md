---
title: "Viewing AVI files"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by daniell59 on 2009-11-05
I hooked up my camera and it was immediately detected. I was able to view JPEGs. How do I view the video, the AVI files?

---

### Post by OffAxis on 2009-11-05
vlc will do it.

```
sudo apt-get install vlc
```

---

### Post by Temposs on 2009-11-05
What happens when you try to open the AVI files?

EDIT: Yes, vlc is a good option

---

### Post by rygar on 2009-11-05
AVI can be played in movie player/totem which is installed by default, although a lot of people prefer VLC because it seems to work for everything.  you'll also want to install a few proprietary codecs if you haven't yet, it should minimize the amount of unplayable media in your future...

at a terminal, try this:
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install vlc vlc-plugin-pulse

see if that works for you...

---

### Post by kyuubi777 on 2009-11-05
vlc is the shizza!!!! you get compatibility w/ basically every shell + codecs out there as standard.. none of this "download extra codecs" crap

---

### Post by daniell59 on 2009-11-05
> **OffAxis said:**
> vlc will do it.

```
sudo apt-get install vlc
```

Thanks, but tell me something. How can I learn know which code to type?

Thanks

---

### Post by daniell59 on 2009-11-05
I just  installed it, but where do I find it?

---

### Post by tom.swartz07 on 2009-11-05
> **daniell59 said:**
> I just  installed it, but where do I find it?
its under applications, sound and video.


if you would like to learn how to use the terminal commands, [http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/) is a great place to start.

Hope this helps!

---

### Post by philinux on 2009-11-05
> **daniell59 said:**
> Thanks, but tell me something. How can I learn know which code to type?

Thanks

System>Help and Support - scroll to bottom of list>Advanced Topics>Terminal Commands References(Man pages)

For your code look in System Administration> scroll down to apt-get.

---

