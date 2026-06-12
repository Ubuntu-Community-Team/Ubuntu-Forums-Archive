---
title: "picasa shop icon not working"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by masmithrpg on 2009-06-09
I am on ubuntu 9.04 and have picasa 3.0.  I am not absolutely positive, but i think since i ugraded to 9.04 my picasa shop icon no longer works.  It just sort of hangs(like a windoze program).  I have been searching for a resolution but so far no luck.  Any ideas on how to resolve this.  

Thanks 
mike

---

### Post by chrisod on 2009-06-09
I just checked - it's not working for me either. (Picasa 3 / Jaunty).

---

### Post by jmatties on 2009-06-17
I had the same problem. I found a solution [here]("http://groups.google.com/group/Google-Labs-Picasa-for-Linux/browse_thread/thread/76b23f4514edb3e9"). In a nutshell, here's Sean's solution.

Instead of using vim, I used gedit:
```
sudo gedit /opt/google/picasa/3.0/wine/drive_c/Program\ Files/Google/Picasa3/runtime/defaults.ini
```

Replace this line:
printerURL=https://uploader.picasa.com/providers/wine/printers.php?picasaversion=30

with:
printerURL=https://client4.google.com/providers/printers.html

Save, and it should work immediately.

---

### Post by masmithrpg on 2009-06-22
Fantastic,  It works now.  I searched and found a similar windows solution, but couldn't figure out how to do this for ubuntu.   
Thank you so much.

---

