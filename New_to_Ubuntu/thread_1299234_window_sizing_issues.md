---
title: "window sizing issues"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-10-23
im having some issues with my display, i have a netbook with widescreen display and the problem i am having is that certain windows (eg the tool boxes in gimp) that cant be maximised, and others that are locked to a certain size overhang the display, and i have no way to see what is it at the bottom...is there a way to fix this???

---

### Post by wrgb2 on 2009-10-23
Do you mean that, for example the Gimp toolboxes, you've resized them to their minimum possible size and they still overhang the display.  Or you can't see the top or bottom to grab hold and resize them?

Randy

---

### Post by JamesParnell on 2009-10-23
i have resized to the minimum size they can be and yes it still overhangs

---

### Post by kbielefe on 2009-10-23
Don't know how to fix it, but I know two work arounds that may help.  If you hold down alt, you can move a window up by clicking and dragging anywhere on the window, not just on the title bar.  That will let you move it up to see the rest of the window.

The other option, which I've not tried personally, is that you may specify a virtual display size in the display subsection of your /etc/X11/xorg.conf that is larger than your actual display size, and it will scroll if you move your mouse to the edge.  Search for "virtual xdim ydim" on [this page]("http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html").

Hope that helps.

---

### Post by JamesParnell on 2009-10-23
thanks, i will give it a read through.

---

