---
title: "Clicking on a web link"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-01-01
hello :) Sometimes when I click on a link a message box comes up saying "This link needs to be opened with an application" and I have to choose one. What does this mean? Also I downloaded skydomes and the caps for the cube and I don't know where the files need to go or how you install them. Any help would be really appreciated :) Thanks.

Oh and HAPPY NEW YEAR :)

---

### Post by Methuselah on 2010-01-01
> **ThePinkWitch said:**
> hello :) Sometimes when I click on a link a message box comes up saying "This link needs to be opened with an application" and I have to choose one. What does this mean? Also I downloaded skydomes and the caps for the cube and I don't know where the files need to go or how you install them. Any help would be really appreciated :) Thanks.

It means the link is not a web page so firefox cannot open it itself.
This might happen when you click a .pdf file, word document or any number of non-html things.

---

### Post by ThePinkWitch on 2010-01-01
Thankyou..so I need the equivalent of adobe reader or something?

---

### Post by Methuselah on 2010-01-01
Yes...for pdf files 'evince' will do but adobe also provides an adobe reader and browser plugin (that'll allow firefox to appear open it within its window).
But depending on the file type in question a different program is needed.

---

### Post by ThePinkWitch on 2010-01-01
Thankyou..I clicked on a gnome.org link in another post in this forum and got that message. I'll get Adobe and see if that works.

---

### Post by beegary on 2010-01-01
Try this...
Right click the link, and select Copy Link Location
Then open a text editor (e.g. from terminal type gedit) or openoffice writer
Press ctrl+v or right click and paste
Look at the link and see the type of file that is linked i.e. *.pdf
If your are not sure what the extension is paste the link here and \ill try to help:P

---

### Post by ThePinkWitch on 2010-01-01
> **beegary said:**
> Try this...
Right click the link, and select Copy Link Location
Then open a text editor (e.g. from terminal type gedit) or openoffice writer
Press ctrl+v or right click and paste
Look at the link and see the type of file that is linked i.e. *.pdf
If your are not sure what the extension is paste the link here and \ill try to help:P

Thanks for answering..I did what you said and this is what I got

apt:gnome-do

---

### Post by beegary on 2010-01-02
Im not entirely sure, someone else will probably be able to help more but it seems you need Gnome-Do (but I think this is just an application launcher).
Try (in terminal):
```
sudo apt-get install gnome-do
```Sorry I cant help any more

If this doesnt help perhaps post a link to the page where you found the link

---

### Post by ThePinkWitch on 2010-01-03
> **beegary said:**
> Im not entirely sure, someone else will probably be able to help more but it seems you need Gnome-Do (but I think this is just an application launcher).
Try (in terminal):
```
sudo apt-get install gnome-do
```Sorry I cant help any more

If this doesnt help perhaps post a link to the page where you found the link

Thankyou very much for your replies :)

---

