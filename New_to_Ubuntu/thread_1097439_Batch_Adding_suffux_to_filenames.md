---
title: "Batch Adding suffux to filenames"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by maphilli14 on 2009-03-16
Hey there ABT folk, I hope this is easy for someone.  I keep getting lost on searches with complicated language and syntax.

I'm trying to take a series of files that are from a digital camera like:

IMG_1001.CR2
IMG_1002.CR2
IMG_1004.CR2
IMG_1007.CR2
IMG_1009.CR2

IE - non contiguously numbered.  Then I'd like to either rename them or add a suffux in the form of:

IMG_1001--01.CR2
IMG_1002--02.CR2
IMG_1004--03.CR2
IMG_1007--04.CR2
IMG_1009--05.CR2

I've tried mcp/mmv to no avail, although this tutorial was very helpful:

[http://www.kriyayoga.com/love_blog/post.php/413]("http://www.kriyayoga.com/love_blog/post.php/413")

TIA,

Mike

---

### Post by kaibob on 2009-03-16
If you're looking for something with a graphic interface, pyrenamer will do what you want:

[http://www.infinicode.org/code/pyrenamer/](http://www.infinicode.org/code/pyrenamer/)

The following shell script will also do what you want. You have to change the target directory:

```
#!/bin/bash

cd /target/directory

count=001

for file in *.CR2 ; do
   basefile=$(basename "$file" .CR2)
   cp "$file" "$basefile--${count}.CR2"
   count=$(printf "%03d" $((count+1)))
done
```

I used copy (cp) rather than move (mv) as a precaution. Be sure to keep backups of all originals.

---

### Post by maphilli14 on 2009-03-16
Very cool, works perfect!  In fact I used ln -s as my next down stream app didn't care that the files were linked and not real!

Thanks much!

Mike

---

