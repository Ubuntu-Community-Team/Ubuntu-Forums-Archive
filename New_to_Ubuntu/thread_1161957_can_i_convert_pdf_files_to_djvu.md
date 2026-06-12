---
title: "can i convert pdf files to djvu?"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by stinger30au on 2009-05-17
i have a few hundred pdf files scattered thru many directorys. the pdf files range from 80 meg to 600 meg in length


is there a simple command i can run from shell to convert these pdf files to djvu?


i dont mind if i have to do them one at a time. it will take ages if i have to though thats all.



is there a scrpit or something i can use to scan my directorys and convert all the pdf files it goes to djvu files?

i dont really mind if there is no script to do it and i need to do each manaually, so long as i can do it.


thanks

---

### Post by brian_p on 2009-05-17
> **stinger30au said:**
> 

is there a simple command i can run from shell to convert these pdf files to djvu?

```
apt-cache search djvu
```

```
apt-get install pdf2djvu
```

---

### Post by stinger30au on 2009-05-17
thanks

---

### Post by stinger30au on 2009-05-18
i didnt write this, but i tested it and it works


# !/bin/sh

for i in *.pdf ; do
j=`basename $i | sed -e 's/\.pdf//'`
pdf2djvu --dpi=400 -o $j.djvu $i
done



make sure pdf2djvu is installed first

sudo apt-get install pdf2djvu then run the script.
it will go thru the directory and convert all pdf files to djvu and keep the
same file name as the original.

*make sure there is no spaces in the file name* this script wont handle it

---

### Post by TarNation1101 on 2010-10-21
Thank you! 
I've been looking for a while how do batch convert to djvu. 
ubuntuforums is quickly becoming my goto source for help

---

