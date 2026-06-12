---
title: "What is the difference between .jpg and .JPG?"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by Miljet on 2010-01-04
I was cleaning up my Pictures directory and noticed that every file ending with .jpg (small letters)is listed in the terminal in light purple but the files ending with .JPG (capitol letters)are listed in normal black text. Does Ubuntu see these as different types of files? I can change the name of a file from .jpg to .JPG and it will change colors. Same exact file with same name except for the suffix.

---

### Post by jlhaslip on 2010-01-04
no difference in the file or image.

---

### Post by oldsoundguy on 2010-01-04
nothing other that capitalization.   BUT, if you link to a file that is .jpg and you put .JPG into the code for the link, you will get a busted link! (and visa versa!)

There, CASE COUNTS!

---

### Post by jflaker on 2010-01-04
They are different files.  Linux is case sensitive...

picture.jpg is not the same as picture.JPG and not the same as Picture.jpg

---

### Post by theozzlives on 2010-01-04
Linux is case sensitive so it looks at them differently. It should treat them the same, if you change the view to icons do you see the pic?

---

### Post by sisco311 on 2010-01-04
> **Miljet said:**
> I was cleaning up my Pictures directory and noticed that every file ending with .jpg (small letters)is listed in the terminal in light purple but the files ending with .JPG (capitol letters)are listed in normal black text. Does Ubuntu see these as different types of files? I can change the name of a file from .jpg to .JPG and it will change colors. Same exact file with same name except for the suffix.

It's just an obscure feature of gnome-terminal. 

.avi, .png, .jpg ... files are recognized as multimedia files while .AVIs, .PNGs ... are not.

I'm too lazy (and I don't use gnome-terminal :P), but one should file a BUG report. ;)

---

### Post by Miljet on 2010-01-04
Thanks sisco311, that was what I was getting at. The difference between being seen as multimedia versus regular file. 

And thanks to everyone else who responded. Yes, the files are viewable both as icons and pictures no matter which extension. I was just curious as to why they displayed differently in the terminal listing.

---

### Post by lovinglinux on 2010-01-04
> **Miljet said:**
> Thanks sisco311, that was what I was getting at. The difference between being seen as multimedia versus regular file. 

And thanks to everyone else who responded. Yes, the files are viewable both as icons and pictures no matter which extension. I was just curious as to why they displayed differently in the terminal listing.

Additionally, with the exception of some applications, in Linux you usually do not need an extension. You can for example rename **picture.jpg** to simply **picture** and it will still be recognized by most applications. You can even rename movie.avi, which has a video format, to movie.mp3, which is an audio format. It will play normally as video on mplayer, vlc, xine...

---

