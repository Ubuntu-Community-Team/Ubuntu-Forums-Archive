---
title: "unzip using a wildcard"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by supermooshman on 2010-08-29
hey all,

I am looking  to unzip a bunch of files in a folder (they all are seperate files)
I tried 
```
unzip  ./*zip
```
but I only got "caution: filename not matched:"

anyone knows what went wrong?

cheers

---

### Post by jtarin on 2010-08-29
Option # 1 : unzip multiple files using single quote (short version)

Type the command as follows:
```
$ unzip ‘*.zip’
```

Note that *.zip word is put in between two single quote, so that shell will not recognize it as a wild card character.

Option # 2 : unzip multiple files using shell for loop (long version)

You can also use for loop as follows:
```
$ for z in *.zip; do unzip $z; done
```

---

### Post by supermooshman on 2010-08-29
> **jtarin said:**
> Option # 1 : unzip multiple files using single quote (short version)

Type the command as follows:
```
$ unzip ‘*.zip’
```

Note that *.zip word is put in between two single quote, so that shell will not recognize it as a wild card character.

Option # 2 : unzip multiple files using shell for loop (long version)

You can also use for loop as follows:
```
$ for z in *.zip; do unzip $z; done
```

many gracias, it worked!

---

### Post by Emmtor on 2010-08-29
If you wish to get all the .zip files in a folder, you should use *.zip

So if you want to unzip all files in a directory, you should type

```
 $unzip /DIR/*.zip 
```

where '/DIR' is the directory you have the files.
you could just type 

```
 $unzip /*zip 
```

I hope that cleared things out for you.

---

