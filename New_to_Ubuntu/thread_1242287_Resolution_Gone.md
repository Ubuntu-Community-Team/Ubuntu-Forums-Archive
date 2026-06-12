---
title: "Resolution Gone"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by sideffects on 2009-08-17
I was messing around with Boxee and I used an S-Video cable to link to my tv, and I used the tv as an extended desktop. Now, the tv is unplugged and the highest resolution that I can set my laptop to is 1024x768, whereas before I was using 1200x800. Is there a fix?

---

### Post by colau on 2009-08-17
> **sideffects said:**
> I was messing around with Boxee and I used an S-Video cable to link to my tv, and I used the tv as an extended desktop. Now, the tv is unplugged and the highest resolution that I can set my laptop to is 1024x768, whereas before I was using 1200x800. Is there a fix?
System>Preferences>Display
It's 1024x768

---

### Post by sideffects on 2009-08-17
That's not what I meant. Sorry, I had a really hard time explaining what happened. Basically, I used to use 1200x800, but now the highest resolution in the drop down list is 1024x768.

---

### Post by sideffects on 2009-08-17
anyone?

---

### Post by wojox on 2009-08-17
What graphics card are you using?
You could always go into /etc/X11/xorg.conf and take a look at it.

---

### Post by NightwishFan on 2009-08-17
You can restore default graphic settings in recovery mode. This will remove all restricted drivers and custom setups though.

---

### Post by sideffects on 2009-08-17
> **wojox said:**
> What graphics card are you using?
You could always go into /etc/X11/xorg.conf and take a look at it.
I looked in the xorg.conf file and it told me to run
sudo dpkg-reconfigure -phigh xserver-xorg
so I did, and everything seems to be working now. Thanks!

---

