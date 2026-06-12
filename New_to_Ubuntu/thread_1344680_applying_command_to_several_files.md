---
title: "applying command to several files"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by lemuriens on 2009-12-03
Hello,

I have a list of files, where part of the filename is sequentially numbered (i.e. file1,file2,file3 etc) and I want to echo a line to the end of all of them:

$echo "text" >> all the files

How do I do this? I tried "file*" but it didn't work.

Thanks!

---

### Post by pbrane on 2009-12-03
try this:

```

sed -i '$a\the end' file*.txt

```

this will append the text "the end" to every file1,2,3,4.txt in that directory.
To see what this will do without making changes to the actual files, run sed without the -i argument. That means edit the files 'in-place'.

---

### Post by kostaben on 2009-12-03
Another way would be using a loop:
```
for i in ./*; do  echo "text" >> $i; done
```

---

### Post by ukripper on 2009-12-03
As others explained. But if you want to do your way with echo, you can simply do this too:
```
echo 'text' >> file1 | echo 'text' >> file2 | ....so on
```

not practical though

---

