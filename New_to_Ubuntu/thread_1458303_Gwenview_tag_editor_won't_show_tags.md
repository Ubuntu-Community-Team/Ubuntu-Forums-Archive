---
title: "Gwenview tag editor won't show tags"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by Cleveland Rock on 2010-04-19
I finally decided to get off my butt and start tagging my images, but I noticed the tags aren't showing up. I don't want to report it as a bug, because it's probably something simple like a missing font or something.

If the "about" dialogues are to be believed, I am using KDE 4.3.5 and Gwenview 2.3.4.

Please see the attached screenshot. Thank you.

**Edit:** Actually, it seems my tags aren't being saved, so I guess it's more than just a missing font. Argh! I suck at Linux!

---

### Post by Cleveland Rock on 2010-04-20
Bump.

Also, if it helps any, the Gwenview start page says, "Sorry, browsing by tag is not available. Make sure Nepomuk is installed on your computer.".

I have no idea how to install Nepomuk.

---

### Post by mgranet on 2010-04-20
You can setup Nepomuk (and the Strigi search) from System Settings-->Advanced Tab-->Desktop Search. 
A info box will probably pop up. Ignore it.
Enable the checkbox for Nepomuk, and Strigi, if you want it. (Strigi, IMO, can be a resource hog.) Don't tinker with the memory useage of Nepomuk in the Advanced tab. That slider don't work the way you think it works.

---

### Post by Cleveland Rock on 2010-04-20
Thanks, but I don't know how to open System Settings. I expected it to be in the System > Administration menu, but it's not there.

---

### Post by mgranet on 2010-04-20
Ummm... You're using Gnome. I think. I'm not really sure....

---

### Post by mgranet on 2010-04-20
Does your desktop have a top panel, a bottom panel, and the left of the top panel says Applications | Places | System?

Or a big panel at the bottom, with a blue K icon?

---

### Post by Cleveland Rock on 2010-04-20
> **mgranet said:**
> Do you have a top panel, a bottom panel, and the left of the top panel says Applications | Places | System?

Or a big panel at the bottom, with a blue K icon?
I used to have the former until I rearranged my menus.

---

### Post by mgranet on 2010-04-20
Ok. You are using Gnome, with a KDE app. That might be the root of the problem. Unfortunately, I don't use Ubuntu proper enough to know how to help you turn on Nepomuk in Gnome's control panel. Hopefully, there might be one or two others around this forum who have heard of this Gnome thing, and would be able to help you out. ;)

---

### Post by Cleveland Rock on 2010-04-20
Shoot, maybe I should have used [ubuntu] instead of [kde].

---

### Post by mgranet on 2010-04-21
OK, I'm on to something. In a terminal: ```
nepomukserver
```

This started the server and allowed me to set tags. The problem is it's not persistent. You should be able (on 9.10, I think)to go to System-->Preferences-->Session and add it there. I think.

EDIT: Thought wrong. I'm not really sure how to do it in Gnome.

---

### Post by Cleveland Rock on 2010-04-21
Brilliant. That works. Unfortunately, I don't have "Session". I have "Startup Applications", if that would work.

---

