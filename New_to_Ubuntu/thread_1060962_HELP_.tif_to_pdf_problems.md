---
title: "HELP .tif to pdf problems"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by monstereel on 2009-02-05
I am new to Ubuntu and have run into a major problem.  I regularly need to download large .tif files and convert to pdf, the files are large architectural prints and contain as many as 20 pages.  First, they take forever to download and then when I open them in Document Viewer my entire computer freezes for 3-5 minutes while it tries to open.  Second,  I can't find a pdf printer that will convert the documents and keep them the original size, everything wants to reduce to 8.5x11.  Is there a way to convert tif to pdf while still maintaining the page size?

Also, why does my system come to a screeching halt when I start loading tif files?  Am I doing something wrong?

---

### Post by kaibob on 2009-02-05
You can use the Imagemagick convert utility to convert from TIF to PDF. This utility has numerous options including options that determine page size:

[http://www.imagemagick.org/script/convert.php](http://www.imagemagick.org/script/convert.php)

---

### Post by monstereel on 2009-02-05
Thanks,

I tried Imagemagick and here's what happened.

in terminal I typed

convert filename.tif filename.pdf

which according to Imagemagick's site is the command.  However, I get a message that says that neither file name is valid.  What am I doing wrong?

---

### Post by cariboo on 2009-02-05
If you are in the same directory as the .tif file you have to add a ./ before the file name eg:

```
convert ./filename.tif filename.pdf
```

Jim

---

### Post by kaibob on 2009-02-05
Your command line should work as written, and only two things come to mind. First, you have to be in the directory that contains the source TIF file. I know this is obvious, but it is something that can be overlooked. Second, make sure that you observe capitalization of the source file name. After checking both of these, if convert still doesn't work, please copy and paste the exact error message that you receive from convert.

---

### Post by Don1500 on 2009-02-05
Silly question #39

Did you install  Imagemagick ? or is it just in the folder?

---

### Post by monstereel on 2009-02-05
sorry guys, I guess I've been too frustrated with this to think clearly
but still no dice.  Below is the results from Terminal.  Any thoughts?  I'm attempting this with the file open, should it not be open?  I tried it both ways, open and closed but no difference.




mike@mike-laptop:~$ convert ./Beverland.tif Beverland.pdf
convert: unable to open image `./Beverland.tif': No such file or directory.
convert: missing an image filename `Beverland.pdf'.
mike@mike-laptop:~$

---

### Post by monstereel on 2009-02-05
I did install imagemagick from the terminal

---

### Post by kaibob on 2009-02-05
What directory contains the TIF file? 

What do you mean when you say that you're trying it with the file open?

---

### Post by monstereel on 2009-02-05
I am in the documents-filebrowser which is where the .tif file is saved.  Where should I be?

---

### Post by kaibob on 2009-02-05
> **monstereel said:**
> I am in the documents-filebrowser which is where the .tif file is saved.  Where should I be?

According to what you previously posted, you were not in that directory when you ran the convert command. That's why it couldn't find the TIF file.

---

### Post by monstereel on 2009-02-05
kaibob,

i tried it multiple ways and I'm having problems getting it to work.  i'm really new to ubuntu and i'm learning a lot.  this convert function is critical to my work and i don't know my way around ubuntu well enough yet.  you're right, i do need to learn my way around how linux handles files a little better.  i appreciate your patience.  thanks for your time.

---

### Post by Kellemora on 2009-02-05
Hi Monstereel

I think I see your problem!

```
mike@mike-laptop:~$
```

This is your HOME/User Directory

You need to type
```
cd NameOfNextFolder
```
to move up one folder, then once in that folder, do it again if necessary.  As an example:
```
cd Desktop
```
```
cd Bluprints
```

Then you can run the commmands needed.

TTUL
Gary

---

### Post by kaibob on 2009-02-05
> **monstereel said:**
> kaibob,

i tried it multiple ways and I'm having problems getting it to work.  i'm really new to ubuntu and i'm learning a lot.  this convert function is critical to my work and i don't know my way around ubuntu well enough yet.  you're right, i do need to learn my way around how linux handles files a little better.  i appreciate your patience.  thanks for your time.

The following page has a good explanation of navigating the linux file system by way of the command line. It's actually quite easy once you understand the basics--it's just a bit confusing at first because it differs from Windows. 

[http://www.tuxfiles.org/linuxhelp/linuxfiles.html](http://www.tuxfiles.org/linuxhelp/linuxfiles.html)

And, be sure to remember that capitalization matters with linux. The file picture.jpg and Picture.jpg are two different files.

---

