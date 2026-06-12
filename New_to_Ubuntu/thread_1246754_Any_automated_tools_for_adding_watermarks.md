---
title: "Any automated tools for adding watermarks?"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by cosmoshell on 2009-08-22
Im looking for a tool that will run threw a folder and add a url at the bottom of all the image files. Any ideas of a program to do this?

---

### Post by Penguin Guy on 2009-08-22
You should investigate ImageMagick. Try something like [COLOR="Green"]convert *old.png* label:'*[www.yoursite.com](www.yoursite.com)*' -gravity South -append *new.png*[/COLOR]. You can get a list of all your files by doing something like [COLOR="Green"]find *.png[/COLOR], then you'll have to pipe the output of that through to ImageMagick somehow. Good luck!

---

### Post by cosmoshell on 2009-08-22
> **Penguin Guy said:**
> You should investigate ImageMagick. Wait a minute and I'll find the exact command for you. TY I dident know imagemagick could do that ill look into its commands.

---

### Post by cosmoshell on 2009-08-22
is there any simpler tools then image-magic that can add text to the lower right side of an image in bulk with variable sized images? I think it will take me many months to figure out how to do something like this with it. I had no idea that program did so much. And i cant find a tutorial anywhere for this.

---

### Post by Penguin Guy on 2009-08-22
> **cosmoshell said:**
> is there any simpler tools then image-magic that can add text to the lower right side of an image in bulk with variable sized images? I think it will take me many months to figure out how to do something like this with it. I had no idea that program did so much. And i cant find a tutorial anywhere for this.
No, I don't think so, but if you give a little time I don't mind creating a program for you. I need to know a little more about exactly what you want though. Also: what's the name of your site?

---

### Post by cosmoshell on 2009-08-22
phatch its in the repos it does what i need. very easy to use.

---

### Post by cosmoshell on 2009-08-22
> **Penguin Guy said:**
> No, I don't think so, but if you give a little time I don't mind creating a program for you. I need to know a little more about exactly what you want though. Also: what's th name of your site?

Creating the Watermark:
[[COLOR="Green"]convert -background LightGrey -fill Black -font ./TimesRoman.ttf -pointsize 14 label:'www.mysite.com' watermark.png[/COLOR]]("http://ubuntuforums.org/attachment.php?attachmentid=125806&stc=1&d=1250932058")
Are you happy with this font/size?

Applying the Watermark:
[[COLOR="Green"]composite -gravity southeast -dissolve 75 watermark.png new.png[/COLOR]]("http://ubuntuforums.org/attachment.php?attachmentid=125804&stc=1&d=1250932019")
Are you happy with this opacity?

wouldn't heart if you posted the script. I might be abled to use it for something else someday.

crap i cant delete this.

---

### Post by Penguin Guy on 2009-08-22
> **cosmoshell said:**
> wouldn't heart if you posted the script. I might be abled to use it for something else someday.
[Sure]("http://ubuntuforums.org/attachment.php?attachmentid=125808&stc=1&d=1250933490"). If you take a look inside you should find that there a variables near the top like [COLOR="Green"]OPACITY=75[/COLOR], you can easily change this with a text editor to something like [COLOR="Green"]OPACITY=40[/COLOR] if you would prefer that.

> **cosmoshell said:**
> crap i cant delete this.
:lolflag:

---

