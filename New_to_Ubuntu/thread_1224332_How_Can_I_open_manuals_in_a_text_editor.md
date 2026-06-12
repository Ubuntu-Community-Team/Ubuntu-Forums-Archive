---
title: "How Can I open manuals in a text editor?"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by conradin on 2009-07-27
Hi all, 
I want to open the manuals in a text editor such that I might search them for very specific contents quickly, or possibly add my own notes. 

How can I do this?

---

### Post by Zenze on 2009-07-27
you could do:
```
man command | grep searchword
```

or even just look at the man page online in a browser

---

### Post by quinnten83 on 2009-07-27
do you mean you want to be able to read a man page?
you can do man "command" > filename.txt
that will save the man page to a textfile which you can read later on.

---

### Post by llamabr on 2009-07-27
> **quinnten83 said:**
> do you mean you want to be able to read a man page?
you can do man "command" > filename.txt
that will save the man page to a textfile which you can read later on.

This actually won't work very well, since you'll get all of those formatting chars, too.  Try:

```
man man | col -b > man.txt
```

---

### Post by wojox on 2009-07-27
[http://www.linuxmanpages.com/](http://www.linuxmanpages.com/)

---

### Post by llamabr on 2009-07-27
> **wojox said:**
> [http://www.linuxmanpages.com/](http://www.linuxmanpages.com/)

Right.  Googling a command will also usually return its man page.

If you just want to search for a phrase while inside of a man page, you use the / key.

Actually, ```
man man
``` is a pretty good read.  So is ```
man bash
```

---

### Post by Mornedhel on 2009-07-27
Some editors (or rather, some IDEs) have support for man pages, for instance Emacs.

---

### Post by beren.olvar on 2009-07-27
a quick trick is to note that man is just a less over a "file" (a pipe really).
you can either try to find that file, or for example 

$ man less
once inside man, press s
it will prompt for a log file, then you put /tmp/man-less, for example
then exit, and you have the man page in /tmp/man-less

If you want to change the man page for good (which I don't recomend) you will have to look for the specific file, in my case /usr/share/man/man1/less.1.gz, for example

you can do
locate man|grep <command> |grep gz
to find it

cheers

---

### Post by conradin on 2009-07-27
Wow I love the forums,
thanks for the great responses! quinnten83's post was pretty much what I wanted. I'm not always on-line when I'm using Ubuntu I'll check the rest of them out soon. Much Thanks to ALL!!!

---

### Post by niteshifter on 2009-07-27
Hi,

Just for the sake of having "all" the various ways to read and capture man output, here one that's missing:

Click the help icon on the top panel. Type man <command> in the search box. Click anywhere in the displayed man page, type Ctrl-A then Ctrl-C. All the text is now on the system clipboard, paste it wherever.

Note that the above does not work with info <command>.

---

