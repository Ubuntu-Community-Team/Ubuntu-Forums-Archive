---
title: "How do I install this dock? &amp; Icons question"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by juil on 2009-11-04
I came across this screenshot and was wondering how I could install the dock at the bottom?

[http://www.ubuntu-art.org/content/preview.php?preview=3&id=76898&file1=76898-1.jpg&file2=76898-2.jpg&file3=76898-3.jpg&name=Azel](http://www.ubuntu-art.org/content/preview.php?preview=3&id=76898&file1=76898-1.jpg&file2=76898-2.jpg&file3=76898-3.jpg&name=Azel)

Also, i downloaded some icons packages to use them but I am not sure how to use them. I put them in the /home/.icons/ folder but when i go to change icon for an app it doesn't detect the icon in the folder...
Also what is the difference between .svg and .png?

---

### Post by undecim on 2009-11-04
That bar is AWN. Install the avant-window-navigator package, and it will appear in your Applications menu.

When you change an icon for an App, it only shows icons that are part of your current theme. You should be able to browse for more and navigate to your .icons folder. Or, you can go to your appearance preferences and edit your current theme to use that set of icons (the icon theme should appear in the "icons" tab while editing your theme)

SVG is an acronym for Scalable Vector Graphic, and PNG is an acronym for Portable Network Graphic.

In an SVG file, information about the size and location of lines and curves is stored. With PNG, information about each individual pixel is stored. What this means is that SVG images can be scaled to any size without pixelating (i.e. becoming blurred or blocky), whereas with PNG, it is not.

---

### Post by m4tic on 2009-11-04
icon packs are to be in tarballs, go to preferences and appearance. on the themes tab, click install

---

### Post by abhiroopb on 2009-11-04
svg and png are just two different picture formats. 

For icons go to: System>Preference>Appearance>Install and select where your icon pack is.

The dock could be a number of programs. Try gnome-do (in a terminal: sudo apt-get install gnome-do). Once installed start it up from Acessories>Gnome Do. Click on the arrow in the top right corner. Select Preferences, select appearance and under theme select docky.

---

### Post by cptr13 on 2009-11-05
That dock is AWN...not any number of docks.  However, most of the available docks are similar and fun to fool with.  The most common ones are AWN, Cairo dock and Gnome-Do.  There are a few others to choose from too though.  All have pros and cons.  Personally, I love the functionality of Gnome-do

---

