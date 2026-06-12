---
title: "csh noob question"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by olifu02 on 2010-11-12
Hi i just moved to Ubuntu from being a mac user for years.  Im trying to get csh in my termianl and i did install csh using 

sudo apt-get install csh 
 
and it installed fine but when i type csh into the terminal i just get the % sign and nothing else.  Nothin will run that i put into my .cshrc file.  Any help is appreciated.  Thanks

---

### Post by gmargo on 2010-11-12
What is in your .cshrc file?  It seems to work for me. (BTW, you might check out **tcsh** too.)

```

$ cat .cshrc
alias   l       'ls -l'
$ csh
% alias
l       ls -l
% 

```

---

### Post by olifu02 on 2010-11-12
Well now i can get csh to work but in my Users settings i have my shell opening settings to be /bin/csh but no matter what....bash comes up.  I would like csh to come up upon terminal opening.

---

### Post by ayenack on 2010-11-12
I don't know much about this but isn't tcsh a better choice than csh. It has all the functions of csh and also has a command line editor.

It's in the repo's.

**sudo apt-get install tcsh**

The home page.

[http://www.tcsh.org/Welcome](http://www.tcsh.org/Welcome)

---

### Post by gmargo on 2010-11-13
> **olifu02 said:**
> Well now i can get csh to work but in my Users settings i have my shell opening settings to be /bin/csh but no matter what....bash comes up.  I would like csh to come up upon terminal opening.

Use the **chsh** command to set your login shell.  How did you set it?

---

### Post by uRock on 2010-11-13
The % sign is correct for csh.```
rabbit@rabbit-desktop:~$ csh
% tcsh
rabbit-desktop:~> ksh
$ bash
rabbit@rabbit-desktop:~$ 

```

---

