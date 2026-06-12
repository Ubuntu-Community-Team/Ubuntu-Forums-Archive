---
title: "where does Ubuntu put source code?"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by mrcactu5 on 2009-04-09
I want to look at the source code for lilypond on my 8.10 installation.  Which folder do I look in?

---

### Post by Dougie187 on 2009-04-09
It doesn't download the source by default. Usually if you install a package from the package manager, it just downloads a .deb which is like a .exe installer on windows. You don't have to do a whole lot with it, mainly just double click it.

If you want to get the source, you can open a terminal and type this.
```
sudo apt-get source *packagename*
```

In this case, if the package is called lilypond then you would type
```
sudo apt-get source lilypond
```

Then you should get the source in the directory you ran this command from.

---

### Post by mrcactu5 on 2009-04-09
after a lot of Googling I tried 

```
>locate *.ly
```

A huge list of folders came up, but basically everything was located in usr/share/lilypond/2.10.33 

What is the difference between grep and locate?  What if I want to look inside the files without opening them one by one?

---

### Post by amauk on 2009-04-09
You can download source ISO's

Here's Intrepid
[http://cdimage.ubuntu.com/releases/8.10/release/source/](http://cdimage.ubuntu.com/releases/8.10/release/source/)

The source code is huge in comparison
(2.6G of source code to compile the standard 700M desktop CD)

---

### Post by feelshift on 2009-04-09
> What if I want to look inside the files without opening them one by one?  I think grep does that. Correct me if I'm wrong.

---

### Post by Dougie187 on 2009-04-09
> **feelshift said:**
> I think grep does that. Correct me if I'm wrong.

Locate searches for all files who's paths match some string. So for instance, if you did
```
locate ly
```
then you will get all files on your computer (that are in the locate database, which can be updated by typying "sudo updatedb") that have a path with ly in it, if your user name was something like lilly then you would get all of the files in your home directory because /home/lilly would match the ly string locate was using.

Now, grep on the otherhand, grabs a regular expression from a list of lines. Now in this case, you could do something like 
```
locate ly | grep lily
```
This should give you all of the files on your computer that have lily in the path.

You can use grep on particular files, by doing something like this
```
grep 'String' filelist
```
Where filelist can be a single filename or something like *, or you can pass some output from another command to it like I did in the previous command. You can read the man pages for further information on this though.

---

### Post by mrcactu5 on 2009-04-09
I guess finally... grep something with two words in it like 

```
>grep define relative *.scm
```

I am looking for the expression "define relative" in the *.scm files.

---

### Post by Dougie187 on 2009-04-09
> **mrcactu5 said:**
> I guess finally... grep something with two words in it like 

```
>grep define relative *.scm
```

I am looking for the expression "define relative" in the *.scm files.

Did you ever get your source?

---

### Post by mrcactu5 on 2009-04-09
Apparently... building Lilypond is really involved and usually you don't have to do it.  Instead you just modify a certain set of Scheme and Lilypond files in usr/share/Lilypond.

---

### Post by Dougie187 on 2009-04-09
I don't quite understand what you are doing anymore.

So you did or didn't get the source? I wouldn't think if you got the source you would be messing around in /usr/share/lilypond? Why would you be building lilypond? It is in the repos.

---

