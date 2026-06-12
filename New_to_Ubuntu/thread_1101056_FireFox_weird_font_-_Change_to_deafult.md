---
title: "FireFox weird font - Change to deafult?"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by UnknownFear on 2009-03-19
I somehow changed the font for FireFox and now I don't know how to get back to the default font setting. Does anyone know what the default font settings is, or how to get back it it?

---

### Post by lukjad on 2009-03-20
Sure! Open up Firefox and go to *Edit->Preferences*. Then select the *Content* tab. Under the **Fonts and Color** subsection, change the **Default font:** to **serif**. Size 16. If you changed the setting in the **Advanced** section, my defaults are:

```
Fonts for: Western
Proportional: Serif
Serif: serif
Sans-serif: sans-serif
Monospace: Monospace
```

In that order. The font sizes are 16 for the Proportional, and 12 for the Monospace. 

While there are more setting, I don't think you would have changed them, so I'll spare you the details. ;)

Hope this helps!

---

### Post by kpatz on 2009-03-20
This may sound sacrilegious, but how can I get my Firefox fonts in Ubuntu to look more like the ones I see in Windows?

The Windows fonts are more readable, sharper on my LCD display.

EDIT:  I noticed, for example when on here, the posts appear in a sans serif font in Windows but in a serif font in Ubuntu.  All my font settings are the same in both installs.

---

### Post by lukjad on 2009-03-20
Sure! Just install msttcorefonts. This can be done by installing it through Synaptic (*System->Administration->Synaptic Package Manager*) by scrolling down to msttcorefonts and right clicking it and selecting Install, or you can open the Terminal (*Applications->Accessories->Terminal*) and type:
```
sudo apt-get install msttcorefonts
```

Then enter your password. Once it is installed, shutdown all instances of Firefox and start it again. That should do it.

---

### Post by humphreybc on 2009-03-20
This may be of some help but I find the following settings best for Ubuntu system fonts and Firefox fonts:

(The fonts in firefox are size 12, for some reason that gets blanked out by the arrow).

Cheers!

---

### Post by cool-linux on 2009-03-20
check this! work for me!! 

[http://ubuntudoitall.blogspot.com/2009/01/firefox-with-antialiasing.html](http://ubuntudoitall.blogspot.com/2009/01/firefox-with-antialiasing.html)

---

### Post by UnknownFear on 2009-03-20
That worked. Thanks, lukjad007!

---

### Post by lukjad on 2009-03-20
You're welcome! 
PS, I like your avatar.

---

### Post by kpatz on 2009-03-21
Thanks guys... playing around with the fonts makes Firefox (and my desktop) more readable in Ubuntu.

---

### Post by ncabane on 2009-03-27
Msttcorefonts worked fine for me!

Thanks!

---

### Post by lukjad on 2009-03-30
Great!

---

