---
title: "Using Commands in the same directory"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by BunnyBear on 2011-02-15
Ok I am tossing my new Ubuntu hat into the ring. I want to know what command do you use when you need to make a new folder but want to stay in the same directory. I know I can use mkdir to create subdirectories but then when I want to make a folder in  a specific directory (the same one) How do I do that?

Thanks for the help:popcorn:

---

### Post by TeoBigusGeekus on 2011-02-15
```
mkdir folder1
mkdir folder1/folder2
mkdir folder1/folder2/folder3
```
...and so on.

---

### Post by kn0w-b1nary on 2011-02-15
you would use:
```
mkdir ./foldername
```

Hope this helps!

---

### Post by Old *ix Geek on 2011-02-15
> **kn0w-b1nary said:**
> you would use:
```
mkdir ./foldername
```The dot slash aren't necessary, as the directory's name is relative to where the user is at the moment.

> **TeoBigusGeekus said:**
> ```
mkdir folder1
mkdir folder1/folder2
mkdir folder1/folder2/folder3
```
...and so on.That will work, but it's clunky. :) Try this instead:
```
mkdir -p directory1/directory2/directory3
``` and so on.

---

### Post by Mariane on 2011-02-15
If you mean you want to create your new directory in the directory from which you can see the reference one instead of creating it IN the reference one you do: 

```

cd ..
mkdir directoryname

```

Mariane

---

### Post by BunnyBear on 2011-02-16
[B]I want to MAKE several directories in my home directory. BUT I only want to use 1 command at the command line.

Remembering that my 'Home' directory is also the directory with my user name so that is my active directory thus /home/user(name

So the command that I use REMEMBER one command  would be;

mkdir directory directory1 directory2 somethingnew

Is this the right command?

Thanks have some Popcorn:popcorn:[/B]

---

### Post by freak42 on 2011-02-16
Why don't you try it out in a subfolder of your home, just in case it goes wrong?

Or look into the help pages of the mkdir command?

man mkdir

---

### Post by fabricator4 on 2011-02-16
> **BunnyBear said:**
> [B]I want to MAKE several directories in my home directory. BUT I only want to use 1 command at the command line.


That format will indeed make several directories in your home directory.  eg:

```

mkdir dir1 dir2 dir3 dir4

```

will make all four directories in your home directory, or wherever you happen to be at the time.

If you want to make directories with other subdirectories 'Old *nix Geek' had it right:  (Thanks!  :p )

```

mkdir -p dir1/dir2/dir3/dir4

```

will make all the directories in the tree down to dir4.  Interestingly, you can combine both of these:

```

mkdir -p dir1a/dir1b/dir1c dir2a/dir2b/dir2c dir3a/dir3b/dir3c

```

etc ad nauseum

If you want to make directories in another tree from where you are located you have to specify the full path from root onwards.

Chris

---

### Post by BunnyBear on 2011-02-16
Thanks! Since I am a newbie the initial one was what I used as an example and it worked! Thanks so much for your help and suggestions. What does the -p stand for? Now on to making files and inputting info in another directory all from the command line...ugh!

---

### Post by fabricator4 on 2011-02-16
> **BunnyBear said:**
> What does the -p stand for? 

'-p' is for '--parent'  It means make all the parent directories all the way down to the last one if they don't already exist.

You can look at the manual for commands by typing:

```

man commandname

eg: 
man mkdir

```

The interface for man is rather archaic so it may seem a bit strange. Type ':' and you'll get a command bar at the bottom of the screen.  In this bar type 'q' to quit.  You just need to type the colon and the question mark on their own, not the single quote marks.

You can also use man to find things in the manual pages that you don't even know the command name for.  For example if you want to find the command(s) for copying files you can use the following:


```

man -k "copy files"

```

That should get you started. You'll find the man pages rather terse and confusing at first until you learn the typical structures.  Sometimes the the man page will give a location where you can look at a more comprehensive (and friendly) manual page that may give examples, and you should follow these up if you are confused.

If you really get stuck, of course come back and ask questions.

Chris

---

### Post by BunnyBear on 2011-02-16
Thanks! Been searching how to make a file but found nothing that makes sense

---

### Post by Old *ix Geek on 2011-02-17
I know you've marked this thread solved, but then I saw this:

> **BunnyBear said:**
> Been searching how to make a file but found nothing that makes sense
What do you want to do, exactly?

---

### Post by BunnyBear on 2011-02-17
I wanted to make a hard link and a soft link  and then add text to a file

---

### Post by TeoBigusGeekus on 2011-02-17
```
man ln
```
to learn about links.

```
echo some text > file.txt
```
Adds the string "some text" to file.txt deleting everything else from the latter. If the file doesn't exist, it is created.

```
echo some more text >> file.txt
```
Appends the text "some more text" to file.txt, i.e. previous content of file.txt is kept.

---

