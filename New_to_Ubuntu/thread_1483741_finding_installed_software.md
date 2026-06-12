---
title: "finding installed software"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by ronlayt on 2010-05-14
I installed the pdf2djvu program. How do I find it and use it. How is code entered in the machine? I just loaded ubuntu 10.04 onto my acer notebook and everything is running just fine. I have no experience with this os compared to microsoft. Thanks in advance.

---

### Post by ronlayt on 2010-05-14
How do I find and operate this program? I loaded it from "get software". I have just loaded 10.04 onto my acer notebook. All is well and everything is running fine. I have zero experience with UBUNTU but way too much with Microsoft. Where do I start to convert a pdf to a djvu document? How do I input code into the machine? Thanks in advance!

---

### Post by Locke_99GS on 2010-05-14
If it has a gui, it should (most do) add itself to the menu. Check Application->Accessories or Application->Office. If it doesn't provide a gui front end, it may be command line only. Try invoking it by name from a shell.

---

### Post by ranch hand on 2010-05-14
I am not familiar with that program but it should be listed in your Applications>Office menu if it is a program with a gui.

If not open your terminal Applications>Accessories>Terminal and;
```

pdf2djvu

```
should pull it up.

If it is just a reader the default works just fine,  Just click on the file or the link and it will be up and running.

---

### Post by ronlayt on 2010-05-14
OK Where and how do I enter this code? I found terminal but I have no experience with code.

---

### Post by patchwork on 2010-05-14
To find information on how to use the program, type in at the terminal prompt
```
man pdf2djvu
```

You can type 'q' to quit the manual page.

The man page will also detail the command line options and syntax for starting the program, assuming this program has a documented man page.

---

### Post by Ozymandias_117 on 2010-05-14
It's not in Applications -> Office or perhaps Applications -> Graphics?

---

### Post by ronlayt on 2010-05-15
I did as patchwork advised and the manual showed up alright. My question is how do I use the program? I don't understand the commands-is there a tutorial on using the terminal? If I have a pdf up and I want to convert it to djvu what do I do? Thanks for your patience everyone.

---

### Post by ranch hand on 2010-05-15
I am not sure what you are looking for here.  The man pages are usually pretty good.  I will admit that a certain fluency in geek is sometimes needed (I am pretty new myself).

As for your app I ran a quick search and found this;

[http://djvu.sourceforge.net/](http://djvu.sourceforge.net/)

Check their documentation.  They ought to know what they are talking about.

I do not want to be presumtious but here are some other links you may find interesting;

This is a good one to kind of set your mind in the right path;
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

These 2 have enough info to keep you busy for a year or so, if you poke around you will find what you need;
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

[http://ubuntuforums.org/showthread.php?p=7157629](http://ubuntuforums.org/showthread.php?p=7157629)

This is my personal favorite and I highly recommend the first book listed, very handy.  I think I will buy a copy.
[http://www.linuxlinks.com/article/20090405061458383/20oftheBestFreeLinuxBooks-Part1.html](http://www.linuxlinks.com/article/20090405061458383/20oftheBestFreeLinuxBooks-Part1.html)

---

### Post by Ozymandias_117 on 2010-05-15
Please don't make duplicate threads... 
[http://ubuntuforums.org/showthread.php?t=1483751]("http://ubuntuforums.org/showthread.php?t=1483751")

---

### Post by cariboo on 2010-05-15
Please don't create multiple threads on the same subject. I have merged your two threads.

Pdf2djvu is a command line program. There is no gui, to see the options if you open a terminal and type pdf2djvu, it will should give you the command line options. the most basic command would be:

```
pdf2djvu -o <djvu-file> <pdf-file>
```

where <djvu-file> = the name of the output file and <pdf-file> = the name of the file you want to convert.

---

### Post by ronlayt on 2010-05-15
Thanks for all the links Ranch hand. I downloaded the ubuntu guide-good info and I found a lot I needed.Ozymandias_117 and Cariboo907-sorry-my mistake-I didn't notice that the first post loaded and I reposted. Thanks for the help everyone. Its greatly appreciated.

---

### Post by patchwork on 2010-05-15
I've never used it, but according to the man page it has quite a few options.  The general syntax for converting a pdf to a djvu file seems to be 
```
pdf2djvu -o foo_djvu_filename foo_pdf_filename
```

Obviously, there are a lot of options as to customizing the output, and the man page covers those in detail.

---

