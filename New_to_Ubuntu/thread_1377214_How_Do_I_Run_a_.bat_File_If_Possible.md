---
title: "How Do I Run a .bat File If Possible?"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by showithers on 2010-01-10
Hello.  I need to know if it is possible to run a Windows .bat file in Ubuntu, and if so, how.

In case you need to know, the following is the content in the file:

@echo off

echo

cls

EgyDown.ex_ x -d1 -o+ -y+ -vm+ GTA3.uha

del GTA3.uha

cls

SETUP.BAT

cls

echo ******************************************

echo *                                        *

echo *           [www.egydown.com](www.egydown.com)              *

echo *                                        *

echo *                                        *

echo ******************************************

pause

del SETUP.BAT





Thanks ahead of time.

---

### Post by Temposs on 2010-01-10
you would be able to do that with wine or with dosbox possibly.

---

### Post by lawenlerk on 2010-01-10
The syntax of scripts in linux are different.

del is rm
cls is clear
but echo is still echo

u have to create a file with the extension .sh put this as the first line
```

#!/bin/sh
```

and then just write the rest like writing a .bat file except with the new syntax

after that, save and run

```
chmod +x (filename).sh
```

to run the script, just type in

```
./(filename).sh
```

---

### Post by theozzlives on 2010-01-10
Batch files are DOS scripts, they don't run on Linux. I know, I used to be a pretty darn good batch programmer. The most popular it seems is a BASH script (*.sh). One liners can normally be done in an alias. You just gotta forget about the Microsoft way of doing things.

---

### Post by goiggles on 2010-01-10
assuming you have wine installed if not```
sudo apt-get install wine
```

in the terminal run```
wine cmd
```

then in the wine command prompt run the .bat file it should work then

---

### Post by s3a on 2010-01-11
In terminal:
1) cd to directory
2) wineconsole cmd
3) start filename.bat

---

### Post by RiMTrO on 2012-03-06
worked for me, using wine cmd thaks.

---

### Post by overdrank on 2012-03-06
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

