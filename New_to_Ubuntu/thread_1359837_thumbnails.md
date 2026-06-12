---
title: "thumbnails"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by hellomoto on 2009-12-20
Hey, im trying to workout why only some of my thumbnails show up in my video folder on my external hard disk. They are all .avi files. 

However newly ripped videos don't show any thumbnails but old films in my collection do. Is there anyway I can get them to appear?

---

### Post by Physical Hook on 2009-12-20
```
rm -r $HOME/.thumbnails/*

```Let us know if the problem persists.

---

### Post by hellomoto on 2009-12-20
> **Physical Hook said:**
> ```
rm -r $HOME/.thumbnails/*

```Let us know if the problem persists.

Hey, thankyou for the quick reply.

I followed your instructions, this removed everything in the .thumbnail directory. 

When i refreshed my films folder. It just removed any previous thumbnails, now none of the films have thumbnails.

I rechecked in the .thumbnails dir, and it only has a .thumbnails/fail/gnome-thumbnail-factory with .pngs init.

Any ideas?

---

### Post by Paqman on 2009-12-20
> **hellomoto said:**
> 
Any ideas?

Do you have Totem installed? Have you checked the settings at Edit > Prefs > Preview?

---

### Post by hellomoto on 2009-12-20
I have been doing some research and it could it be possible the reason Im not get thumbnails is due to NOT having totem installed and using mplayer instead? is there a way to get movie thumbnails WITHOUT having to install totem.

---

### Post by hellomoto on 2009-12-20
> **Paqman said:**
> Do you have Totem installed? Have you checked the settings at Edit > Prefs > Preview?

no i do not have totem installed, this apears to be the problem, I am just installing ffmpegthumbnailer to see if this corrects the problem.

---

### Post by hellomoto on 2009-12-20
i am unable to get ffmpegthumbnailer to work in the command line, always get invalid argument.

the man page can be see here: [http://code.google.com/p/ffmpegthumbnailer/wiki/FFMpegThumbnailer]("http://code.google.com/p/ffmpegthumbnailer/wiki/FFMpegThumbnailer")

can any show me some example useage for AVI files? I would like to do a whole directory of avi files with one command if possible. 

Thankyou

---

### Post by Physical Hook on 2009-12-20
```
find ./ -name "*.avi" -exec ffmpegthumbnailer -i {} -o {}.jpeg ;\

```

---

