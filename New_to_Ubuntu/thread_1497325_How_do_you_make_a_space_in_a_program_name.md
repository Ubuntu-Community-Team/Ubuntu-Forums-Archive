---
title: "How do you make a space in a program name?"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by harryliddic on 2010-05-30
I am trying to cd to a mounted program on sr0. The entry in mtab is GENESIS\0402.1 but in using that I get 'no file or directory' the disk name is GENESIS 2.1. I have tried double backslashes which reads out like the entry in mtab but get the same results. I am trying to put the source code into the /src directory and have gone through three pages of terminal combinations. Could some one tell me what I overlooked or just plain do not know.

---

### Post by quadproc on 2010-05-30
> **harryliddic said:**
> I am trying to cd to a mounted program on sr0. The entry in mtab is GENESIS\0402.1 but in using that I get 'no file or directory' the disk name is GENESIS 2.1. I have tried double backslashes which reads out like the entry in mtab but get the same results. I am trying to put the source code into the /src directory and have gone through three pages of terminal combinations. Could some one tell me what I overlooked or just plain do not know.
Normally in Linux or Unix systems, the space character is a delimiter.  Thus, that space in the identifier is seen as s delimiter and it breaks the identifier into two pieces.

To get around this, there are a few methods and the ones that work will vary depending on where you are trying to put the identifier.  For the shell bash, try quoting the identifier:
```
cd "GENESIS 2.1"
```You probably noticed that the mtab entry has a backslash in it; that backslash "escapes" the next 3 characters and treats them as an octal number.  Octal 040 is a space.  So you are seeing an encoded form of a space.

I am not sure that all of this will get you what you want, though; you said that the disk name is genesis but I am not sure what you mean by "name".  You may need to mount the disk so that you can use it; if so, you can call it anything you want when you mount it.

quadproc

---

### Post by lkraemer on 2010-05-30
Try:
```

cd GENESIS?2.1

```

The ? can substitute for any character or number.

lk

---

### Post by Ozymandias_117 on 2010-05-30
> **lkraemer said:**
> Try:
```

cd GENESIS?2.1

```

The ? can substitute for any character or number.

lk

The correct thing there would be ```
cd GENESIS\ 2.1
``` which tells it to ignore the space.

---

### Post by CharlesA on 2010-05-30
Quotes work too.

---

