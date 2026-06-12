---
title: "Viewing Files on iphone w/out opening rhythm box"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by ubunwhat on 2010-09-27
Fairly new to Linux and have muddled through using Rhythmbox to sync my iphone for the most part.  There is one very annoying issue, however.  I am a podcast junkie and I really need to be able to delete listened to podcasts.  This is impossibly in Rhythmbox.  I can go into the phone and select them, but my only options are "cut", which removes them from the list but not the phone, and "remove from playlist" which does the exact same thing.  In both cases they are back as soon as the phone syncs, even though they are nowhere on my laptop hard drive.  Maddening!  I have tried to delete them using the swipe and delete method in the iphone itself, but again, they just keep re-appearing every time I sync.  I need to be able to view the phone as a drive ( something windows does without hassle ), so I can just delete the bloody things.  When I try to do that by navigating to the phone in Places, I hit a brick wall.  I open up the podcasts folder and, rather than a list of podcasts, I just get an option to open rhythmbox.  Any help would be greatly appreciated.

---

### Post by andrewthomas on 2010-09-27
can you navigate to the files in the terminal?

where does it mount at?

it should be under /media/xxxx,  so it you open a terminal and ```
cd /media
```then```
 ls
```it should show some options

---

### Post by ubunwhat on 2010-09-30
The phone connects via USB.  I have no idea what you mean when you ask how it is mounted.  I tried to navigate there via the terminal, but got no love.  I got into the /media directory but the ls command produced absolutely nothing.  The phone's name is "broccoli" because, well, I hate it, and when I tried to got a step further and go cd /broccoli it said no such device existed.  However, the phone does show up as broccoli in both rhythm box and Places.  I really do need to find a way to delete items from the phone and have them stay deleted.

---

