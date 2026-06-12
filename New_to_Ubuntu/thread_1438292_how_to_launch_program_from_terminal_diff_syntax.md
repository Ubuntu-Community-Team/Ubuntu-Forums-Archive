---
title: "how to launch program from terminal diff syntax?"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by rppngears91 on 2010-03-24
Hi all, I sorta recently got on the Linux wagon....LOVE it!! lol

Ive googled this a few times but just cant seem to think of the magic words to type into google to help me.

I was wondering if there is a (basic simple) way to change the "syntax"? used to open a program inside a terminal 

JUST for example (in terminal) "Firefox" opens firefox 

I WANT 
                                                "FX" to open firefox

---

### Post by byStanderone on 2010-03-24
...try to focus on 'keyboard shortcuts' there are lots of things you can do bout it.

---

### Post by rppngears91 on 2010-03-24
true I could...but it a lot cooler when you launch something form a terminal.  I wanted to switch to linux because I was just plain bored of windows, I can make keyboard shortcuts in Windows. 

I dont wanna just change firefox, for instance when launch songbird from a terminal I have to type "./songbird" Id like to modify it so I just have to type "songbird"

Thats brings me to another question, but Ill try and work one at a time here.

---

### Post by patchwork on 2010-03-24
You can use aliases to do this.  See ```
man bash
```


EDIT:  If you add the program to /usr/bin, you don't need to preface it with ./

See also [http://www.hypexr.org/bash_tutorial.php#alias](http://www.hypexr.org/bash_tutorial.php#alias)

---

### Post by rppngears91 on 2010-03-24
hmmm Ive also notice if the nautilus file browser, a green arrow over executables??  Does that have anything to do with what I am trying to figure out?

---

### Post by rppngears91 on 2010-03-24
> **patchwork said:**
> you can use aliases to do this.  See ```
man bash
```
edit:  If you add the program to /usr/bin, you don't need to preface it with ./

see also [http://www.hypexr.org/bash_tutorial.php#alias](http://www.hypexr.org/bash_tutorial.php#alias)

thank you!!!!

---

### Post by patchwork on 2010-03-24
I don't have green arrows over my executables in Nautilus, so I don't know what you are seeing.

There are two different things going on here.

1.  Aliases allow you to create customized commands to run basic commands (i.e. showme for ls, if you're so inclined)

2.  Adding programs to directories specified by the $PATH variable in bash do not require explicitly telling the computer where to find the file (the ./ preface tells the computer to look in the current directory)  
Default $PATH:```
kevin@crystalpepsi:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```You can alter/add-to/remove-from the $PATH variable.  This is covered in the bash man page listed above, or you can find documentation out on the web.

---

