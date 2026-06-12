---
title: "help with the tar command"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by DFord425 on 2009-04-24
I want to tar my home directory and save it to an external hard drive before i upgrade to 9.04. I seem to be having trouble doing it. If i navigate to my external hard drive in the terminal, i will want to use the -C $HOME flag? and the -f filename? i know i use tar -c to create an archive but im not sure about which other flags to use. And i know i do it as root.

---

### Post by ddrichardson on 2009-04-24
```
tar cvfz filename.tar.gz /home/username
```You'll probably need to do it from /home as sudo too.

Edit: to expand on that, c = create, v=verbose, f=archive file, z=gzip compression.

---

### Post by DFord425 on 2009-04-24
i need to be in my $HOME directory?

---

### Post by ddrichardson on 2009-04-24
You could do it direct to the removable drive if you want:```
tar cfvz /media/harddisk/filename.tar.gz /home/username
```

---

### Post by DFord425 on 2009-04-24
thanks, i tried it from my external and it worked. I had the filename and directory backwards, i was listing the filename second and the directory first, that was my problem. Thanks for your help.

---

### Post by ddrichardson on 2009-04-24
I often have to check tar with the man command because it seems illogical to tell it the filename to create before telling it what to put in it.

---

