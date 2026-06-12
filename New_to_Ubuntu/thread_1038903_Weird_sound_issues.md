---
title: "Weird sound issues"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by djk21108 on 2009-01-14
First time Ubuntu user.  I'm having a problem with sound in general.  Sometimes youtube videos are making sound, sometimes not.  Sometimes IM's coming in are making sound, sometimes not.

I don't get it.

---

### Post by iaculallad on 2009-01-14
Try installing the audio support wrapper for non-free flash plugin:

```
sudo apt-get install libflashsupport
```

---

### Post by djk21108 on 2009-01-14
Package libflashsupport is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  flashplugin-nonfree-extrasound
E: Package libflashsupport has no installation candidate

---

### Post by iaculallad on 2009-01-14
Sorry for that, I should have asked you want Ubuntu version you're using since libflashsupport is only available for Hardy through the universe repository. For the Intrepid version, try:

```
sudo apt-get install flashplugin-nonfree-extrasound
```

---

### Post by djk21108 on 2009-01-14
thanks, but im still having trouble with pidgin, i went to the sound tab in preferences and everything seems to be in order.  when i try to preview a sound it wont give me anything

---

### Post by iaculallad on 2009-01-14
Open Pidgin and select Preferences from the Tools menu. Under the "Sound" tab, click on the Method drop-down list and select "Command":
Sound command: **aplay %s**

---

### Post by djk21108 on 2009-01-14
thanks again, you're such a pro.

can you help me with this issue :)

[http://ubuntuforums.org/showthread.php?p=6545687#post6545687](http://ubuntuforums.org/showthread.php?p=6545687#post6545687)

---

