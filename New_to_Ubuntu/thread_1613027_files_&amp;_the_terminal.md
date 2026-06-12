---
title: "files &amp; the terminal"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by Hi-Ho-Silver! on 2010-11-03
How do I open a file with the terminal after I set the file as "allow executing file as program." 

Thanks! :D

---

### Post by papibe on 2010-11-03
If it is a text file and you want to just see the file:
```
$ cat file
```
or page by page
```
$ more file
```
To edit it:
```
$ nano file
```
or, only if you know how to use the vi editor:
```
$ vi file
```
You can also launch a graphic editor:
```
$ gedit file
```
If the file is a binary and you want to execute it:
```
$ ./file
```

I hope it helps.

EDIT: added the binary case.

---

### Post by Hi-Ho-Silver! on 2010-11-04
Thank you for the reply. Basically, the instructions I received were to:
-right click the file and hit properties
-tag allow it to run as program 
-open it with the terminal

I have gotten as far as tagging it to run as program, but still no luck in opening it with the terminal?

---

### Post by alang184 on 2010-11-04
Can you give a bit more details about what you mean by "opening with the terminal"?

Are you talking about a file containing text which you want to launch from the GUI and the file contents displayed in the terminal?

---

### Post by HermanAB on 2010-11-04
Howdy,

To run it:
$ ./programname

To edit it:
$ gedit programname

Or if you are a masochist:
$ vi programname

---

### Post by Hi-Ho-Silver! on 2010-11-04
> **alang184 said:**
> Can you give a bit more details about what you mean by "opening with the terminal"?

Are you talking about a file containing text which you want to launch from the GUI and the file contents displayed in the terminal?

It is a program that is java based and runs on windows. It won't open on linux, but the kid who made the program wrote a guide on how to open it on linux. After I was told to make the file "allow executing file as program" to open it with the terminal. I have the slightest clue what it means to open it with the terminal. I right clicked and then clicked open with...I was given a whole list of applications I could open the file with, but could not find "terminal" anywhere.

---

### Post by Hi-Ho-Silver! on 2010-11-04
> **HermanAB said:**
> Howdy,

To run it:
$ ./programname

To edit it:
$ gedit programname

Or if you are a masochist:
$ vi programname


I did $ ./run.sh (program name is 'run.sh') and it says in the terminal "command not found." am I doing something wrong?

---

### Post by papibe on 2010-11-04
> **Hi-Ho-Silver! said:**
> Thank you for the reply. Basically, the instructions I received were to:
-right click the file and hit properties
-tag allow it to run as program 
-open it with the terminal

I have gotten as far as tagging it to run as program, but still no luck in opening it with the terminal?
It looks like you need to run or execute the file/program:
```
$ ./file
```
BTW, It could be always a good idea to read this[ ATTENTION ALL USERS: Malicious Commands]("http://ubuntuforums.org/announcement.php?f=326") ... just in case.

---

### Post by Hi-Ho-Silver! on 2010-11-04
> **papibe said:**
> It looks like you need to run or execute the file/program:
```
$ ./file
```BTW, It could be always a good idea to read this[ ATTENTION ALL USERS: Malicious Commands]("http://ubuntuforums.org/announcement.php?f=326") ... just in case.

Thank you, I will look over the manual. However, I did try the command $ ./run.sh and still no luck. It says "command not found"/"no such file or directory."

---

### Post by papibe on 2010-11-04
Probably it's in another directory. I imagine you downloaded, or unpacked it on a subdirectory. Let's say that dir is myDir:
```
$ cd myDir
$./run.sh
```
you can always list the files on the actual directory by doing:
```
$ ls
```
you can go back to the previous directory by doing:
> $ cd ..

Regards.

---

### Post by zer010 on 2010-11-04
Are you in the same directory as the file you are trying to run?  
```
cd /path/to/file
```to get to the directory where this file sits.

"BTW, It could be always a good idea to read this[ ATTENTION ALL USERS: Malicious Commands]("http://ubuntuforums.org/announcement.php?f=326") ... just in case."  *thumbs up*

---

### Post by Hi-Ho-Silver! on 2010-11-04
Hmm.. you cleared things up a bit, thank you. It seems its not the commands or the way I messed around with the file that is the problem, I think it is the instructions I received were a bit too vague. Thank you for your help, I now understand linux that much more, hehe :D

---

