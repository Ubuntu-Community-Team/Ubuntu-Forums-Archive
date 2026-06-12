---
title: "sketchup equivalent"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by qwertyuiop96 on 2009-04-08
I've been using sketchup for a while now, and love it.  Previously worked on OS X- then on the other computer I replaced XP Pro 64- whick it didn't work on well at all.  Of course, it was Windows ;) It doesn't seem to work with Wine- Actually Wine never worked for me.  Anyway, does anyone know of something like sketchup?  I don't do indoors, just exteriors.  And it MUST be free.

---

### Post by durand on 2009-04-08
Apparently, it should work in wine: [http://wiki.winehq.org/GoogleSketchup](http://wiki.winehq.org/GoogleSketchup)

You could look at [Blender3d]("http://blender3d.org"). It's not that similar to sketchup as it's designed to be an all round 3d program rather than for architecture but it is a really, really good program when you learn how to use it. It might be what you're looking for, or it might not.

---

### Post by qwertyuiop96 on 2009-04-09
It's not sketchup- but I think that once I grow more proficient at using it I may decide it is better than sketchup- as it does subsurfing, which I LOVE.  Not quite the same interface- more complex- But I am determined to figure it out! :KS

---

### Post by durand on 2009-04-09
Yeah, it is really well made though the interface can take a while to get used to. There are a huge amount of tutorials for Blender.

[http://blendernewbies.blogspot.com](http://blendernewbies.blogspot.com) and [http://en.wikibooks.org/wiki/Blender_3D:_Noob_to_Pro](http://en.wikibooks.org/wiki/Blender_3D:_Noob_to_Pro) are the two main sites I use.

Post at their forums if you get stuck: [www.blenderartists.org](www.blenderartists.org)

---

### Post by qwertyuiop96 on 2009-04-09
I understand this is the UBUNTU, and not Blender forums, but since this thread seems to almost be going in the direction of Blender help, I'll ask a Blender question!  Downloaded, installed- went normal- through add/remove.  So, under apps, graphics there are 2 blender icons, one "fullscreen" and one "windowed".  That's all fine and dandy, but the "windowed" isn't windowed, its full screen.  This is a pain, since I need to see the tutorial and Blender at the same time.  Thanks in advance.

---

### Post by durand on 2009-04-09
Are you using desktop effects? Maybe it will work fine if you turn them off? You could run blender from the terminal with the -w flag. That might work.

Applications > Accessories > Terminal:

```
blender -w
```

I say "might" because it's supposed to be loading in windowed mode...You could always just alt+tab to the tutorials.

---

### Post by qwertyuiop96 on 2009-04-10
The problem was the effects- not compatable well with Compiz Fusion?  With Metacity it did window and worked great.

---

### Post by wildman4god on 2009-04-10
Back to the original topic. There is no alternative (other than blender) for Google sketchup, however being its a Google product I imaging they will eventually produce a Linux version, sometimes it takes them a while to get Linux versions of their software out.

---

### Post by C.S.Cameron on 2009-04-11
SketchUp works great with wine but only with Nvidia graphics cards.
There are a few tricks to getting it to work though.
After installing with wine,
Go to /home/YOURNAME/wine/drive_c/windows/regedit.exe
expand HKEY_CURRENT_USER
expand software, google, sketchup, glconfig, display and click HW_OK
Change the value to 1.
In wine configuration add SketchUp to applications and set windows version to XP.
open SU and close the startup windows as quick as possible, may need a reboot.

---

