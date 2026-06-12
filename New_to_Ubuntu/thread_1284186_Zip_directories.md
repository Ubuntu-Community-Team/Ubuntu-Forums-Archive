---
title: "Zip directories"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by Kayone on 2009-10-06
I feel dumb for asking but I don't want to burn up disks testing... I fail :D

Ok, I am porting files over to a windows box from a linux box. The file names are fairly long and they are getting cut off. I would like to zip everything up so the files keep their names. 

I am wondering if gzip -r will preserve all of the file names for the files AND directories (or does it only go in and compress the files individually and leave the directories alone)?

Thanks guys!
I would just test it out but I can't unfortunately.

-K1

---

### Post by bswilson on 2009-10-06
The short answer is **yes**.

By default, gzip preserves the names of files and directories.  You can ensure this is enforced by using -N also:

```
gzip -Nr ./your-stuff
```

Hope this helps.

---

### Post by ptn107 on 2009-10-06
```
tar cvzf archive.tar.gz path-to-files
```

ex:
```
tar cvzf documents.tar.gz /home/phil/Documents
```

tar is recursive by default

[1] man tar

---

### Post by Kayone on 2009-10-06
Thanks! I figured it would be something that ridiculously simple :)

---

### Post by Kayone on 2009-10-06
[COLOR=Red][B][SOLVED]

[COLOR=Black]Thanks guys![/COLOR]
[/B][/COLOR]

---

