---
title: "Copying All But the First Line into a New File"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by senthilmuthiah on 2009-03-27
Dear All:

I have a text file and I would like to copy all the lines except the first one to a new text file.

I know I could do this using sed/awk but I wasn't able to figure out, how exactly would I write that.

Looking forward to some help!:)

---

### Post by senthilmuthiah on 2009-03-27
I think I have got it.  Thanks to [http://student.northpark.edu/pemente/sed/sed1line.txt](http://student.northpark.edu/pemente/sed/sed1line.txt)

That was a real nice compilation of what sed was capable of doing.

For my problem, I used, 

sed -n '2~1p' <oldFILE> >> <newFIlE>

Basically, this line outputs every 1 line starting from the second line to a new file called <newFile> :)

---

### Post by andrew.46 on 2009-03-27
Hi senthilmuthiah,

> **senthilmuthiah said:**
> I have a text file and I would like to copy all the lines except the first one to a new text file.

I see you have already found one sed answer but there is an easier way with sed:

```
sed 1d oldfile > newfile
```

You have to love sed :-).

Andrew

---

