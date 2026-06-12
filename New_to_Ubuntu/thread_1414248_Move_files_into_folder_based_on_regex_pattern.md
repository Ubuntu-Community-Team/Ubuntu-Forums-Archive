---
title: "Move files into folder based on regex pattern"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by Mander on 2010-02-23
I have a big folder full of pdf files of research articles that I want to organize a little better.  Some of them have been renamed by BibTeX key; the rest have miscellaneous names, usually whatever cryptic code the site they came from used to identify them.  I've been using Mendeley to make it easier to identify the files, but ideally I want to have all the references in JabRef.

The first thing I'd like to do is move all the files that already have been renamed into a separate folder.  I'm sure I can do this with regex but I'm getting confused by the commands.  All of my BibTeX keys follow a pattern of author last name-last two year digits-first word of title, so if I could figure out how to use find to look for any number of alpha characters, then two numbers, then any number of alpha characters again, then .pdf it would work.

I tried this experimentally but it gave me no results:
```
find home/Documents/Articles -regex [a-z]+\b[0-9]{1}[0-9]{1}\b[a-z]+\.pdf | mv home/Documents/Articles/BibTeX
```

I'm sure I have just misunderstood how to use the regex keys, or put something in the wrong order. Can someone help me figure out what to do?

Thanks.

P.S. I've tried Referencer a few times in the past but it always just seems to crash without doing anything.  Are there other programs out there that can try to rename or recognize pdf files based on DOI, etc?

---

### Post by undecim on 2010-02-23
```
find home/Documents/Articles -regex [a-z]+\b[0-9]{1}[0-9]{1}\b[a-z]+\.pdf -exec  mv {} home/Documents/Articles/BibTeX \;
```

I believe that will do what you want, assuming your regex is correct.

EDIT: Also, if you want to ignore case, you can use -iregex

---

### Post by tver3305 on 2011-05-19
You can use a combination of grep, awk and xargs. I dont know how to to mv, but I had a problem that I had to delete a bunch of files based on the time stamp and I used the following command:
```
ls -ltr | grep 2011-05-11\ 13:21 | awk '{print $8}' | xargs rm -rf 
```

Maybe you will learn something form this.

---

