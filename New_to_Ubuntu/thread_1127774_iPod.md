---
title: "iPod"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-04-16
How do I set things up such that my iPod opens Floola as soon as I plug in my iPod to my PC?

---

### Post by nol1ght on 2009-04-17
There are 2 way to change autoplay program.
1) You have to use: System->Preferences->Removable Drives and Media Preferences. There is a multimedia tab and portable music player checkbox.
(if you cant find Removable Drives and Media Preferences just install it with "sudo apt-get install gnome-volume-manager" )
2) You can edit /etc/gnome/defaults.list, find the line: x-content/audio-player=..... and edit it as you wish.

---

### Post by dunbrokin on 2009-04-17
> **nol1ght said:**
> There are 2 way to change autoplay program.
1) You have to use: System->Preferences->Removable Drives and Media Preferences. There is a multimedia tab and portable music player checkbox.
(if you cant find Removable Drives and Media Preferences just install it with "sudo apt-get install gnome-volume-manager" )
2) You can edit /etc/gnome/defaults.list, find the line: x-content/audio-player=..... and edit it as you wish.

Thanks for that, but actually it only partly worked. On my machine (running Jaunty) I followed route 1 and now my iPod works perfectly. However, when I look at gnome/defaults.list, it does not show that the audio player is associated with Floola...it is associated with rhythmbox.desktop.

Now, on my wife's machine (Running intrepid) it does not have the same Removable Drive and Media and so I cannot set hers via 1. However I did set it via 2 and replaced rhythmbox.desktop with floola.desktop......but nothing happened......CONFUSED!!

---

### Post by reeseslover531 on 2009-04-17
I think it looks in both places to see if there is a default. I am pretty sure it looks for the config file from part 1 first, and then moves onto the defaults file.

---

### Post by dunbrokin on 2009-04-17
> **reeseslover531 said:**
> I think it looks in both places to see if there is a default. I am pretty sure it looks for the config file from part 1 first, and then moves onto the defaults file.

I don't think that can be true as I closed down my machine and restarted between when I followed 1) and when I looked up defaults.list. And it was after I restarted my machine that Floola worked automatically with my iPod. I then looked up defautls.list....and hence my confusion!!!

---

### Post by superprash2003 on 2009-04-17
try system->preferences->preffered applications

---

### Post by dunbrokin on 2009-04-17
> **superprash2003 said:**
> try system->preferences->preffered applications

Nope, that does not appear to work as the iPod does not appear in that series of menus.

---

### Post by dunbrokin on 2009-04-19
bump

---

### Post by dunbrokin on 2009-04-21
bump

---

