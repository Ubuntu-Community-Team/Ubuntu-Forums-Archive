---
title: "webcam wont work in skype"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by minsf on 2010-01-15
i cannot get my webcam to work with skype in ubuntu.
conversation works great (both mic and speakers) and i can see my friend's webcam, but he cannot see mine.

i know my webcam (logitec quickcam e 3500) works on my 9.10 installation, because i installed the "cheese" package which works perfect.

skype installation: i downloaded the latest deb package from skype (skype-ubuntu-intrepid_2.1.0.47-1_i386.deb). when i double clicked it, i noticed it says that it depends on 8 packages (libqt4-core libqt4-gui etc.) so i installed all the dependencies with apt-get, and then finished the skype installation, which went well.

when i right-click skype on the panel and choose Options>VideoDevices i can see that "UVC Camera (xxxx: xxxx) (/dev/video0)" is selected, which seems correct. but when i click "test" i get nothing. 

any clue?

---

### Post by spiderbatdad on 2010-01-15
IDK i ran 
```
sudo dpkg --info skype-ubuntu-hardy_2.1.0.47-1_386.deb
```
and got a list of 10 pgks...one of which is libxv1:
```
Depends: libasound2 (>> 1.0.12), libc6 (>= 2.3.6-6), libgcc1 (>= 1:4.1.1-12), libqt4-core (>= 4.2.1), libqt4-gui (>= 4.2.1), libstdc++6 (>= 4.1.1-12), libx11-6, libxext6, libxss1, libxv1

```

---

### Post by Merk42 on 2010-01-15
You may need to follow the instructions [here](http://www.eoinmurphy.org/blog/2009/04/26/logitech-webcam-skype-under-ubuntu/)
I did for my Logitech cam and it worked great

---

### Post by minsf on 2010-01-18
> **Merk42 said:**
> You may need to follow the instructions [here](http://www.eoinmurphy.org/blog/2009/04/26/logitech-webcam-skype-under-ubuntu/)
I did for my Logitech cam and it worked great
thanks! 
i followed the link in the beinning of the link that you posted, and ran skype with
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype &
```
and now the webcam works great!

---

### Post by carnfall on 2011-03-08
> **Merk42 said:**
> You may need to follow the instructions [here](http://www.eoinmurphy.org/blog/2009/04/26/logitech-webcam-skype-under-ubuntu/)
I did for my Logitech cam and it worked great

Link is broken and I get the exact same problem! Any help?

---

### Post by dawershonu on 2011-09-13
> **minsf said:**
> thanks! 
i followed the link in the beinning of the link that you posted, and ran skype with
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype &
```and now the webcam works great!

I get ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

I have tried everything. My webcam works on google talk and cheese.
Any ideas?

---

