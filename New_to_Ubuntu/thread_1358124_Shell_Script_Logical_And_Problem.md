---
title: "Shell Script Logical And Problem"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by nmaster on 2009-12-18
I'm fairly new to shell scripting and I think that I'm misunderstanding logical and.  I think the comment in my script should explain what I'm trying to do.

Here's my script:
```

#! /bin/sh                                                                      

# prints file to pdf and moves it to the current directory                      
# 'lpPDF file' will print file to a pdf and move it to the current directory    

##########################################################################      
# set-up:       sudo apt-get install cups-pdf                                   
#               mkdir ~/.PDF                                                    
#               go into /etc/cups/cups-pdf.conf and change OUT to ~/.PDF        
##########################################################################      

name=`basename "$1"`
new_file="${name}.pdf";
lpr -P PDF $1 &&  mv  ~/.PDF/$new_file .

```The file prints to ~/.PDF properly,
```

neal@neal-laptop:/home/neal/.PDF 
$ dir
testFile.pdf

``` but this is the error I get:
```

$ lpPDF testFile
mv: cannot stat `/home/neal/.PDF/testFile.pdf': No such file or directory

```Clearly, the mv is not waiting for the lpr to finish.  I need the file to print and only then do I want to move it to the current directory.  What am I doing wrong?

---

### Post by nmaster on 2009-12-18
more info:  This used to work.  See my final post here: [http://ubuntuforums.org/showthread.php?t=1353612](http://ubuntuforums.org/showthread.php?t=1353612)

---

### Post by doas777 on 2009-12-18
you could sleep for a few secs, though this is a less than optimal answer
```

sleep 10;echo hello

``` will pause for 10 secs and then print the message.

it looks like your && usage is correct. have you tried quoting your commands?

---

### Post by nmaster on 2009-12-18
> **doas777 said:**
> you could sleep for a few secs, though this is a less than optimal answer
```

sleep 10;echo hello

``` will pause for 10 secs and then print the message.

it looks like your && usage is correct. have you tried quoting your commands?

quoting doesn't change anything.  also, sleep wouldn't be a good idea since longer documents would take longer to print.

---

### Post by falconindy on 2009-12-18
This is probably way over the top, but....

```
#!/bin/bash
name=`basename "$1"`
new_file="${name}.pdf";
lpr -P PDF $1

sleep 2
while [[ `lsof "$HOME/.PDF/$new_file"` ]]; do
  sleep 1
done

mv "$HOME/.PDF/$new_file" ./
```
Basically, sleep until lsof doesn't find anyone poking at your file.

Edit: note that Bash is necessary for the double square brackets to work as intended.

---

### Post by nmaster on 2009-12-18
> **falconindy said:**
> This is probably way over the top, but....

```
#!/bin/bash
name=`basename "$1"`
new_file="${name}.pdf";
lpr -P PDF $1

sleep 2
while [[ `lsof "$HOME/.PDF/$new_file"` ]]; do
  sleep 1
done

mv "$HOME/.PDF/$new_file" ./
```Basically, sleep until lsof doesn't find anyone poking at your file.

Edit: note that Bash is necessary for the double square brackets to work as intended.


i haven't tried it but that sounds okay... except i still don't understand by using && didn't work.  can anyone explain?

---

### Post by falconindy on 2009-12-18
> **neal.m.master said:**
> i haven't tried it but that sounds okay... except i still don't understand by using && didn't work.  can anyone explain?
lpr is executed as a background job, and immediately returns control to the shell, rather than waiting for the job to truly complete. Because of this, the mv command is executed too soon and fails on a file that doesn't yet exist.

Not sure what's changed, but maybe an explanation of what's happening may spark something.

---

### Post by doas777 on 2009-12-18
> **neal.m.master said:**
> quoting doesn't change anything.  also, sleep wouldn't be a good idea since longer documents would take longer to print.

your right, sleep would be bad/unnecessary if it was synchronously threaded, but then if it were, your && would work fine (note falconindy's post about lpr running in the background asynchronously) .

---

### Post by nmaster on 2009-12-18
> **falconindy said:**
> This is probably way over the top, but....

```
#!/bin/bash
name=`basename "$1"`
new_file="${name}.pdf";
lpr -P PDF $1

sleep 2
while [[ `lsof "$HOME/.PDF/$new_file"` ]]; do
  sleep 1
done

mv "$HOME/.PDF/$new_file" ./
```Basically, sleep until lsof doesn't find anyone poking at your file.

Edit: note that Bash is necessary for the double square brackets to work as intended.

This seems to solve the problem with mv, but now I noticed a problem with basename.  It doesn't do the right thing for a file with a jpg extension:
```

$ lpPDF Documents/lucia.jpg 
lsof: status error on /home/neal/.PDF/lucia.jpg.pdf: No such file or directory
lsof 4.78
 latest revision: ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/
 latest FAQ: ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ
 latest man page: ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man
 usage: [-?abhlnNoOPRstUvVX] [+|-c c] [+|-d s] [+D D] [+|-f]
 [-F [f]] [-g [s]] [-i [i]] [+|-L [l]] [+m [m]] [+|-M] [-o [o]]
 [-p s] [+|-r [t]] [-S [t]] [-T [t]] [-u s] [+|-w] [-x [fl]] [--] [names]
Use the ``-h'' option to get more help information.
mv: cannot stat `/home/neal/.PDF/lucia.jpg.pdf': No such file or directory
neal@neal-laptop:/home/neal 
$ lpPDF testFile
neal@neal-laptop:/home/neal 
$ 

```

Otherwise, it works.  Whats up with basename?

---

### Post by nmaster on 2009-12-18
I decided to mark this thread as solved.  I've asked my question about basename in a new thread so its easier for other people to search for.

 [http://ubuntuforums.org/showthread.php?t=1358696](http://ubuntuforums.org/showthread.php?t=1358696)

Thanks for the help.

---

### Post by NJ0E on 2009-12-18
Not sure, but could you do the move first and then print?  Seems from my reading of the posts that the move command isn't waiting for the print command.  Just my 2 Cents (not a really good coder).

---

### Post by nmaster on 2009-12-18
> **NJ0E said:**
> Not sure, but could you do the move first and then print?  Seems from my reading of the posts that the move command isn't waiting for the print command.  Just my 2 Cents (not a really good coder).

No the move cannot be executed first. The file doesn't even exist until it's printed.  Thats how cups-pdf works.

---

