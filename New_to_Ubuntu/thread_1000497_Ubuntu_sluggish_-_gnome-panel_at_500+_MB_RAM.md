---
title: "Ubuntu sluggish - gnome-panel at 500+ MB RAM"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by Nixie Pixel on 2008-12-03
Hi, I have been noticing that lately both gnome-panel and firefox have been using up about 500MB of RAM.  I am pretty sure that Firefox is because I often have many windows open, but I would think it shouldn't be that high.

gnome-panel, however, I would not expect to be that high.  Right now, here are the breakdowns:

Firefox: 
Virtual - 874.2 MiB
Resident - 662.5 MiB
Writable - 628.1 MiB
Shared - 34.5 MiB
X Server - 21.4 MiB

gnome-panel:
Virtual - 40.2 MiB
Resident - 25.5 MiB
Writable - 12.2 MiB
Shared - 13.4 MiB
X Server - 518.0 MiB

I am running 8.10, Intrepid Ibex, my kernel version:
2.6.27-10-generic #1 SMP Fri Nov 21 12:00:22 UTC 2008 i686 GNU/Linux

Is there any more information I can provide to help figure out what is going on?  I have tried rebooting several times, but the same problem exists.

Thank you!

~Nix

---

### Post by nhasian on 2008-12-03
You gave up on KDE already?  Just for reference on my system i have:

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 8833 nhasian    20   0  608m 333m  34m S    5 16.5  59:16.37 firefox
 6048 nhasian    20   0 77072  25m  14m S    1  1.3   0:42.82 gnome-panel 
```


to find the data i used:
```
top | grep gnome-panel
top | grep firefox
```

dang firefox is a big resource hog!

---

### Post by Nixie Pixel on 2008-12-03
Well, I am actually working with Linux on four different machines, 2 of them dual-booting, and thinking of dual-booting with a 5th.  (Not all of them are mine.. I am a geek, but not *that* much of a geek!)  The machine I am talking about here is my primary laptop which has 2GB RAM and a dual-core processor.  

However, to answer your question, yes I did give up on KDE on my server.  I was having a hard enough time trying to figure out how everything worked with the CLI to worry about two different interfaces that were quite different from each other.  I might try KDE again in the future, but right now I can't even get Samba to share a directory out over my network without major problems, so it won't be any time soon!

Anyway, to the matter at hand - I take it then that 500MB of RAM usage is not out of the ordinary for gnome-panel?

If so, do you have any idea why Intrepid might feel sluggish on this machine as compared to running on one that is 5 years old and nowhere near as powerful?  I don't have any extra memory-resident programs running that I know of, and the server is running twonky and Vuze at the moment.  So I really can't fathom what is going on >=/

Edit:  By the way, I am embarrassed to tell you that after using the top command I was unsure of how to stop it other than by exiting out of the terminal...

---

### Post by skymera on 2008-12-03
I've just read.

In nautilus you can stop it previewing thumbnails. Apparently that reduces memory usage to about 25MB for Gnome-Panel.

Give it a shot and say how it goes.

---

### Post by Nixie Pixel on 2008-12-03
So far, so good, this seems to be keeping gnome-panel to a reasonable memory usage level.

Thanks!

---

### Post by Michael.Godawski on 2008-12-03
Here I found a long list of tweaks which promises to enhance the speed of firefox; did not try them out by myself.


[LIST]
[*][http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)
[/LIST]

I also stumbled upon this:


[LIST]
[*][http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/)
[/LIST]
Again, no idea if it is a real alternative to FF but worth a try.

And for the sluggishness of the gnome panel try this:


[LIST]
[*][http://www.ubuntu1501.com/2007/12/speed-up-gnomes-menus.html](http://www.ubuntu1501.com/2007/12/speed-up-gnomes-menus.html)
[/LIST]

---

### Post by Nixie Pixel on 2008-12-04
Unfortunately, X Server memory was up over 600 MiB for gnome-panel today, and system performance slowed to a crawl, even with the thumbnail tweak.

I will try the menu popup tweak, but that seems to address timing, not memory, no?

Thanks!

---

### Post by nhasian on 2008-12-05
i just checked firefox's memory usage and today it's over a gig!  jeeze.  after a bit of digging I found this:

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/304942](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/304942)

---

### Post by HungryMan on 2008-12-05
> **Nixie Pixel said:**
> 
Edit:  By the way, I am embarrassed to tell you that after using the top command I was unsure of how to stop it other than by exiting out of the terminal...

just press q, like you would with man

---

### Post by nitrofurano on 2009-03-17
i had an experience on running better i386 on a P4 computer with 256mb ram than an amd64 on a Core2Duo with 512mb ram

It seems to be the reason Debian webpage says somewhere about Sparc32 and Sparc64 architectures, as they were not too focused on Sparc64 yet due on the ram memory used on this platform seems to be too much when compaired with the Sparc32, and there are no significant differences of performance - and there would be a similar situation about between i386 and amd64

What i think is only worth running amd64 platform on machines you have more than that 2gb ram limit you found at i386 (i think, 3gb at least)

Otherwise, i were also getting this problem as opportunity to try lighter window managers, like LXDE (i really love this one! i'm using it now!), Fluxbox (used it for years), PekWM, JWM, etc.

Well, after the frustrating amd64 experience on the Core2Duo, while i don't have at least 3gb ram there, i installed back the i386

---

