---
title: "simple searching"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by Don Bowen on 2010-02-13
This should be an easy one... when I use search, I put *.mp3 into the search bar, on a drive that I KNOW has mp3s...and it finds ... nothing...

How do you search for files on your hard drives with Ubuntu?

---

### Post by Girya on 2010-02-13
> **Don Bowen said:**
> This should be an easy one... when I use search, I put *.mp3 into the search bar, on a drive that I KNOW has mp3s...and it finds ... nothing...

How do you search for files on your hard drives with Ubuntu?

Not sure if you want to use a terminal but from one (Applications>Accesories>Terminal):

```
find -name *.mp3
```

outputs: 

> ./Music/Roxy_Music-Avalon-03-Avalon.mp3
./Music/01-When_I'm_Gone-Away_From_The_Sun-3_Doors_Down.mp3
./Music/02-Just_A_Friend_(Live)-Valentine's_Day_Massacre,_Volume_1_Men_Sing_Break-Biz_Markie.mp3
./Music/01-17-Walk_This_Way_-_Featuring_Run-D.M.C.-Gold-Aerosmith.mp3
./Music/The_Rolling_Stones/Some_Girls/Far_Away_Eyes.mp3
./Music/The_Rolling_Stones/Some_Girls/Lies.mp3
./Music/The_Rolling_Stones/Some_Girls/Just_My_Imagination.mp3
./Music/The_Rolling_Stones/Some_Girls/Respectable.mp3
./Music/The_Rolling_Stones/Some_Girls/Some_Girls.mp3
./Music/The_Rolling_Stones/Some_Girls/Miss_You.mp3
.....


---

### Post by Sir Jasper on 2010-02-13
Hi,

Alternatively you could try gnome-search-tool (using a desktop launcher or a shortcut if desired).

My regards

---

### Post by l-x-l on 2010-02-13
Under Applications go to Accessories then "Search for File"

---

### Post by Don Bowen on 2010-03-07
OK...well "search for files" under Application ... Accessories... seems to work well.
I was specifically wondering why the little magnifying glass in nautilus doesn't do anything.  That's the magnifying glass icon thing in "File Browser".  Click on it and it replaces the "location" input space with "search".  Put *.mp3 in there and it finds ... nothing.  type "*.*" in the search bar...and it finds nothing... what is the point of this?
   It's irritating... it's like a "volume" control on a car radio...that...doesn't adjust the volume!

---

### Post by Don Bowen on 2010-03-07
maybe I need to "un ask" the question... as Pirsig wrote in "Zen and the Art"  ... or at least ask in a different way...

In the ubuntu file browser...
a) what is the magnifying glass for?
b) how do I get it to find ANYTHING? (presuming it is there to find things... it might not be!)

---

### Post by asmoore82 on 2010-03-07
> **Don Bowen said:**
> OK...well "search for files" under Application ... Accessories... seems to work well.
I was specifically wondering why the little magnifying glass in nautilus doesn't do anything.  That's the magnifying glass icon thing in "File Browser".  Click on it and it replaces the "location" input space with "search".  Put *.mp3 in there and it finds ... nothing.  type "*.*" in the search bar...and it finds nothing... what is the point of this?
   It's irritating... it's like a "volume" control on a car radio...that...doesn't adjust the volume!

The built-in search in nautilus is targeted for a less advanced user,
to get results, just search for ".mp3" ~ leave out the wildcard(*).

As with any software, when you target the less advanced user, the "power user" loses some functionality.
In this case, searching for "*.mp3" automagically implies that you only want
files that end with ".mp3" and nautilus cannot oblige.

The search tool under the Places Menu will probably suit your skill level much better:
"Places -> Search for files..." ~ it accepts wildcard globs(*) and single characters(?).
You could say "Find all MP3 files whose 4th letter is "e" ... "???e*.mp3"

---

