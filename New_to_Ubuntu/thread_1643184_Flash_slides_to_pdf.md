---
title: "Flash slides to pdf?"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by Mariane on 2010-12-11
I'm having big problems with some flash (SWF) slides. 
The slides are the one called "Flash files (powerpoints)" there: 
[http://kemst.hi.is/gods_and_goddesses/](http://kemst.hi.is/gods_and_goddesses/)

I can apparently download them but I can neither view them online nor offline nor
print them to pdf. 

avidemux won't open these files
vlc won't open these files
lpr -P PDF filename.swf
returns without error but does nothing
lpr -P PDF filename.swf > filename.pdf
creates a pdf file which cannot be opened. 

Mozilla opens the file but displays only the first slide. 

Please help! Watching the conference videos without being able to see the slides makes no sense! 

Mariane

---

### Post by Mariane on 2010-12-11
Ron999 told me I could view them in Mozilla, and that I had to click on a slide to see the next one. So now I have them! 

I would still like the pdf converter, though, for now I have to make a screenshot of every slide, edit it to trim off the edges, paste it in OpenOffice and then export to pdf. It works but it is time-consuming. 

Mariane

---

### Post by diablo75 on 2010-12-11
First, Flash/Shockwave files are not "Powerpoints", as they suggest on that website.  Powerpoint is a program by Microsoft that is bundled with their Office suite of software and it is used to create simple slideshows (and nothing more) for office presentations and such.  Shockwave, however, is a multimedia plugin for web browsers that acts as a platform for interactive video/audio content, which you could use to present something simple like a series of pictures that progress in order with a mouse click, up to and beyond full feature arcade games like pacman and such.  Shockwave is not typically used for publishing slideshows except in cases where you want to use a web browser as your presentation software, instead of Powerpoint or Open Office Impress.

That being said, SWF files can be opened directly by any web browser, so long as that browser has the Shockwave Flash plugin installed.  Just save the SWF file and then open it directly with Firefox.

As for converting the SWF file into a PDF, your best bet (since SWFs technically are not slide shows) is to open the SWF file in firefox, take a screenshot of each slide and import those screenshots into a new word document in Open Office, and then export that document as a PDF.

---

### Post by Mariane on 2011-03-02
That's what I ended up doing... I took a screenshot of every slide with ksnapshot, saved them as a sucession of .png files, and then put them in an Open Office document later exported to .pdf. 

Tedious, and the result was a large pdf, but it worked. 

Thanks to all of you. 

Mariane

---

