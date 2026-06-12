---
title: "How do i do it .avi"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by iwannalearn on 2009-02-05
Hi all been along time away from ubuntu but back again.

Can some one please help me out a bit please.

I just downloaded a backup film of rapidshare, came as normal in 8 parts .RAR

On windoz i used unrar them to one .avi file.

then use WinAVI to convert it to a mpeg2, which i would then ftp over to my linux set-top-box and watch it on the tv.

How is the procedure done using ubuntu?
does the unrar unpack the same way into one .avi file?
how do you convert .avi to mpeg2

i have read about winff but a bit lost with it.

Thanks for any tips

Cheers

---

### Post by fraser_m on 2009-02-05
You need unrar installed if you don't have it already, then you should be able to double-click on the .rar file and extract it.

```
sudo aptitude install unrar
```

As for converting it, you'll probably need ffmpeg first, and then you can install WinFF from it's homepage.

---

### Post by Rolcol on 2009-02-05
I would install unrar like fraser_m has explained and then use Ubuntu's default Archive Manager (file roller) to open the .rar file.  It should automatically join the other .r01 files.  I use HandBrake for media conversion.  It's not in the Repos but they have a package for Ubuntu.

[http://handbrake.fr/](http://handbrake.fr/)

---

