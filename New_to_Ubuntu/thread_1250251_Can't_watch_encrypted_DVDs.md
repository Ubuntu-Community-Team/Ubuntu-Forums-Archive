---
title: "Can't watch encrypted DVDs"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by shawnisalk on 2009-08-26
Hello, everyone. I realize there are a bazillion threads about DVD viewing difficulties, and I have read a bunch, but am still not able to view encrypted DVD's. 

This is what happens:
I open the DVD with Totem-xine.
It plays the DVD intro.
Right before the moment when it would otherwise go to th DVD menu, 
it closes without an error (this tells me it an issue about encryption)

What I have done so far:
Installed Totem-xine because this comes recommended
Installed ubuntu-restricted-extras
Installed css2

I'm wondering if I should uninstall all the totem stuff and re-install just totem-Xine (it seems like I still have the gstreamer version installed)

Any ideas?

Thanks,
Shawn

---

### Post by NoaHall on 2009-08-26
If you get a program called Ultamatix, it has the libraries you need to watch them - but you can only use them in USA

---

### Post by Moop on 2009-08-26
You need the libdvdcss2 package from Medibuntu. 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by jerome1232 on 2009-08-26
When you say you installed css2 do you mean libdvdcss2?

If not you need it from the medibuntu repo.

---

### Post by mkvnmtr on 2009-08-26
Enable the medibuntu repository. Open the package manager and choose to view the sections of the medibuntu repository. I use mplayer. Then you should find libdvdcss2. I believe when you install that you will be able to work with most dvds. There also might be some gstreamer packages that will help with some dvds.

---

### Post by nick_nik on 2009-08-26
Could somebody explain the differance if any between the Multiverse repository and medibuntu?

Nick

---

### Post by jerome1232 on 2009-08-26
They explain it on their site
[http://www.medibuntu.org/](http://www.medibuntu.org/)


basically it's software that can't be legally included with ubuntu due to various legal restrictions.

---

