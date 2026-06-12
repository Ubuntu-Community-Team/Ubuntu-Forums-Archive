---
title: "epub to pdf converter ~ not sure where to put this"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by RandomP on 2010-08-29
Not exactly sure where I should put this topics, so mods move it if need be. 

Anyway, I am searching for a converter that does epub to pdf.... In all of my google searches I have found results for pdf to epub converters, but never the other way around. Can someone help me in this regard?

---

### Post by davidmohammed on 2010-08-29
does [this]("http://epub2pdf.com/") help?

---

### Post by RandomP on 2010-08-29
Cant exactly say so.... I am trying to figure out how to get it to start up, lol.

---

### Post by jtarin on 2010-08-29
[Documentation for installing and running.]("http://epub2pdf.com/README.epub2pdf.txt"). You need Java as its written in Java and its invoked by a script.> Unzip the epub2pdf zipfile in a location of your choice. 
It will create a directory called "epub2pdf".

Open a command prompt, change to the new "epub2pdf" directory, 
and invoke the program like so:

(Windows) 
epub2pdf.bat <path-to-epub-file>

(Linux / OSX / etc.)
chmod +x ./epub2pdf.sh 
./epub2pdf.sh <path-to-epub-file>

By default, the PDF is formatted for the Foxit eSlick Reader 
and is placed in your home directory

---

