---
title: "udev rules - possible values of ENV"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by wep940 on 2011-05-13
Is there any type of environment variable so that when a Kindle or other ebook reader is mounted it is set as an ebook reader and not as a usb audio device?  I've seen the rule in udev rules for the Kindle - I commented mine out so by default it mounts as a removable disk.  I'd like to change it to say it's an ebook reader.

Thanks in advance!

---

### Post by wep940 on 2011-05-14
Bump.   What I'd like to know is if there is a value for ENV in a udev rule that will id the device as an ebook reader, much in the way that this sets to a media player (I comment out that rule myself so it doesn't try ask if I want to mount my Kindle with Banshee):
 
ATTRS{idVendor}=="1949" , ATTRS{idProduct}=="0001|0002|0003|0004" , ENV{ID_MEDIA_PLAYER}="amazon_kindle"

 
Thinking there may be a variable like ID_EBOOK_READER or some such thing.

---

### Post by wep940 on 2011-05-16
bump.

---

### Post by TeoBigusGeekus on 2011-05-16
I've never bothered to learn how to write udev rules - too lazy, I still use hal and dbus.
However, could [this]("http://www.reactivated.net/writing_udev_rules.html") be of any help to you?

---

### Post by wep940 on 2011-05-16
Couldn't find the possible ENV variables in there when I looked last week, however I think I'll just put NAME='Kindle' on the rule and that should be good enough.
 
Thanks!

---

