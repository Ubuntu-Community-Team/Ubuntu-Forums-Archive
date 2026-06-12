---
title: "[SOLVED] Simple Copy from Command line"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by Nxion on 2009-01-01
I am trying to move multiple mp3 files from multiple directory's into one folder on my desktop. I can find them by doing this:

```
locate *.mp3
```

And it finds them, but when I wanted to move them I did this:

```
cp -R -v *.mp3 /home/mp3
```

It does not work. I get this error

```
cp: cannot stat `*.mp3': No such file or directory
```

I guess I am missing something in the syntax. Can anyone give me a hand please?

Thanks :)

---

### Post by lazyart on 2009-01-01
cp is looking in the current directory. :(

---

### Post by scorp123 on 2009-01-01
> **Nxion said:**
> ```
cp: cannot stat `*.mp3': No such file or directory
```

I guess I am missing something in the syntax. The path is wrong, obviously. If "locate" says that the MP3's are in a certain directory, then you have to put that directory name there too. Because "*.mp3" will assume your current location. And if there are no MP3's then the error is correct.

BTW, this stuff is highly inefficient. Why locate? And why cp? Why not put it all into one single command?

In plain English:
```
find all files underneath my current location and with 
an extension "mp3" or "MP3" and then copy them to /home/mp3/
``` ... And translated into a shell command ... 
```
find . -name '*[mM][pP]3' -print -exec cp -v {} /home/mp3 \;
```

Explanation for the above:
[LIST]
[*]First argument is always "where" ... so by giving a dot "." as argument I am saying: "right here"
[*]what follows is a regular expression that encompasses "MP3", "mP3", "Mp3" and "mp3" ... just in case
[*]if matches are found, you are informed and the names are printed out
[*]if matches are found, then a "cp -v" (verbose copy) is executed
[*]{} is a placeholder for the matches themselves
[*]\; is a placeholder for an enter keystroke, so the "-exec" argument knows where the command we want to execute actually ends
[/LIST]

---

### Post by Copernicus1234 on 2009-01-01
Sure.

First do this to create a file with all the file names:

**locate *.mp3 > myfile**

Then you read all the lines from the file, executing the copy command for each one:

[B]cat myfile | while read line; do cp "$line" . ; done
[/B]

The above will copy all the files into the directory you are currently standing in, so replace the "." with a path if you dont want that.

---

### Post by amauk on 2009-01-01
```
find "/current/path/of/mp3s/" -type f -iname '*.mp3' -exec mv {} "/new/path/of/mp3s/" \;
```

should do it

---

### Post by scorp123 on 2009-01-01
> **Copernicus1234 said:**
> **locate *.mp3 > myfile** ...  Not very efficient ;)

---

### Post by Copernicus1234 on 2009-01-01
> **amauk said:**
> ```
find "/current/path/of/mp3s/" -type f -iname '*.mp3' -exec **mv** {} "/new/path/of/mp3s/" \;
```

should do it

Just a warning here to complete newbies who read this: the typo above (mv instead of cp) will move the files instead of copying them. :)

> **scorp123 said:**
> Not very efficient ;)

I know, but where is the fun in using the actual find command... :)

---

### Post by scorp123 on 2009-01-01
> **amauk said:**
> ```
find "/current/path/of/mp3s/" -type f -iname '*.mp3' -exec mv {} "/new/path/of/mp3s/" \;
```

should do it I like the "-type f" idea ... you're right, without it we might catch directories too if they happen to have "mp3" somewhere in their name. Not sure OP wants that.

I totally forgot about the "-iname" option in GNU find, LOL.

```
find . -iname '*.mp3' -type f -print -exec cp -v {} /home/mp3 \;
```

---

### Post by amauk on 2009-01-01
> **scorp123 said:**
> I like the "-type f" idea
I always specify the type - just habit

(after accidentally wasting 4 hours grep'ing through the harddisk block device for some bit of text)

---

### Post by Nxion on 2009-01-01
Thanks to all who replied. I felt stupid asking the question because I should know that :)

---

### Post by Nxion on 2009-01-01
> **scorp123 said:**
> The path is wrong, obviously. If "locate" says that the MP3's are in a certain directory, then you have to put that directory name there too. Because "*.mp3" will assume your current location. And if there are no MP3's then the error is correct.

BTW, this stuff is highly inefficient. Why locate? And why cp? Why not put it all into one single command?

In plain English:
```
find all files underneath my current location and with 
an extension "mp3" or "MP3" and then copy them to /home/mp3/
``` ... And translated into a shell command ... 
```
find . -name '*[mM][pP]3' -print -exec cp -v {} /home/mp3 \;
```Explanation for the above:
[LIST]
[*]First argument is always "where" ... so by giving a dot "." as argument I am saying: "right here"
[*]what follows is a regular expression that encompasses "MP3", "mP3", "Mp3" and "mp3" ... just in case
[*]if matches are found, you are informed and the names are printed out
[*]if matches are found, then a "cp -v" (verbose copy) is executed
[*]{} is a placeholder for the matches themselves
[*]\; is a placeholder for an enter keystroke, so the "-exec" argument knows where the command we want to execute actually ends
[/LIST]


My thanks to you!

---

### Post by nemilar on 2009-01-01
Just for funsies, I'd probably do something like this:

```
find . -iname "*.mp3" | xargs cp -t /home/mp3 
```

---

### Post by Nxion on 2009-01-01
> **nemilar said:**
> Just for funsies, I'd probably do something like this:

```
find . -iname "*.mp3" | xargs cp -t /home/mp3 
```

Ill give that one a try too :) Thanks!

---

