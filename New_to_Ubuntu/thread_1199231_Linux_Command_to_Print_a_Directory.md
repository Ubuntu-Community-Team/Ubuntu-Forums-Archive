---
title: "Linux Command to Print a Directory"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by TunaCanTommy on 2009-06-28
I'm almost embarrassed to ask this:

How do I print the contents of a directory ? ?

I couldn't find anything in Nautilus and I did a man search on; pwd, cat, lpr and ls.  Nothing obvious jumped out at me.

I'd like to have a hard copy of some music and movie directories on my hard-drive but can't work out a linux command to do it.

---

### Post by WRDN on 2009-06-28
To list files:

```
ls [directory] | lpr
```

Just use "ls" if you are in the directory you want to list the contents of.

Use the "-a" option to list all files (normal and hidden files):

```
ls -a [directory] | lpr
```

---

### Post by jerome1232 on 2009-06-28
I don't remember how to actually print from a terminal but an easy way would to be to send the results of ls to a text file than print the text file.

ie

```
ls -a /path/to/directory > ls-results
```

Then open the text file "ls-results" with your fav text editor and print from there.

---

### Post by linuxmagick on 2009-06-28
If you're looking to print out a physical copy to a printer, then you could use ls to get the list of directories and then pipe that list over to the lpr command.  This requires that you have your printer properly configured.  By this, I mean that you're already able to print to it from Ubuntu.

ls -a | lpr

---

### Post by theozzlives on 2009-06-28
```
ls > list.txt
``` Then print list.txt.

---

### Post by Nervouswreck on 2009-06-28
Tuna can, I'm pretty sure you meant a paper copy when you said "hard copy." You can pipe the output of the ls command to the printer. That is to say
[code]prompt$ ls | lpr [options]

---

### Post by TunaCanTommy on 2009-06-28
Thanks guys . . . that got it.  I needed to use $ ls | lpr.
Also sending the output to a text file is a good way to go.
Solved my issue, Thanks again . . .

---

### Post by mikechant on 2009-06-29
The following thread from this site's archives discusses how to add a directory listing function to Nautilus for convenience:
[http://ubuntuforums.org/archive/index.php/t-1107462.html](http://ubuntuforums.org/archive/index.php/t-1107462.html)

---

### Post by TunaCanTommy on 2009-06-30
@mikechant

Got it, did it, works like a charm . . . thank you very much!

What is it you say - " . . and Robert's your mother's brother !"

---

