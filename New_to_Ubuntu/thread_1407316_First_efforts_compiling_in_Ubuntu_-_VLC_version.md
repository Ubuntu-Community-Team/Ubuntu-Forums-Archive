---
title: "First efforts compiling in Ubuntu - VLC version"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by oldmankit on 2010-02-15
So there's a bug in VLC 1.0.2 which is fixed for the latest release, 1.0.5.  (The bug is that when you open the playlist and sort by any column, it crashes out with a 'segmentation fault').  Because I could not see any precompiled .deb files for the latest release, I went about downloading the source code and compiling myself.  A few hours later, I finally got it to work.  Well, almost.  It hasn't found an interface module, so I'd better go back and tweak the configuration options.

But anyway, the question is, the package I've complied is definitely 1.0.5, but why when I type "vlc --version" does it still say 1.0.2 Goldeneye?

I know this probably has a really simple solution, so thanks if anyone can point me in the right direction!

---

### Post by zvacet on 2010-02-15
Somebody will answer you to your compilig problem,but if you want you can download VLC from [here.]("http://www.getdeb.net/updates/Ubuntu/9.10/?q=vlc")

---

### Post by Linuxforall on 2010-02-15
Have you removed older vlc? Also did you install to home folder?

---

### Post by oldmankit on 2010-02-16
>  		Somebody will answer you to your compilig problem,but if you want you can download VLC from [here.]("http://www.getdeb.net/updates/Ubuntu/9.10/?q=vlc")
I knew there was a simpler way!  I'd never heard of getdeb.net.  Thanks for that - it's updated a few of my programs for me.

Now the bug has gone, and I'm free to organise my music collection a bit better.  Amarok obviously does organising well, but I just love how small and fast vlc is.

>  		Have you removed older vlc? Also did you install to home folder? 	
I had previously uninstalled the old version, which is why I was so confused about the version number.  I built it inside /usr/share/vlc-1.0.5/, and didn't specify installing to my home folder, do you think that was why?

I appreciate your help.

---

