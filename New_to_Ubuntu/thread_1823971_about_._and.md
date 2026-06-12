---
title: "about ./* and /*"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by o15977 on 2011-08-12
what is the difference between ./* and /*
i have seen a lot of syntax with ./*, but never worked for me, what is the 'dot' doing there?

---

### Post by Wim Sturkenboom on 2011-08-12
dot indicates current directory

Assuming * represents a file,
1)
./* is a file in the current dirrectory. The format is often used because the current directory is often not in the path that is used by the shell to find a program
you could also have used /path/to/currentdirectory/* but it's more typing ;)
2)
/* is a file in the systems root directory

---

### Post by Wim Sturkenboom on 2011-08-12
simple test

create a file in your home directory with the following contents
```

#!/bin/bash
echo helloworld

```
I used vi as the editor, feel free to use what you're familiar with. Next make it executable (chmod command below) and run it with ./helloworld.sh.
Next try to run it without the ./
```

fortyfourgalena@desktop-01:~$ vi helloworld.sh
fortyfourgalena@desktop-01:~$ chmod 755 helloworld.sh 
fortyfourgalena@desktop-01:~$ ./helloworld.sh 
helloworld
fortyfourgalena@desktop-01:~$ helloworld.sh 
helloworld.sh: command not found
fortyfourgalena@desktop-01:~$ 

```
You will notice that if you use tab completion, ./hello followed by pressing<tab> will complete the filename while if you start with hello and press <tab> it will not because the shell will look in its path and can not find the file there.

---

### Post by nothingspecial on 2011-08-13
/ is the root directory, the beginning of the file system. Think of linux as one big folder. Everything is in / Most things are in another folder in / or a folder in a folder in / (and so on) but wherever you are (even a cd, dvd or external drive) you are always in /


. means where you are.

if you are in your Documents folder, then . means /home/$USER/Documents

if you are in your Music folder then . means /home/$USER/Music

if you are in the root directory then . means / so in that case ./ and / mean the same thing.

* means anything and everything including nothing so /* means everything in your root folder (which is everything), whereas ./* means everything in the folder you are in.

Again, if you are in the root directory ./* and /* mean the same thing.

---

