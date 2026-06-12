---
title: "OGM Rip Error While Merging"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by conryf on 2009-04-04
Hi, I'm trying to rip my DVD so I can just play them on my harddrive. After searching the forums I decided to try OGMRip. I'm ripping a longish movie (2hr 22min) but still, it took almost 16 hours to rip and then, at the end, it crapped out. Giving the error "Error while merging"

Is there soem way for this to work, and to take less time? Could this be a DVD Burner Driver issue? I have a Sony DRX-S7OU-R external DVD burner and a lenovo X61 laptop.

---

### Post by MrWES on 2009-04-04
> **conryf said:**
> Hi, I'm trying to rip my DVD so I can just play them on my harddrive. After searching the forums I decided to try OGMRip. I'm ripping a longish movie (2hr 22min) but still, it took almost 16 hours to rip and then, at the end, it crapped out. Giving the error "Error while merging"

Is there soem way for this to work, and to take less time? Could this be a DVD Burner Driver issue? I have a Sony DRX-S7OU-R external DVD burner and a lenovo X61 laptop.

I've tried them all, and IMHO -- K9Copy is the best. It's a KDE app, but it'll run perfectly find in GNOME. 

```
sudo apt-get install k9copy
```

You can rip the DVD full, or it will produce an iso file that you can burn to a DVD5.

Bill

---

### Post by halitech on 2009-04-04
+1

K3b will also make a copy as well, just select to create iso and then you can use something like VLC to play the iso and have full menus as well.

---

### Post by conryf on 2009-04-04
Is that reccomended? And is it space efficient to just keep an ios on the hard drive?

I used k9copy and liked it too, but I was thinking that keeping iso's were sub optimal.

---

### Post by JDorfler on 2009-04-04
Have you tried Handbrake yet?  Here's a [link to add it to your repository]("https://launchpad.net/~handbrake-ubuntu/+archive/ppa").

---

### Post by halitech on 2009-04-04
you can use K9copy to just rip out the main part of the movie if you want as well. I just like iso files cause it means I can reproduce the dvd at any time if need be :)

---

### Post by conryf on 2009-04-09
Well, I ripped all the DVD I wanted succesfully with k3b, k9copy was still acting funny. But now I have nearly 300 gigs of movies and not all of them need to be iso's. Is ther any way to convert iso's to mpg4 or avi or something?

---

