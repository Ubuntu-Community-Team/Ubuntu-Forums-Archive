---
title: "Different Background for each &quot;desktop&quot;?"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by akakingess on 2009-05-08
Is it possible to have a different background for each "virtual desktop"? I have (4) different desktops (love that function in Ubuntu (Gnome)), but would like to have different backgrounds. I know some ubuntu genius out there knows of a way!!!

Earl

---

### Post by Rinzwind on 2009-05-08
There are some programs: 

wallpapoz
[http://wallpapoz.akbarhome.com/](http://wallpapoz.akbarhome.com/)
It's a bit laggy when switching

You can with compiz: 
[http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/](http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/)

Here's a instruction video on doing it manually: [http://gsocblog.jsharpe.net/archives/15](http://gsocblog.jsharpe.net/archives/15)

---

### Post by crobruncato on 2009-05-08
> **Rinzwind said:**
> There are some programs: 

wallpapoz
[http://wallpapoz.akbarhome.com/](http://wallpapoz.akbarhome.com/)
It's a bit laggy when switching

You can with compiz: 
[http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/](http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/)

Here's a instruction video on doing it manually: [http://gsocblog.jsharpe.net/archives/15](http://gsocblog.jsharpe.net/archives/15)

I'm having trouble with the compiz method. I'm in jaunty, and the background images option isn't available.

Rob

---

### Post by akakingess on 2009-05-08
> **crobruncato said:**
> I'm having trouble with the compiz method. I'm in jaunty, and the background images option isn't available.

Rob
Actually I had the same prob, but if you scroll further down in CCSM there is a wallpaper setting, make sure and check the check-box and load what images you will want to use there.  Also, make sure that the setting in Awn Manager that the directions tell you to turn off is turned off, can't remember what it was off the top of my head.  I eventually got it to work and am loving it!!!

Earl

---

### Post by akakingess on 2009-05-08
> **akakingess said:**
> Actually I had the same prob, but if you scroll further down in CCSM there is a wallpaper setting, make sure and check the check-box and load what images you will want to use there.  Also, make sure that the setting in Awn Manager that the directions tell you to turn off is turned off, can't remember what it was off the top of my head.  I eventually got it to work and am loving it!!!

Earl
Sorry about that, I just looked it up, it wasn't the setting in Awn Manager, it was opening up the Run command Alt+F2, typing gconf-editor and hitting run. Then under apps->nautilis->preferences make sure 'show desktop' is turned off. Hope that works for you.

Earl

---

