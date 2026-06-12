---
title: "help with ./configure"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by utkarshjadhav on 2010-08-05
root@utkarsh-laptop:/home/utkarsh/Downloads/AdobeReader# ./configure
bash: ./configure: No such file or directory

---

### Post by cj.surrusco on 2010-08-05
Have you checked the directory for a configure file? You didn't really give too much info about your problem.

---

### Post by utkarshjadhav on 2010-08-06
I have installed Lucid Lynx.
I want to install Adobe Reader to read pdf files.
right now its opening with document viewer.


I tried with some ways -

sudo apt-get install AcroRead
sudo apt-get install acrobat etc etc 
but all in vain.
as the error was----couldnt find package


So I downloaded tar.gz
extracted it.
and now i am trying to install it 
hence using  ./configure
and error is as mentioned above.

---

### Post by lisati on 2010-08-06
Ubuntu comes with "Evince", which will read PDF files.

It could be that the tar.gz file you've downloaded doesn't have a "./configure" file or that it's in a subdirectory located within your Downloads folder - you might have to look for a file with a name like "readme" or a place on the website where you downloaded the file for installation instructions.

---

### Post by cj.surrusco on 2010-08-06
I would take a look at the Readme file that is inside of the Adobe directory. It may have you run an install file instead of the normal "configure and make" procedure.

---

### Post by pipemartinm on 2010-08-06
The packages are there, the built in reader is pretty good though.
```

sudo apt-cache search adobe
...
adobereader-deu - Adobe Reader
adobeair - runtime for rich Internet applications
adobe-flashplugin - Adobe Flash Player plugin version 10
acroread - Adobe Reader

```

---

### Post by spyrule on 2010-08-06
The packages are there. Make sure your typing:

```
sudo apt-get install acroread
```

All lowercase. I noticed in your thread that you had "... AcroRead ...". Linux is very case sensitive. You can also get it through Applications->Ubuntu Software Center, and do a search for Acrobat.

---

### Post by oldos2er on 2010-08-06
acroread is in the partner repository, which is not enabled by default. System, Administration, Software Sources, Other Software tab.

---

### Post by utkarshjadhav on 2010-08-07
did with ---Applications->Ubuntu Software Center
thanks all.
:p;):o

---

