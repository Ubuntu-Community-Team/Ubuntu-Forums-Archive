---
title: "JPG automatic file extension"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by kid1000002000 on 2009-08-21
Hello World...

I am new to the forum and to ubuntu.  Thought I'd give it a try, and I am so far really impressed.  I should have ditched microsoft years ago.

One problem: tons of programs will not recognize any of my uppercase, .JPG files.  Only .jpg (lowercase) files are recognized.  I did a quick search on your forum, and yes- there are options to change all my file names, but this is not really practical: my olympus camera records in the .JPG format.  


Anyone have any ideas?  Is there some sort of code that will route all .JPG file extensions to a .jpg format automatically?  Being a new user, this is sorta frusturating in that I have so little experience with something like this (but I am willing to learn).

---

### Post by mike555 on 2009-08-21
can't you just rt. click on a .JPG and go to properties and set it to open with what you want?  the only trouble I had was if I put a .JPG picture on my desktop then tried to insert it in Thunderbird ,it didn't see it until I set it to see "all files"

---

### Post by kid1000002000 on 2009-08-21
for basic needs that might work.  but programs such as qtpfsgui just won't take it.  for buggy programs, is there a workaround to program linux to just treat both extensions the same way?

---

### Post by cariboo on 2009-08-21
I use the following script to change file names and extensions from upper to lower case:

```
#!/bin/sh
#Change upper case names to lower case
for i in *.[Jj][Pp][Gg]; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done
```

Copy the script into a text editor and save it as whatever you want to call it, I call it no_caps. Next copy the script to /usr/local/bin:

```
sudo cp no_caps /usr/local/bin
```

then make it executeable:

```
sudo chmod +x /usr/local/bin/no_caps
```

Now go into the directory with the upper case file names and extensions and run the script:

```
no_caps *
```

---

