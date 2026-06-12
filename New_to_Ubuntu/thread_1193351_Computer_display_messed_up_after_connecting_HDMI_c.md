---
title: "Computer display messed up after connecting HDMI cable"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by mangurt on 2009-06-21
Greetings all,
I connected a HDMI cable from my laptop to a LCD tv.  Now, after I disconnected the HDMI cable, my laptop monitor is smaller (I have about 2 inches of black space on each side that is not used at all.  Is there anyway to change this?
Thanks

---

### Post by plexi50 on 2009-06-21
I had the same thing happen to me. Could not get it to come back to the correct resolution.  I ran this in terminal:

$ sudo dpkg-reconfigure xserver-xorg

all was back to normal.

---

### Post by mangurt on 2009-06-21
I tried that, and I still have the same problem :(

---

