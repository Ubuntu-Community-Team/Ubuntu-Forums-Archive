---
title: "i need to make an ISO of an old windows hard drive"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by danny_galaga on 2008-12-27
this hard drive i have is from my MAME cab (google if you dont know). so while it's not very large (win98 stripped down, with everything on there like mame and roms etc still less than 1 gig) it has a few different things on there like macros etc that would be a real pain to set up again. for instance, there is a macro to shut down the cab using the fire button and player 2. and on start up, it goes straight to the game menu. it also has a space invader sound to replace that windows start up sound :) 

ive been meaning to do this for a while. i had a scare last night and realised i better do it before i WISH id done it. in fact, this drive is a copy a friend made for me from the original, so its certainly worth the effort.

so whats the best thing for me to make an ISO of it (i guess thats what i need to do) and then plug in another hard drive and put the image on that- ready to rock and roll again?

---

### Post by handydan918 on 2008-12-27
> **danny_galaga said:**
> this hard drive i have is from my MAME cab (google if you dont know). so while it's not very large (win98 stripped down, with everything on there like mame and roms etc still less than 1 gig) it has a few different things on there like macros etc that would be a real pain to set up again. for instance, there is a macro to shut down the cab using the fire button and player 2. and on start up, it goes straight to the game menu. it also has a space invader sound to replace that windows start up sound :) 

ive been meaning to do this for a while. i had a scare last night and realised i better do it before i WISH id done it. in fact, this drive is a copy a friend made for me from the original, so its certainly worth the effort.

so whats the best thing for me to make an ISO of it (i guess thats what i need to do) and then plug in another hard drive and put the image on that- ready to rock and roll again?

If you can boot a live cd up on this system, or chain the drive up in another system, you can use dd or rsync to make complete copies.

---

### Post by danny_galaga on 2008-12-27
im guessing thats not available in the synaptic packages? is dd short for something? where do i find it?

edit: i have the hard drive in question temporarily hooked up to this computer as a secondary. ive simply copied all the files i can from it so that if worse comes to worst, i still have something to work with. but an image would be best...

---

### Post by handydan918 on 2008-12-28
dd is installed by default, but if you get the syntax wrong, you're gefficken.
I'd recommend rsync instead. Sorta like this:
```
rsync -av <source> <target>
```

Luck!

---

### Post by mapes12 on 2008-12-28
This is what you want: [http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

It's free, easy to use, better than Ghost and 100% windoze supported. You can then move onto the best OS going i.e. Ubuntu Linux.

---

