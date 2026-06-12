---
title: "Ubuntu does not seem to automatically recognize my laptop's webcam"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by Space-Wolf on 2009-12-04
I downloaded skype, and everything worked fine.  I could see my friend and all, but my webcam wasn't transmitting.  I guess ubuntu didn't pick up on it.  Is there a way to manually set it up?

---

### Post by dca on 2009-12-04
I always install *'cheese'*, it's in the repos.  It pretty much tells me w/o research as soon as you open app (webcam light will come on and you'll see yourself in camera) if my equipment works with a particular webcam whether integrated in laptop or USB cam on desktop...

---

### Post by Bölvaður on 2009-12-04
webcam brand?

if you dont know or cannot find out then use this command to detect it.

open the terminal (Applications &#8594; Accessories &#8594; Terminal)

if it is connected through usb
```
lsusb
```

if it is built in webcam
```
lspci
```

the camera should automatically be put to /dev/video0 I think.

---

### Post by stoogiebuncho on 2009-12-04
In my experience, Skype does not find your webcam automatically.  You need to right-click on the Skype icon in your system tray, go to "Options", and go to the "Video" section.  There's a place there where you can select the location of your webcam.  There may be several options, just try them one by one until you find the one that works.

*note* If you do this while you are on a call with someone, you will have to hang up and call them back before changes take effect.

*edit* Also, in order to Skype to transmit your video, you need to enable it.  When you are in a conversation with someone, there will be a light blue button on the window with something that looks kind of like a video projector.  Click on that and you will have the option to "Enable my Video" or something like that

---

### Post by Space-Wolf on 2009-12-04
Sweet it's working now.  But, when I'm in skype the video window is tiny and there doesn't seem to be any readily available options that will let me increase it's size...

---

### Post by stoogiebuncho on 2009-12-04
I'm pretty sure one of those little blue buttons at the bottom of your conversation window will give you the option to go double size or full-screen.  I can't test it right now as none of my friends are online, but I remember doing it in the past.

---

