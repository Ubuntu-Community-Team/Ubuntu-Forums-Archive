---
title: "Opening PDF from Terminal"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by TheEvilOne6620 on 2009-07-25
I am trying to figure out how to open PDF files from the terminal, or basically any type of file.  Videos , Movies, whatever.  Is this possible?

I know you can launch apps from the terminal so I was wondering if this is possible also.

I recently cut and pasted a pdf file to my documents folder and now when i go to it it just loads foreve and the new pdf never shows up????

If i browse to it in terminal and do a ls command it hsows that it is there but i dont no how to open it

Ive tryed gnome-open and it doesnt work

Any help would be great

---

### Post by wojox on 2009-07-25
Type in Terminal:

```
man pdftohtml
```

---

### Post by _Purple_ on 2009-07-25
From terminal, go to the folder which has the pdf file and type the following:
```
evince filename
```
or 
```
acroread filename
```

Is this what you are looking for?

---

### Post by liquidmonkey on 2011-11-14
just helped me out, THANKS!

---

### Post by oldos2er on 2011-11-14
Closed, necromancy.

---

