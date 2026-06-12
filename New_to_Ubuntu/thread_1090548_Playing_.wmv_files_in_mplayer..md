---
title: "Playing .wmv files in mplayer."
date: 2009-03-08
forum: New to Ubuntu
---

### Post by melrokz on 2009-03-08
Hi. My .wmv files, when opened in mplayer, it gives an error> mplayer could not load wmvdmod.dll
I found the file in my windows installation, but where to copy this to so that mplayer can use it???

---

### Post by hammad1337 on 2009-03-08
I think ubuntu should not give dll errors, as it foes not use .dlls ( though m not 100% sure).

Wine uses dll files. and these can be placed in ~/.wine/c_drive/windows/system32/ directory.

---

### Post by mrbiggbrain on 2009-03-08
> **hammad1337 said:**
> I think ubuntu should not give dll errors, as it foes not use .dlls ( though m not 100% sure).

Wine uses dll files. and these can be placed in ~/.wine/c_drive/windows/system32/ directory.

This is not totaly true, linux can use any file it chooses, it could have a .dll file as the exectable and .exe file as the library if it really wanted. but by all means, .dll isnt a really common ubuntu filename

---

### Post by hammad1337 on 2009-03-08
:D
I totally get you man, but your post might be a bit confusing for melrokz.

---

### Post by mc4man on 2009-03-08
If your using the i386 intrepid (32 bit) then just go here and install w32codecs.
 
[http://packages.medibuntu.org/intrepid/w32codecs.html](http://packages.medibuntu.org/intrepid/w32codecs.html)

---

### Post by hyper_ch on 2009-03-08
you can use my generator in the sig to add the medibuntu repos (you get access to skype and googleearth and other stuff) and then install w32codecs or w64codecs depending on your system.

---

### Post by kaixi on 2009-03-08
What about installing ubuntu-restricted-extras package and then play the video from Totem?

---

