---
title: "scan to jpg or gif?"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by dbch on 2009-11-27
Bought a scanner and need to scan and upload pics for a job deadline tonight.  Site only takes jpg and gif.  

How?  I can't get those extensions on the xsane scanning program I got.  Its past the deadline by an hour.  If I don't get this then I have to go for a long long walk to a 24hr fax machine.

Help.

---

### Post by mbzn on 2009-11-27
Scan as normal
When saving rename to abc.jpg and the dropdown box for type select jpeg.

---

### Post by Boffie on 2009-11-27
If you have GIMP, you can import your scan and save it as JPG or GIF from there.

---

### Post by anaconda on 2009-11-27
sudo apt-get install imagemagick

After installing imagemagick you can convert between imageformats like this:
eg.
convert image.png image.jpg

(or whatever.. even converting image to a pdf works
convert image.jpg image.pdf )

---

### Post by dbch on 2009-11-27
******* eh!  mbzn  Why didn't anyone just say that before, I've been looking all over the place.

Boffie - I got the gimp, just fiddled;  now that I know I'll check it out...

anaconda - I got imagemaker, even re-installed it and can't find it on my computer anywhere.  If its just a terminal thing, I'm not into that yet.  Maybe ltr ...              ?

Thanks everyone.

---

### Post by bwang on 2009-11-28
First of all, it is imagemagick, not imagemaker.
Open a Terminal, and type
```
cd <directory file is in>
```
So if the file is on the desktop then you would
```
cd /home/$USER/Desktop
```
Then type
```
convert <filename> <outfile.jpg>
```
You will get a file called outfile.jpg in the same directory the file is in.

---

