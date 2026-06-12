---
title: "What does this command mean?"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by Vignesh S on 2010-01-29
Right, I was getting around downloading the source tree for Android-x86, and while I was doing so, I had to use this command:

echo $PATH

My two questions are:
1. What does the above command mean?
2. What exactly is the PATH?

---

### Post by Atzu on 2010-01-29
that command should print on terminal the path where you are; path is well... the path you are... like /home/username 

"Echo's to the screen what you type after echo. Echo is useful for producing diagnostics in command files, for sending known data into a pipe, and for displaying the contents of environment variables." from: [http://www.computerhope.com/unix/uecho.htm](http://www.computerhope.com/unix/uecho.htm)

---

### Post by baddog144 on 2010-01-29
$PATH is a value which holds all the places that your shell should look in for executable files. /bin, /usr/bin/, etc. 

So 'echo $PATH' simply echoes the value of $PATH back at you

---

### Post by spcwingo on 2010-01-29
It should just display the default location of all of your binaries.  For example if in a terminal you type:

```
lspci
```

it will run "lspci".  lspci is in /usr/bin.  The reason you didn't have to type the full path is because "lspci" is in you path.

---

### Post by Revolutionary101 on 2010-01-29
The echo command displays whatever you type after it. If you put a $ that will make it display whatever result of the command you type after it. As for PATH I don't know, I tried it in my terminal and it just displays a bunch of (what I think) are random paths. I don't know where they lead.

---

### Post by yeats on 2010-01-29
echo prints out a string or the contents of a variable.

$PATH is a bash/sh environment variable that contains the directory path to programs so you can just call them by their names (e.g., firefox) rather than their full directory paths (e.g., /usr/bin/firefox).  Since /usr/bin is in the $PATH, you can just type "firefox" to call up the program.

---

### Post by Vignesh S on 2010-02-05
Thanks everyone :)

---

