---
title: "Creating a media hub"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by gosp on 2011-08-03
I just found an old unused computer in my parents' attic (Pentium 2 or 3 era.) My plan is to stick it in my closet, add a usb number pad and speakers, and then leave it as a music system for my bedroom (I'll remove keyboard, monitor, etc at the end). 

The idea is that I'll have 10 or so genres, so I can press a button, and the always on computer will start playing music from a folder or playlist.   Is Ubuntu going to be a good fit for this system? Would I save a significant amount of power by going to a lighterweight system (xubuntu?) If so, what do you recommend? Once I'm set up, I shouldn't need a GUI. Hell. I can set it up without a GUI just as well.

 I'm not familiar with writing any shell scripts for linux, but could I write one which does the following-If musicplayer is not playing, start it.  Stop music. Start playing from folder X on a Random track

 Which programs should I look into which should have such a capability? I shouldn't have a problem with SSHing from another computer to change up the playlists, should I?  Ideally I'll never have to hook this guy up to a monitor.  Thanks for any help!

---

### Post by Mark Phelps on 2011-08-03
> **gosp said:**
> Is Ubuntu going to be a good fit for this system? 

Any recent version -- probably NOT.  Ubuntu is not really a lightweight distro; instead, it's a full-featured distro.

I tried an older version on a PIII 800 -- and it was slow SLOW as to be all but useless.

Also, I believe that you need 300+MB of memory to install (or is it 500+?); either way, if your old PC has 256MB (typical amount for those days), you won't even be able to install Ubuntu, let alone run it.

Look into Lubuntu, it demands less resources.

---

### Post by nothingspecial on 2011-08-03
If you installed any old minimal distro (no gui) (but why not ubuntu) and mpd, you could control the music from your phone/laptop/netbook

---

### Post by aeiah on 2011-08-03
+1 for mpd. ive just installed it on a £30 router so id think a P2/P3 era pc should be ok, provided you install a linux distro light enough.

id go with ubuntu minimal or a barebones debian install, but you might find that something even lighter would be better.

---

### Post by gosp on 2011-08-03
Hey guys, thanks for the help so far. MPD seems versatile enough and I'll try it out.  I just tore the computer open and discovered that I had actually upgraded to 512MB of memory several years ago, so I'll go ahead and try lubuntu and xubuntu to see that they work well enough.

---

