---
title: "Game Install"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by Nathan Cunningham on 2009-07-07
I want to install the game 'micropolis' similar to Sim City. I downloaded the folder for install here. I am confused as to how to now install that onto my computer. What commands do I need to run in order to run the game?  Thanks!

---

### Post by jonobr on 2009-07-07
Hello


What kind of game? Is it Linux or windows?
If windows are your running it in wine?

Do you know where the binary executable for that game is?

Im guessing its micropolis

if you dont know where it is try in a terminal window

```
find ~/ . name micro* 
```

If (as an example) it finds mircopolis in


/home/<user>/Desktop/Games/

and the executable is micropolis
then simply run it by typing 

```
/home/<user>/Desktop/Games/micropolis
```

or you could change to that directory

```
cd /home/<user>/Desktop/Games/
```

and then execute it by typing

```
./micropolis
```
This assumes again the binary executable is micropolis

---

### Post by Nathan Cunningham on 2009-07-07
Its definitely a Linux game. When I run the find command, it says "No such file or directory" even though the folder is on my desktop, I can see it in plain sight. There is a Python Script with a list of commands. Do I need to just run all those commands individually? Or is there a way to run all the commands at once?

---

### Post by jonobr on 2009-07-07
if you open a terminal and type

cd ~/Desktop/<folder>

where folder is the name of the folder

and in there type ls -l and post the results here, Ill have a look for you,
in the meantime, Ill try and find the game

Cheers

---

### Post by jonobr on 2009-07-07
actually a stupid question for you

When you said you can see the folder.

Is it a folder or is it a file that says something like

micropolisblah.tgz or 
micropolisblah.tar.gz?

---

### Post by Nathan Cunningham on 2009-07-07
If you meant the letter "l" this is what I got:
total 3640
-rw-r--r-- 1 nathan nathan 3723053 2009-07-07 12:45 micropolis.xo

If you meant |, as in the symbol usually above the Enter key, this is what I got: 
bash: syntax error near unexpected token `|'

If you meant neither the letter nor the symbol, then I don't know what I'm supposed to type in. 

[http://www.donhopkins.com/home/micropolis/](http://www.donhopkins.com/home/micropolis/)

Its a file: Micropolis.xo

---

### Post by jonobr on 2009-07-07
the xo is for a specifc type of laptop. AKA the $100 laptop, so unless you have that, this is not for you.

Im thinking you need micropolis-activity.tgz

when you download it, open a terminal and type

```
cd ~/Desktop
```

then

```
gunzip micropolis-activity.tgz
```

then 

```
tar -xvf micropolis-activity
```

then

```
cd micropolis-activity
```

then 

```
./micropolis
```

I tried it but it doesnt like my xserver stuff

---

### Post by Nathan Cunningham on 2009-07-07
I got all the way to the last step. When I tried to run "./micropolis" it just said No such file or directory. So, I don't know where to go from here. It worked for the most part, then failed at the end.

---

### Post by jonobr on 2009-07-07
ok, so after the second last step type ls -l
 thats l as in lowercase L for Lima

---

### Post by Nathan Cunningham on 2009-07-07
This is what I typed in:
nathan@dell-desktop:~/Desktop/micropolis-activity$ ./Micropolis

And this was the result:
Starting Micropolis in /home/nathan/Desktop/micropolis-activity ... 
Welcome to X11 Multi Player Micropolis version 4.0 by Will Wright, Don Hopkins.
Copyright (C) 2002 by Electronic Arts, Maxis. All rights reserved.
sh: Syntax error: Bad fd number
sh: Syntax error: Bad fd number
Adding a player on :0.0 ...
Darn, X display ":0" claims to support the shared memory extension,
but is too lame to support shared memory pixmaps, so Micropolis will run slower.
Please complain to your X server vendor, The X.Org Foundation
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  72 (X_PutImage)
  Serial number of failed request:  1931
  Current serial number in output stream:  1953

Does that just mean my server doesn't support this game?

---

### Post by jonobr on 2009-07-07
I got the same error when I ran it,
I hoped you would have better luck but obviously not,

Ill check around for the error and see what I can find

---

### Post by jabro on 2009-09-15
So did you guys ever figure this out?  I was just doing the same, and came across the same error...

---

### Post by Nathan Cunningham on 2009-09-15
Not really. I never installed it. I moved on with my life. :cool:

---

### Post by jabro on 2009-09-16
haha... well in case you want to start that up again... I found this thread: [http://ubuntuforums.org/showthread.php?t=665844&page=6](http://ubuntuforums.org/showthread.php?t=665844&page=6) someone else has a tarball you can download, and compile.  works for me... been playing all afternoon.  

oh the memories from the 1990's... lol

---

