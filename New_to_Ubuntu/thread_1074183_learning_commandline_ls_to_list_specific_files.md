---
title: "learning commandline ls to list specific files"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by nycste on 2009-02-18
learning commandline ls to list specific files

i want help learning the basic commandline functions using terminal in ubuntu 8.10

i know 

ls, will show me the files in a folder

i know

ls -R, will list i think every file in my computer which i do not want

what i do want is to learn how to make a list of for example all my movies ending in .avi

ls -command to list all .avi files

thankyou

---

### Post by iaculallad on 2009-02-18
That can be accomplished using the wildcard character (*.*): To list all AVI files in your current directory, issue the command below:

Start searching on your current directory:

```
find . -name *.avi -print
```

Search from root

```
find / -name *.avi
```

That's using the **find** terminal command.

---

### Post by kk0sse54 on 2009-02-18
```
ls | grep '.avi'
```
which will list all files with .avi in your current working directory

---

### Post by Triggerhapp on 2009-02-18
```
ls -l *.avi
```
List, with size and owner name, etc, all files ending in .avi

```
ls *.avi
```
Same case, but without details, just the file names

```
find ~ -name "*.avi"
```
Find all .avi files in ~ (Your home directory)

---

### Post by glotz on 2009-02-18
```
man ls
```

---

### Post by Tek-E on 2009-02-18
You can also filter results using grep by doing so.
```

ls -l | grep .avi

```

---

### Post by Tek-E on 2009-02-18
DANGIT!  I before I finished posting C!oud posted what I was going to post before I did! :(

DARN YOU!! >:|  =)

---

### Post by kk0sse54 on 2009-02-18
> **Tek-E said:**
> DANGIT!  I before I finished posting C!oud posted what I was going to post before I did! :(

DARN YOU!! >:|  =)

Well at least the -l was a useful addition to display permissions :p. To the OP as you can see there are multiple ways for accomplishing what you want to do as well as endless combinations of further commands to display things like permissions or hidden files. I suggest you start out by reading the man pages to get a good idea of what a command does and the different options for it.

---

### Post by nycste on 2009-02-18
thanks for all the help so far, going to check it out tomm

i tested a few commands and now i just need to pick specific folders, and then learn to make a list.txt file of the data found

organizing that list.txt file alphabetically would be next and then possibly even merge it with my older lists

thanks again, seeya guys in the morning

---

### Post by Kain000 on 2009-02-19
a SUPER helpful thing to know when learning the command line espacially, is that most any command has a manual to explain it's use and operators ect.

just type 

```
man command
```

and you will get a manual laying out exactly how to use the command written usually by the developer.

tip: use q to exit the manual when you are done to return to your command line prompt.

---

### Post by Orion8 on 2009-02-19
Normally I Google questions like this and find what I need.  But I also found a little Linux Primer at Barnes and Nobles that was cheap and handy.  Not a giant "Bible of Linux" but a small handbook with examples. I have it at work (and am at home) or I'd just give you the title.  It is written for Red Hat but I can't say I've found anything that doesn't work in Ubuntu.  Anway, something like that might be worth the $9 it'd cost you.

---

### Post by jerome1232 on 2009-02-19
If you want to redirect the output to a file, this will put the output from ls to a text file called lsavi. If you wanted to append the output to a file you would use >> instead of >

```
ls *.avi > lsavi
```

---

### Post by Tek-E on 2009-02-19
This is really just another way of doing what everyone else had advidsed you to do.. but just a little trick I used.
Whenever I wanted to filter out some content when using ls I just created a very bare bones shell script like this.
```

#!/bin/bash
#filter
ls -l | grep $1

```
and used the following to make it executable without have to ad the ./
```

# chmod +x filter
# sudo mv filter /bin/

```
of course you could add any argument for ls when looking for files other than -l but at least it gives you a general idea.
now all I have to do it type
```

filter .txt

```
and it gives me the same result without have to continously type ls -l | grep .txt   ( It gets kind of annoying. )  The only problem is with this script being so bare you HAVE to cd to the directory you are wanting to filter content in.

Anyways like I said. Just though I would throw this out there

:p

---

### Post by Tek-E on 2009-02-19
> **nycste said:**
> thanks for all the help so far, going to check it out tomm

i tested a few commands and now i just need to pick specific folders, and then learn to make a list.txt file of the data found

organizing that list.txt file alphabetically would be next and then possibly even merge it with my older lists

thanks again, seeya guys in the morning

If you want to create a list of all the results you filtere out all you have to use is a re-direction symbol ( not 100% sure thats exact term )  so the command would then become
```

ls -l | grep '.avi' > list.txt

```

---

