---
title: "[SOLVED] Where can I add fonts?"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by aut-omatic on 2009-01-01
I want to add the times new roman font to the emerald window decorator. I realized though that most programs use fonts from a source from Ubuntu (i guess.. not sure). So i was wondering if I could add a font that I downloaded somewhere so that I can access it from programs that might use fonts.

---

### Post by hambone79 on 2009-01-01
If you are using GNOME, you can drop the files in your home directory under the ".fonts" directory. This should make them available to Emerald immediately.

Since the .fonts directory is a hidden directory, you may need to go to the View menu in the file manager and enable the "Show Hidden Files" option. You can also hit CTRL+H to make the hidden files visible.

---

### Post by aut-omatic on 2009-01-01
I tried this, but i couldn't find it.
I went to my home directory, and looked at the hidden files. But the only similar directory was .fontconfig

Maybe I'm looking in the wrong directory :S

---

### Post by Big_astur on 2009-01-01
I have then in:

/usr/share/fonts/truetype

fonts it's a hidden folder anyways.

---

### Post by hambone79 on 2009-01-01
It sounds like you are missing the ".fonts" directory. Just create a new one in your home directory (you were in the right place if you saw the .fontconfig directory) and you should be set.

---

### Post by aut-omatic on 2009-01-01
Thanks!! This was a great help!!

---

