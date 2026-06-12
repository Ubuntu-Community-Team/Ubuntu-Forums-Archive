---
title: "finding and running programs in terminal"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by beew on 2010-07-31
Hi, this is a real beginner question. :)

Suppose I want to run a program in the terminal. I cd into the directory where the program is, now to actually run it, I notice that people sometimes type
```

$ sh programname
```

sometimes

```
$ ./programname
```

sometimes just 
```

$ programname
```

What is the difference?

Also, is there a simple way to find out the name of installed programs and their paths from the terminal? I frequently have to check synaptic > properties for this information that's why I prefer to use synaptic over sudo apt-get in the terminal. In the terminal I am not always sure whether something has been installed already or not, for example. :( Whereas in synaptic you can see whether it is marked or not. 

In short, is there an easy way to search for programs in the terminal even if you don't know their exact names? (I often do that in synaptic)  I know about dpkg -l xxx | less , but is there a way to narrow down the search based on partial information so that it doesn't spew out a few pages?

---

### Post by da burger on 2010-07-31
The 3 ways you mentioned all do slightly different things.

```
sh prog
``` Runs the text file prog through a program called sh which interprets it as code and executes that code (instead of sh I could use bash, python, ruby or many others depending on what interpreter I wanted to use)

```
./prog
```Runs prog through an interpreter mentioned on the first line using something called a [shebang line]("http://en.wikipedia.org/wiki/Shebang_(Unix)") or bash if there isn't a shebang line. It will also run the file if it is a compiled executable.

```
prog
``` Searches the path for a file named prog and runs it as above.

Any questions just ask.
Angus

---

