---
title: "Help with cp and wildcards"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by jratliff on 2009-02-15
I have a typical music directory structure genre->artist->album->files and artwork. This command:

```
cp -R /media/fatdata/flac/ ./
```

copies everything.

I want to copy just the artwork and try

```
cp -R /media/fatdata/flac/*.jpg ./

```

but get
```

cp: cannot stat `/media/fatdata/flac/*.jpg': No such file or directory
```

I've tried *jpg and that didn't work either.

I know this is a complete newbie question, but I hope I'm in the right forum for that.

Any help is appreciated.

---

### Post by x33a on 2009-02-15
post the output of:
```
ls -l /media/fatdata/flac/
```

---

### Post by jratliff on 2009-02-15
```
drwxrwxrwx  42 dad users 32768 2009-02-13 16:36 Alternative
drwxrwxrwx 148 dad users 32768 2009-01-31 19:13 Blues
drwxrwxrwx   5 dad users 32768 2008-12-17 07:56 Christmas
drwxrwxrwx   3 dad users 32768 2008-12-24 08:41 Clash
drwxrwxrwx  22 dad users 32768 2008-12-17 11:35 Classical
drwxrwxrwx  30 dad users 32768 2008-12-17 07:56 Compilations
drwxrwxrwx  20 dad users 32768 2008-12-17 07:51 Country
drwxrwxrwx  59 dad users 32768 2009-01-23 08:08 Jazz
drwxrwxrwx  60 dad users 32768 2009-01-31 19:14 Pop
drwxrwxrwx  26 dad users 32768 2009-01-31 19:14 r&b
drwxrwxrwx  21 dad users 32768 2008-12-17 07:38 Reggae
drwxrwxrwx  67 dad users 32768 2008-12-28 21:56 Rock
drwxrwxrwx   7 dad users 32768 2008-12-17 07:19 Soundtrack
drwxrwxrwx  87 dad users 32768 2009-02-13 17:52 Vocal
drwxrwxrwx  11 dad users 32768 2008-12-17 06:08 World
```

---

### Post by x33a on 2009-02-15
These are all directories, so there aren't any jpg's in this directory. hence, you are getting this error. you have to cd into each sub-directory and then copy the jpg's.

or you can try:
```
cp /media/fatdata/flac/*/*.jpg ./
```

---

### Post by jratliff on 2009-02-15
Thanks for the suggestion, but I get the same message.

Is it not possible with the cp command (or some equivalent) to copy just the jpg files from one set of directories to another and replicate the directory structure?

I'm thinking 
```
cp -R /dir1/*.jpg /dir2
```

---

### Post by Old *ix Geek on 2009-02-15
I'm half asleep and haven't finished my first [very large] cup of coffee yet, but a quick try worked, so give this a whirl:

First of all, create a directory somewhere OTHER than in /media/fatdata/flac/.  The reason for this is to avoid including the new directory in the steps below.

So, for example:
```
mkdir /media/fatdata/AllFiles
```

Now position yourself in /media/fatdata/flac:
```
cd /media/fatdata/flac
```

Finally, do this:
```
for directory in `ls`
do cp -R $directory/*jpg ../AllFiles
done
```

That SHOULD do it. :D

EDIT: I didn't test this with subdirectories.  Do you have subdirectories under each category, or just files?

---

### Post by jratliff on 2009-02-15
Thanks for your help Old *ix Geek. I got an error for each subdirectory similar to this one:

```
cp: cannot stat `Alternative/*jpg': No such file or directory
```

I'm guessing this is why you asked if I have subdirectories under each category?

You're taking me into new territory. Now I need to investigate what mode the $ initiates in the first place, what the $ means in $directory, and what the backticks are for.

My operating system trajectory has been from some mainframe in the 70s that ran Fortran->CP/M->MSDOS->Windows & Mac. That last move was in the 80s, so it's been a while since I've been at a command prompt.

---

### Post by sisco311 on 2009-02-15
you can use the fined command:
```
find /media/fatdata/flac/ -name "*.jpg" -exec cp {} /path/to/dest/dir \;
```

---

### Post by jratliff on 2009-02-15
Thank you Sisco311.

That did almost what I had hope for. I wasn't clear about this part: I'd like to recreate the directory structure during the copy.

---

### Post by apmcd47 on 2009-02-15
Try this (untested)
```

find /media/fatdata/flac -depth -name '*.jpg' -print | cpio -pmdv /path/to/dest/dir

```
This assumes you have cpio installed on your system.
The find will create a list of jpg files and pass them through the pipe to cpio.
The cpio will create a duplicate file structure under /path/to/dest/dir and copy the files from the original location keeping the modification time. 
This should preserve symbolic links.

I'm sure you can do the same with pax but I don't know pax at all.

Andrew

---

### Post by jratliff on 2009-02-15
Thank you so much apmcd47.

This is exactly what I needed. This command is going to save me tons of time (and unwanted trips back into Windows). I really appreciate it.

Now if I could just figure out how to mark this thread solved...

---

### Post by sisco311 on 2009-02-16
> **jratliff said:**
> Thank you so much apmcd47.

This is exactly what I needed. This command is going to save me tons of time (and unwanted trips back into Windows). I really appreciate it.

Now if I could just figure out how to mark this thread solved...

[thread=1039481]Thanks and Solved have been disabled due to problems with the database.[/thread]

---

