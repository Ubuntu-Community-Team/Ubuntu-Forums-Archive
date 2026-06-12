---
title: "Used Update Manager to get adobe flashplayer 10 but where is it?"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by bobmac on 2010-02-17
Folks,

Update Manager informed me that there was an update for adobe flashplayer 10 which I downloaded - but where is it. It doesn't show up on any menu or put an icon on the desktop.

Can anyone tell me where it is and how to get at it?

Regards,

Bob

---

### Post by lindsay7 on 2010-02-17
I do not think you can see this file.  It runs in the background.

---

### Post by JackRock on 2010-02-17
If Update Manager downloaded it, it also installed it.

---

### Post by bobmac on 2010-02-17
Folks,

It may well have been installed but my problem is finding it. I've looked all over the place and simply cannot locate it.

Usually, when an app is installed it shows up in the menu and, or, has an icon on the desktop. This app has neither.

Any assistance will be gratefully appreciated

Regards,

Bob

---

### Post by wojox on 2010-02-17
Look in:

```
/usr/lib/flashplugin-installer/
```

If you've got Firefox type:

```
about:plugins
```

in the url bar.

---

### Post by JackRock on 2010-02-17
> **bobmac said:**
> Folks,

It may well have been installed but my problem is finding it. I've looked all over the place and simply cannot locate it.

Usually, when an app is installed it shows up in the menu and, or, has an icon on the desktop. This app has neither.

Any assistance will be gratefully appreciated

Regards,

Bob

Ah, sorry.  I misunderstood your post.  I thought you meant to find a file to install the program.  Flash is one of those programs that is integrated into other items, such as a media player or (more likely) a browser.  So you only see the Flash program when it's actually in use - such as an embedded .flv file on a web page.

---

### Post by philinux on 2010-02-17
Open a terminal. Apps>Access>terminal

```
locate libflashplayer.so
```

It is a file that gets installed as a firefox plugin. It is not an app that has a menu item.

---

### Post by bobmac on 2010-02-17
Folks,

I've tried out all the ideas that you kindly gave me. I managed to locate the *.so file. However, when I go to a video and right click it shows that it seems to still be using version 9.

Any ideas what I'm doing wrong

Regards,

Bob

---

