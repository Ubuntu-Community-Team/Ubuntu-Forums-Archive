---
title: "Best bit torrent cilent"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by Valkyria on 2009-02-28
I was wondering what is the best bit torrent cilent to use in Kubuntu.

---

### Post by taurus on 2009-02-28
Best really depends on who you ask.  For most, it looks like deluge is the winner.

---

### Post by dorkdork777 on 2009-02-28
I normally just use KTorrent. Works fine for me :P

---

### Post by Valkyria on 2009-02-28
> **taurus said:**
> Best really depends on who you ask.  For most, it looks like deluge is the winner.

I tried to install Deluge from add/remove and i got this error
```
APT Error. Context:
    Package download failed, 
    I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package. (due to missing arch), 
    : , 
    : , 
    : , 
    : , 
    : , 
    : 

```

How do i fix the package?

---

### Post by taurus on 2009-02-28
So you have all the repos enable in /etc/apt/sources.list?  In synaptic, go into Settings -> Repositories and make sure there is a check in front of all the repos except the Source code.  Then, reload it and see if you can install sun-java6-bin, sun-java6-jre, & sun-java6-plugin now.

---

### Post by Valkyria on 2009-02-28
> **taurus said:**
> So you have all the repos enable in /etc/apt/sources.list?  In synaptic, go into Settings -> Repositories and make sure there is a check in front of all the repos except the Source code.  Then, reload it and see if you can install sun-java6-bin, sun-java6-jre, & sun-java6-plugin now.

It turned out some installs were broken, and i just fixed em :D.

---

### Post by mkvnmtr on 2009-02-28
Deluge is good and what I use but Ktorrent is just as good. Only takes a little time to try them and find the one you like.

---

### Post by Crafty Kisses on 2009-02-28
Yes, I think Deluge is really good.

---

### Post by Inxsible on 2009-02-28
The best i think is rTorrent. Its a CLI app and an amazing tool.

---

### Post by Simian Man on 2009-02-28
Transmission.  It follows the Gnome principal of having relatively few features, but doing all of them flawlessly.

---

### Post by Valkyria on 2009-02-28
How can i make Deluge the default torrent client?

---

### Post by bgast1 on 2009-02-28
I like both Deluge and Ktorrent. I think because I am using Kubuntu that I will stick with Ktorrent and not bother with Deluge. Transmission works, but I really don't like it. If you are looking for speed, I've found that ktorrent is just as fast as any of them.

---

### Post by Xiong Chiamiov on 2009-02-28
Deluge and KTorrent are both popular, and so is uTorrent through Wine.  Personally, I use rtorrent in a screen session, but it's an ncurses interface, so that's probably not what you want.  BTG is another client that's got some good ideas, but their are still some odd things they have to work out.

---

