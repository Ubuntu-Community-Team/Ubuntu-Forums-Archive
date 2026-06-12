---
title: "copying files from multiple locations to a single destination"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by deostroll on 2009-05-12
Hi,

I am able to list all mp3 files in my file system. There are located inside various directories. How do I copy all those to a single directory.

I use the following command to list files:

```
find -iname *.mp3
```

---

### Post by swoody on 2009-05-12
Try this out:

```
cp *.mp3 /path/to/Folder
```

Let me know if that works. If you get any errors, post them here :)

---

### Post by deostroll on 2009-05-12
```
cp: cannot stat `*.mp3': No such file or directory
```

---

### Post by amac777 on 2009-05-12
Try this (replace /home/username/directory with your desired destination directory):

```
find . -name "*.mp3" -print0 | xargs -0 -I cp {} /home/username/directory
```

---

### Post by deostroll on 2009-05-12
```
xargs: {}: No such file or directory
```

---

### Post by amac777 on 2009-05-12
Sorry, I forgot something... modified it slightly as follows:

```
find . -name "*.mp3" -print0 | xargs -0 -I '{}' cp {} /home/username/directory
```

---

### Post by Lampi on 2009-05-12
Another way without using xargs

```
find SOURCEDIRECTORY -type f -name '*.mp3' -exec cp -v {} TARGETDIRECTORY \;
```

- Replace SOURCEDIRECTORY and TARGETDIRECTORY accordingly
- Sourcedirectory shall be the start point of your recursive search
- Only files will be copied, no directories

---

### Post by deostroll on 2009-05-12
```
find: missing argument to `-exec'
```

---

### Post by deostroll on 2009-05-12
Oops, the last command worked! Can someone explain it briefly?

---

### Post by Dill on 2009-05-12
```
find SOURCEDIRECTORY -type f -name '*.mp3' -exec cp -v {} TARGETDIRECTORY \;
```

Basically, you're finding files starting at a given source directory (/home, /, or wherever you want to start from), which are normal files (type -f), ending in .mp3 (-name '*.mp3). Then, you want to execute the cp command on each file, copying it (cp {}) verbosely (-v [basically printing output when it copies each file]) to a given target directory (i.e. the location to which you want to copy the files).

Cheers,
Dill

---

### Post by deostroll on 2009-05-13
does the "\;" have any significance?

---

### Post by Lampi on 2009-05-13
yes - it has to be there, to show your command interpreter where the find command closes. So you append this every time when you close your find line

---

### Post by unutbu on 2009-05-13
It indicates the end of the -exec command. 

Alternatively, you can also use this command:

```

find SOURCEDIRECTORY -type f -name '*.mp3' -exec cp -v {} TARGETDIRECTORY +
```

The plus sign at the end also ends the -exec command, but tells find to collect together many files before executing the cp command. The net effect is to reduce the number of times cp is called. This can save time if there are a lot of files.

---

### Post by Lampi on 2009-05-13
@unutbu: I know about the "+" replacement and it's advantages in speeding up the find process, and I tried this one yesterday before I posted the other solution, and I failed:
> 
```
sudo find /var/log/ -type f -name '*.log' -exec cp -v {} /tmp +
```
find: missing argument for "-exec".
```
sudo find /var/log/ -type f -name '*.log' -exec cp -v {} /tmp \;
```
will work as planed, **why**?

---

### Post by unutbu on 2009-05-13
Lampi, you are right. "-exec cp -v {} /tmp +" does not work.
Thanks for pointing this out. I've learned something.

According to [http://www.mydatabasesupport.com/forums/linux-misc/156940-argument-list-too-long.html](http://www.mydatabasesupport.com/forums/linux-misc/156940-argument-list-too-long.html), the {} must come at the end of the command. So a correct command which works around this limitation would be

```

sudo find /var/log/ -type f -name '*.log' -exec sh -c 'cp -v "$@" /tmp' blah {} +
```

Note that the blah is important. 
$@ takes all the parts (arguments) of the command except the first. The blah is a space-filler which is needed so that all the file names represented by "{}" get passed to "$@".

---

### Post by Lampi on 2009-05-13
nice trick :) just learned sth as well, thanks!

just to point this out to deostroll:

\; does mark the end of the find command, causing each -exec command to run in it's own process, thus it is much slower than "+"

But: "+" is more case sensitive than \; - so you generally should be on the safe side using \;

I hope I got this right ;)

---

