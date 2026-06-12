---
title: "HTML links and Ubuntu HDD structure"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Martin Wang on 2009-02-02
Hi all,

I just switched from windows to Ubuntu. I have some questions about HDD links. Here is the story:

In my windows enviroment, I have many movies, mp3 in different drive C, D, E... and different directories. So I wrote a html to organize it. So, instead of going through different drive, directory, I simply use firefox to load the html and click the links to open the movie/mp3.  e.g. 
<a href="file:\\\c:\movies\movies1.avi"><img src=file:\\\c:\movies\movies1.jpg"></a> , so I just click the movies1.jpg, it will pop up the movies and I can view it.

My problems is now moving to Ubuntu, there will be no drive C, D, E.... all becomes /media/Drive_NAME.  So, it seems I need to change the html from file:\\\c: .... to file:///media/Drive_NAME... 

My question is there any easy way to do it? instead of modifying the HTML? is there a way to logic map /media/sde1 something to a letter C or something, thanks in advance.

Despite this, I am glad I switched to Ubuntu. It runs faster and you can run it from USB flash drive/HDD.  ... the only drawbacks is lack for good games...

---

### Post by ugm6hr on 2009-02-02
In theory you could use a symlink from /c: to /media/DriveName

However, that doesn't help, since your html uses file:\\\c: rather than file:///c:

I don't think Linux will cope with \ instead of /

---

