---
title: "Saving 'man' documents"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by SteelCore on 2009-09-26
I'm trying to save some man pages so I can later have them printed.  I used
things like
```
laptop:~$ man man > man_document
```
and
```
laptop:~$ man man > man_document.odt
```
I even tried copy/paste. Overall everything works but I always get these funny characters like squares and strange looking question marks in the newly created document. Is there a solution for this?
Thanks in advance

---

### Post by QIII on 2009-09-27
What are you using to view the documents?

What character encoding are you choosing when viewing them?

---

### Post by kaibob on 2009-09-27
The following will do what you want. Unfortunately, it strips out certain punctuation marks. I assume this could be fixed by altering the arguments to the tr command, but I don't know how to do this offhand. Perhaps another forum member will have an idea. 

```
man man | tr -d '\001-\010\013-\037\177-\377' > man_document
```

---

### Post by SteelCore on 2009-09-27
I'm using the default right click>open with 'text editor' and Openoffice in case of the .odt document.  But I'm not sure about the character encoding, how can I find out?

---

### Post by Def13b on 2009-09-27
or,

```
man -E ascii man > output_file
```

---

### Post by SteelCore on 2009-09-27
> **kaibob said:**
> The following will do what you want:

```
man man | tr -d '\001-\010\013-\037\177-\377' > man_document
```

yes this worked perfectly, but what exactly happened? what's the difference between this and my command?

---

### Post by SteelCore on 2009-09-27
> **Def13b said:**
> or,

```
man -E ascii man > output_file
```

this worked perfectly as well.

---

### Post by kaibob on 2009-09-27
> **SteelCore said:**
> yes this worked perfectly, but what exactly happened? what's the difference between this and my command?

My suggestion piped the output through the tr utility, which removed unprintable characters. The suggestion by Def13b is better because it doesn't strip out necessary punctuation. Thanks Def13b.

---

### Post by SteelCore on 2009-09-27
> **kaibob said:**
> My suggestion piped the output through the tr utility, which removed unprintable characters. The suggestion by Def13b is better because it doesn't strip out necessary punctuation. Thanks Def13b.

I will refer to the man pages coz that's the proper way to do it :)
Thanks to all, though I do have another question. Do man pages differ between distros or are they, as I assume, kernel version dependent. So, for example, kernel 2.6.18 on any distro will have the exact same man pages. Thanks again.

---

### Post by KIAaze on 2009-09-27
man pages come with the installed program/package.
If it doesn't provide any, there won't be any man pages.

If the program versions are the same, they'll most likely have the same man pages.
But even then it depends on the packging.
A program installed from source might not have man pages for example.

example of the files installed by a debian package:
```
$ dpkg -L cowsay
...
/usr/share/man
/usr/share/man/man6
/usr/share/man/man6/cowsay.6.gz
/usr/share/man/man6/cowthink.6.gz
...

```

To view the contents of a gzipped man page, you can use zcat:
```
zcat /usr/share/man/man6/cowthink.6.gz
```

> Thanks to all, though I do have another question. Do man pages differ between distros or are they, as I assume, kernel version dependent. So, for example, kernel 2.6.18 on any distro will have the exact same man pages. Thanks again.

So, no, the man pages won't be the same in general between different distros, even if they use the same kernel.
The man pages for the kernel will most likely be the same however.

P.S.:
You can also convert man pages to html:
[http://www.fnal.gov/docs/UNIX/product_methodology/html/rev1_1a-mod/ups-71.html](http://www.fnal.gov/docs/UNIX/product_methodology/html/rev1_1a-mod/ups-71.html)

---

