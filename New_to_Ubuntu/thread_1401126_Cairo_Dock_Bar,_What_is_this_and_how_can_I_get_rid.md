---
title: "Cairo Dock Bar, What is this and how can I get rid of it?"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by Seithe on 2010-02-07
Hi, I just installed the Cairo-Dock Bar. But now when I opened it, this separator or something keeps bothering me, xD its as if something just cut it in half right here in the picture below. How do I fix that? Thanks.
Via picture was uploaded to tinypic.com.
[http://i48.tinypic.com/2a9bbt1.jpg](http://i48.tinypic.com/2a9bbt1.jpg)

---

### Post by nhasian on 2010-02-07
you dont like the cairo dock?  hehe I see that your bottom toolbar is still there.  you can remove it by right clicking on the bottom toolbar and selecting remove.  then you would just use the cairo dock... but since you dont like the cairo dock you can either tell it not to startup when ubuntu starts or uninstalling it.

I would check the settings inside cairo to see if it has a button you can uncheck to prevent it from starting with ubuntu.  alternatively you can look in System->Preferences->Startup Applications (also called sessions in older versions of ubuntu)

if you want to uninstall Cairo-dock you can do it from System->Administration->Synaptic Package manager or from a terminal with the command:

```
sudo apt-get remove cairo-dock
```

a lot of people like using a dock on the bottom of the screen like the MacOS has.  i've tried Cairo-dock, Avant Windows Navigator, Gnome-Do, and Docky.  I'm using Docky now since its fast and light.

---

### Post by Seithe on 2010-02-07
Oh, no I meaning the cut like separator in my picture how do I fix that?

---

### Post by howefield on 2010-02-07
> **Seithe said:**
> this separator or something keeps bothering me,...

Go into the configuration setup and select the Appearance tab, and uncheck "Separate the different types of icons"

(This is for version, 2.1.3).

---

### Post by Seithe on 2010-02-07
Thanks that fixed it! :D

---

### Post by fabounet on 2010-02-08
in the advanecd mode you can also choose how to draw the separators (physical separators like here, flat separators like MacOS or an image of your choice) ;-)

---

### Post by Dlambert on 2010-06-19
Thanks!

---

