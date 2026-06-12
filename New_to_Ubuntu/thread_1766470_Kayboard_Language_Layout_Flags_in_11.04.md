---
title: "Kayboard Language Layout Flags in 11.04"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-05-24
Hi All,

Its a small thing but I'd like to have flags representing my current keyboard layout instead of text in the indicator. 

I've copied the png files to /usr/share/pixmaps and then checked show flags in the gconf-editor.

I've also tried copying the pngs to ~/.icons/flags/ and then checked show flags in the gconf-editor.

I've tried following a suggestion I read here about creating a symbolic link using:
```
   
sudo ln -s /etc/X11/xkb /usr/share/X11

``` 
and then checked show flags in the gconf-editor.

In every case all I get when the show flags option is checked is an empty space where there used to be a layout indicator although the hotkeys to change layouts still works.

Any ideas?

---

### Post by GrouchyGaijin on 2011-05-24
For some reason the png files were corrupted when I copied them to the pixmaps folder.

I recopied them and now I have flags.

---

