---
title: "Batch images to one pdf HOWTO"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by jalirious on 2010-10-07
If you have a bunch of images and want to make a single pdf from them, here is the best way I found. Needs jre.

Copy and paste what's between the stars as a textfile named 'whatever'.
****************
#!/bin/bash
for x in ./*.jpg
do
    echo $x to ${x}.pdf
    convert $x -quality 75 ${x}.pdf
done

echo Merging...
java tool.pdf.Merge *.pdf
****************
chmod 777 whatever
./whatever

If merging fails you can set the java path, Or..

sudo apt-get install pdftk
pdftk *.pdf cat output final_file.pdf

- That's it.

There are numerous ways to do this, doubtless each with its merits, this worked for me, so I put it up for future reference.

---

### Post by paddy100 on 2011-01-04
Great script, one question.....
some of my file name have spaces in them, and this script didnt convert them, how do i get round this??

Help is greatly appreciated

---

