---
title: "How to use the command line Find command?"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by L a r r y on 2010-04-08
I really prefer the locate command to the find command, simply because it is easy to use.

However, the locate's shortcoming is that it cannot find new files -- I even logged out and back in, and restarted the computer to no avail.

So I need the find command.  My understanding of the man page and of the help is very minimal because it is so complex.

OK, now I find that if I go to a specific directory and do a find HeyStupid.txt, it will display that file if it exists in that directory.

I have a content management system on my website, and I want to find where the cms stores a specific file in the images directory online.

I downloaded the images directory to my computer and attempted to find the specific file with ```
locate /home*specific-file.txt
```

But of course, locate does not locate newly acquired files.

```
find /home*specific-file.txt
No such file or directory
``` does not work.

The images directory on my website has several branches and several levels in each branch.  So I need some kind of recursive search tool.  Is there some way for that to happen with find?

---

### Post by shazbut on 2010-04-08
Doing a ```
sudo updatedb
```
updates the index for the locate command for new files. Locate should work after that.
Or you could try piping find through grep:
```
find /home | grep "filename or part thereof"
```

---

### Post by tom.swartz07 on 2010-04-08
Hiya!


First rule of using the command line; if youre not sure of a command, just type ```
man command-that-you-dont-know
```

locate reads one or more databases prepared by updatedb and writes file names matching at least one of the PATTERNs  to  standard  output, one per line.

the command 'find' searches the directory tree rooted at each given file name by evaluating  the given  expression from left to right, according to the rules of precedence until the outcome  is  known at which point find moves on to the next file name.


That being said, the Locate command would be best for your use. The man page will also list how you should use the command, along with any needed flags (i.e. -b for basename).


To exit out of the manual pages, just hit the Q key.

Have fun!

---

### Post by L a r r y on 2010-04-09
> **shazbut said:**
> Doing a ```
sudo updatedb
```
updates the index for the locate command for new files. Locate should work after that.
Or you could try piping find through grep:
```
find /home | grep "filename or part thereof"
```

Hey thanks for the tip on using sudo updatedb, for now I can locate new files with the locate command!

I will also check out the second code sample, using grep with find and see what that returns for me.

Thanks a million!

---

