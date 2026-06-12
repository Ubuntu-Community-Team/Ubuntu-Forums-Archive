---
title: "Cant add new fonts?"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by Ronchap on 2009-08-11
I downloaded a font for a Inkscape tutorial I am doing. It came as .zip. So I extracted it to desktop, and found out where my other fonts are. Problem is, I cant move the folder with the two files in it to the font folder, nor just the two font files. How do I add a font to Ubuntu 9.04?

Edit: Topic was ment to say How can I add fonts? not Can't!

---

### Post by halitech on 2009-08-11
there are 2 ways or doing it.

1. in your /home folder, create a folder called .fonts (the . is important) and move the fonts there

2. Press ALT + F2 and type in gksudo nautilus and use nautilus as root (potentially dangerous) to move the files to the /etc/fonts folder

personally I prefer option 1 as it saves your fonts in the case of a reinstall

---

### Post by Ronchap on 2009-08-11
#1, I created the folder. Put the two font files in there and the font still doesnt show up in Inkscape when I try to change the font. 

and as far as #2 goes, I have no idea what you just said :confused:

---

### Post by Ronchap on 2009-08-11
Well sorry for the double post, but I got them to show up, but this is what I did. Just tell me which folder is the only one the two .tff files should go in. I just copied them, and pasted them in /fonts, /truetype, /fonts/and the folder the two came in

---

### Post by halitech on 2009-08-11
they should be in /home/{username}/.fonts

change {username} to your username

---

### Post by Ronchap on 2009-08-11
oo.. like HAVE to be? Cause while I was waiting, I deleted them from every other folder except /usr/share/fonts, and everything works fine. They show up in inkscape... was i not suppose to do option #2? :( I must have done something wrong with your first option, so I went ahead and figured out #2 and got it working.

---

### Post by halitech on 2009-08-11
option 2 works as well and some people will only add fonts that way but I like option 1 simply because if you have to reinstall, anything outside my home folder gets wiped so with having a .fonts folder in my home folder preserves my fonts without having to reinstall them.

---

### Post by Ronchap on 2009-08-11
Thanks for the tips. It's just a chalk font, I would probably never use it again to be honest..lol. Just wanted my chalk board to look a little more like the tutorial. Thanks again :)

---

