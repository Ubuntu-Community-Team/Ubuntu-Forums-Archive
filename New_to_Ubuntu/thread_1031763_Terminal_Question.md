---
title: "Terminal Question"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by The-IRS on 2009-01-05
hi all.
I have a question. I had to change the directory on my terminal to desktop to install a program. but I have stupidly forgot how to change it back to the default! can anyone give me the code to do this? without it I cant do anything!

thanks for the help
-IRS

---

### Post by donkyhotay on 2009-01-05
If you just type 
```
cd
```
it will automatically take you back to your home folder if thats where you want to go.

---

### Post by adult swim on 2009-01-05
all you need to do is enter in ```
cd
``` and it will always take you back to your home directory

---

### Post by jakupl on 2009-01-05
or just restart the terminal.

---

### Post by donkyhotay on 2009-01-05
> **jakupl said:**
> or just restart the terminal.

Yes that works but it's better to teach proper terminal practices to help people learn how to navigate with the CLI.

---

### Post by adult swim on 2009-01-05
> **jakupl said:**
> or just restart the terminal.

that would be like restarting ubuntu to close a program :)

---

### Post by djbushido on 2009-01-05
Quick "cd" help:

Type ```
cd ~
``` to move to your home directory.
Type ```
cd ~/path
``` to move anywhere inside your home directory
Type ```
cd /
``` to move to the root directory
Type ```
cd /path
``` to move anywhere inside the root directory
Typing ```
cd path
``` will move to the folder relative to your current location. The terminal prompt line will tell you where your current location is.

Well, that should be it. Good luck!

---

### Post by The-IRS on 2009-01-05
it says:
```
stewart@stewart-desktop:~$
```


is that right?

---

### Post by adult swim on 2009-01-05
that looks right
any time you dont know what directory you are in you can run ```
pwd
``` and it will tell you.
it looks like stewart-desktop is the name of your computer.  if you were actually in the Desktop folder it would look like ```
stewart@stewart-desktop:~/Desktop$
```

---

### Post by donkyhotay on 2009-01-05
Yes, the ~ (tilde) represents your home folder. It will always display that symbol to represent it. Because it shows ~ and no other then it means you are in your home folder. Theoretically if it said
```
~/myfolder
```
then it would mean you were within a folder named 'myfolder' that is located within your home folder.

---

### Post by The-IRS on 2009-01-05
thank you

---

### Post by bodhi.zazen on 2009-01-05
For a nice intro to the terminal (bash) see :

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

---

