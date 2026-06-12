---
title: "Can't mount network folder with spaces, åäö"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by gymmarn on 2008-05-05
Hi

I'm an Ubuntu newb, just moved my work computer from Windows -> Ubuntu. I've got the most stuff working, but can't seem to mount the folders inside the network.

This is how I mounted it in Winblows:

\\192.168.0.1\ao\AO Bredband\02.folder\02.14.region\

I can mount this part fine: \\192.168.0.1\ao

But when I try to add the name with the spaces and dots etc Ubuntu translates it into some weird % language. For example:
\\192.168.0.1\ao\AO Bredband
gets the error:
Couldn't show the folder "smb://192.168.0.1/ao/%5Cao%20bredband/" failed to mount etc.

Anyone got a solution to this problem? :)

/Gymmarn

---

### Post by solitaire on 2008-05-05
I'm not sure if this will work but try putting a "/" before the space.

so it reads like this:
```

\\192.168.0.1\ao\**AO/** Bredband\02.folder\02.14.region\

```
I've seen the "/" used before to get folders with spaces to be recognosed.

---

### Post by gymmarn on 2008-05-05
Tried that, still didn't work :(

---

### Post by Iowan on 2008-05-05
See if [this]("http://ubuntuforums.org/showthread.php?t=547958") one helps.

---

### Post by gymmarn on 2008-05-06
Thanks guys for the help. I finally figured out how to do it. It was quite easy when I found out how heh.

I could successfully mount the first part: ao. I failed with the rest though.

When you step inside the folders with the fileviewer (dunno what it's called in english, I've got Swedish translation) you got a button on the left side which allows you to change from "button or textbased location". I pressed textbased and voila got the folder in the right format, just to cut'n'paste and mount :)

/Gymmarn

---

