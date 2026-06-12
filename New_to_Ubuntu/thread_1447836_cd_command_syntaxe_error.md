---
title: "cd command syntaxe error"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by eliasrio on 2010-04-05
i'm running 9.04 32b and GNU bash, version 3.2.48(1)-release (i486-pc-linux-gnu). i tryed the command : usuario@usuario-desktop:~$** cd: /home**
bash: cd:: **command not found**, then i tryed : usuario@usuario-desktop:~$ **cd [-L] [/home/usuario/dowmloads/w32codecs/essentials2007-1007]**
bash: cd: [-L]: No such file or directory, but i have this folder. what I'm doing wrong??
tryed to install this package of video codecs from: 
[http://www.baixaki.com.br/linux/download/w32codecs.htm](http://www.baixaki.com.br/linux/download/w32codecs.htm)

---

### Post by oldos2er on 2010-04-05
> **eliasrio said:**
> usuario@usuario-desktop:~$ **cd [-L] [/home/usuario/dowmloads/w32codecs/essentials2007-1007]**
bash: cd: [-L]: No such file or directory, but i have this folder. what I'm doing wrong??
tryed to install this package of video codecs from: 
[http://www.baixaki.com.br/linux/download/w32codecs.htm](http://www.baixaki.com.br/linux/download/w32codecs.htm)

 Should be ```
cd /home/usuario/downloads/w32codecs/essentials2007-1007
```

 But w32codecs is in the Medibuntu repository; [http://medibuntu.org/](http://medibuntu.org/)

---

### Post by mikewhatever on 2010-04-05
How about *cd /home/usuario/dowmloads/w32codecs/essentials2007-1007*?

---

### Post by CharlesA on 2010-04-05
Meh, I'd just use:

cd ~/dow**n**loads/w32codecs/essentials2007-1007
or
just cd dow**n**loads/w32codecs/essentials2007-1007
since the OP is already in his home directory.

---

### Post by Puz on 2010-04-05
If in fact you typed "cd: /home" the colon is what caused the error in your first attempt.  And on your second attempt you mistyped "downloads". You need to double check every thing for errors before you execute the commands.

---

### Post by lisati on 2010-04-05
> **Puz said:**
> If in fact you typed "cd: /home" the colon is what caused the error in your first attempt.  And on your second attempt you mistyped "downloads". You need to double check every thing for errors before you execute the commands.

+1
I'm not sure where the square brackets [] came from. They're sometimes used in documentation to indicate that something is optional on a command line, and that you need to make some kind of choice about what to type in.

---

### Post by CharlesA on 2010-04-06
Tab can autocomplete most things, just type part of the directory name and hit tab and it will autofill. :D

---

