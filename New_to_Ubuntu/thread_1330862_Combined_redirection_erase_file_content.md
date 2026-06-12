---
title: "Combined redirection erase file content"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by carlos.mendoza on 2009-11-18
Dear Community

I did this in Konsole:

sort < frutas.txt > frutas.txt      

the idea was took the file frutas.txt and order its contents in an alphabetical order but when I type this command:

cat frutas.txt 

nothing appear! the file's content is erased! 

Please, do you now the reason?

I am working in Kubuntu 8.04. Thanks in advance.

---

### Post by MonoDeem on 2009-11-18
Apparently I wasn't too far from the truth .. see the post below.

---

### Post by spikyjt on 2009-11-18
That'll be ```
echo -e $(sort < frutas.txt) > frutas.txt
``` note () not {} and you need to do something with it - i.e. echo ( the -e makes sure it keeps newlines etc intact). If you don't use echo, it will try to execute all the commands in the file! (which hopefully don't exist...

---

