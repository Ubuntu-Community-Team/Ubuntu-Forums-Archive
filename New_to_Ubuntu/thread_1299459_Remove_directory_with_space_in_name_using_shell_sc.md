---
title: "Remove directory with space in name using shell script"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by RealG187 on 2009-10-23
I have my shell script to remove an empty directory on the desktop. When I try to remove a folder named *Beef 2* it doesn't work. Here is the output (I copied my shell script to /bin so I an execute it by simply typing "rd" an not "./rd"

```
mpg@MIKED6:~$ rd
Name of directory to remove -->Beef\ 2
rmdir: failed to remove `Beef': No such file or directory
rmdir: failed to remove `2': No such file or directory
mpg@MIKED6:~$ rd
Name of directory to remove -->"Beef 2"
rmdir: failed to remove `"Beef': No such file or directory
rmdir: failed to remove `2"': No such file or directory
mpg@MIKED6:~$ cd Desktop
mpg@MIKED6:~/Desktop$ file Beef\ 2
Beef 2: directory
mpg@MIKED6:~/Desktop$
```

You can see the code of the shell script source [here]("http://operation420.net/forum/viewtopic.php?f=10&t=917").

---

### Post by cilynx on 2009-10-23
Throw "" around the variable name in the rm command.  rm is treating it as two separate files.  If you use "", the variable will be processed.  If you use '', you'll be passing the variable name literally.

---

### Post by Ocxic on 2009-10-23
try changing 
rmdir $remove && echo -e "$remove removed"
to
rmdir "$remove" && echo -e "$remove removed"

---

### Post by RealG187 on 2009-10-24
If I go $remove and when promted enter "whatever space" woouldn't that be the same as "$remove"?

---

### Post by Bachstelze on 2009-10-24
> **RealG187 said:**
> If I go $remove and when promted enter "whatever space" woouldn't that be the same as "$remove"?

Nope. Try it for youself.

---

### Post by lavinog on 2009-10-24
why not make an alias:
```

alias rd='rm -r'

```

---

