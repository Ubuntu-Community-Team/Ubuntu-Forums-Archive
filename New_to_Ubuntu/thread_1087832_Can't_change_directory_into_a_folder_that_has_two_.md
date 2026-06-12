---
title: "Can't change directory into a folder that has two words in folder name"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by styxcoverbnd on 2009-03-05
Not sure if this is me being dumb or if you just can't do this but when I'm in the terminal and I try to change directory into a folder that has two words in the name (ie 'My Files') I receive an error that the folder doesn't exist. Is there a way to do this with out having to make all folder names one word long?

Note: Oddly enough this happens on my PCLinuxOS install too so I'm wondering if this is a linux problem.

---

### Post by kanikilu on 2009-03-05
You can use a backslash to escape the space. For example: ```
cd My\ Files
``` You can also use quotes: ```
cd "My Files"
```

// Edit - There are numerous introductory guides to the command line. For instance: [http://www.physics.ubc.ca/mbelab/computer/linux-intro/html/basics.html#names-with-spaces](http://www.physics.ubc.ca/mbelab/computer/linux-intro/html/basics.html#names-with-spaces)

---

### Post by avtolle on 2009-03-05
I don't know if I would call it a problem, but you could use, e.g. "My Files" (surrounding the name with quotation marks, making it a string literal); you could use My_Files as a name; there are other options as well.

---

### Post by styxcoverbnd on 2009-03-05
> **kanikilu said:**
> You can use a backslash to escape the space. For example: ```
cd My\ Files
``` You can also use quotes: ```
cd "My Files"
```

// Edit - There are numerous introductory guides to the command line. For instance: [http://www.physics.ubc.ca/mbelab/computer/linux-intro/html/basics.html#names-with-spaces](http://www.physics.ubc.ca/mbelab/computer/linux-intro/html/basics.html#names-with-spaces)

Excellent, thanks for the info

---

### Post by oldos2er on 2009-03-05
ext3 doesn't really like folder or file names with spaces in them. But you can use Tab completion to make it easy, type 'My' [Tab key] and it should mark the name in quotes for you.

---

### Post by tarps87 on 2009-03-05
Tab complete for file and directory name works really well :)
e.g.
My *tab*

It save a lot of time :)

---

### Post by lhowaf on 2009-03-05
The solutions listed work just fine but you shouldn't walk away thinking this is a "Linux problem." If you open the Command Prompt in Windows, you'll find the same behavior. Windows encourages bad practices (using separators in folder/file names) and then you pay a performance price for it. The underlying operating systems, though, hate spaces in filespecs.

---

