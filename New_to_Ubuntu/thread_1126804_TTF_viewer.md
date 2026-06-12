---
title: "TTF viewer"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by 311005901 on 2009-04-15
Hello.
I'm looking for a program that can open my TTF file and put it in a grid, like how Windows displays and previews fonts.

I've tried "FontyPython" and "GNOME Specimen" and both aren't what I'm looking for.

I just want to double-click on the icon on my desktop and see a quick little preview before I put it in my GIMP font directory.

Are there any programs that do this?

---

### Post by llamabr on 2009-04-15
```
brock@hops:~$ apt-cache search preview fonts
texlive-base-bin - TeX Live: Essential binaries
texlive-latex-extra - TeX Live: LaTeX supplementary packages
advi - an active DVI previewer and presenter
catdvi - DVI to plain text translator
dvi2ps-fontdata-ptexfake - Fake pTeX TFM files
dvilib2-dev - a portable DVI interpreter library - development
fontmatrix - featureful personal font manager
gnome-specimen - Simple font preview and compare application for GNOME
libdvilib2-16 - a portable DVI interpreter library - runtime
lxappearance - a new feature-rich GTK+ theme switcher
ghostscript - The GPL Ghostscript PostScript/PDF interpreter
brock@hops:~$ 

```

fontmatrix and gnome-specimen look good.  I'm not familiar with the windows thing you're talking about, but give them a try, and let us know if they're the wrong thing.

---

### Post by 311005901 on 2009-04-16
Thanks for the quick reply!
I'm looking for something like the attached image.

---

### Post by 311005901 on 2009-04-19
Bump?

---

### Post by Yingy on 2009-05-18
Whenever I click on a ttf file from my CD I get a window that looks almost the same as yours.  
There is a font viewer out called fontmatrix.  Screenshot at [http://www.getdeb.net/app/Fontmatrix](http://www.getdeb.net/app/Fontmatrix)  There is a thread on installing this program in the forums at [http://ubuntuforums.org/showthread.php?t=738535](http://ubuntuforums.org/showthread.php?t=738535)
Best of luck to you.

---

### Post by hugmenot on 2009-05-19
There should be a tool installed that pretty much looks like what you want. There wasn&#8217;t one in Intrepid because of some packaging mishap. But your forum profile states that you run Jaunty?

Can you verify that you have "gnome-font-viewer"? It&#8217;s not a separate package but comes with gnome-control-center.

Just open a terminal and run "gnome-font-viewer" to see if it&#8217;s present.

---

### Post by 311005901 on 2009-05-21
> **hugmenot said:**
> There should be a tool installed that pretty much looks like what you want. There wasn’t one in Intrepid because of some packaging mishap. But your forum profile states that you run Jaunty?

Can you verify that you have "gnome-font-viewer"? It’s not a separate package but comes with gnome-control-center.

Just open a terminal and run "gnome-font-viewer" to see if it’s present.

Yes! I got it to work!
I just right click on a font file and go to properties. Then I change the program that Nautilus uses to open it up to "gnome-font-viewer." It works perfectly!
Thanks!
:popcorn:

---

