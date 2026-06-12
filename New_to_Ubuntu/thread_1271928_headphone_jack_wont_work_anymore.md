---
title: "headphone jack wont work anymore"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by grumpylad77 on 2009-09-21
I have been using 9.04 on my Inspiron 1501 for a few years now.
I use my headphones with my laptop a lot, and have never had a problem with them. A few minutes ago, I plugged my headphones in and cranked up the music (in the middle of my school's library) only to find out that the music is playing through the speaker and not the headphones. Any ideas about what could cause this out of nowhere? There is no sound at all through the headphones, and all sound is through the speakers.

---

### Post by LowSky on 2009-09-21
could be a bad jack, things can break. But look in the volume setting to make sure headphone option is turned on.

---

### Post by LewRockwell on 2009-09-21
our vote is for internal jack breakage

.

---

### Post by Yiftos on 2009-09-21
> **grumpylad77 said:**
> I have been using 9.04 on my Inspiron 1501 for a few years now.
I use my headphones with my laptop a lot, and have never had a problem with them. A few minutes ago, I plugged my headphones in and cranked up the music (in the middle of my school's library) only to find out that the music is playing through the speaker and not the headphones. Any ideas about what could cause this out of nowhere? There is no sound at all through the headphones, and all sound is through the speakers.

In 8.10 and 9.04 there is the option (check box) to turn off speakers using headphone jack. I don't remember the exact wording ( I don't have my laptop with me.) You can find it by double clicking the speaker icon displayed within the alert bar. select properties/advance. The check box is there. I had this happen to me two months ago and thought the headphone jack went bad.

---

### Post by djyoung4 on 2009-09-21
Check under volume control to see if the headphone volume is turned up.  mine does this too.  I have to turn the front down under volume control whenever I am listening to headphones because the headphones don't override the speakers to turn them off when I plug headphones in.  it gets kind of annoying but I haven't found a solution to the problem yet.

---

### Post by LowSky on 2009-09-21
> **djyoung4 said:**
> Check under volume control to see if the headphone volume is turned up.  mine does this too.  I have to turn the front down under volume control whenever I am listening to headphones because the headphones don't override the speakers to turn them off when I plug headphones in.  it gets kind of annoying but I haven't found a solution to the problem yet.

sounds (no pun intended) like a chipset identity issue, 

you might need to modify this file
```
/etc/modprobe.d/alsa-base
```

---

