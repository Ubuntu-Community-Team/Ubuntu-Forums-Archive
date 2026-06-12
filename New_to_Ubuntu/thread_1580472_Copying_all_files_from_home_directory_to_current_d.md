---
title: "Copying all files from home directory to current directory"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by UnknownFear on 2010-09-23
I am trying to copy all the files from my home directory to the current directory I am in starting with the letter 'a'. How would I do this using the terminal?

---

### Post by sikander3786 on 2010-09-23
For current directory I don't know. Otherwise the command is,

```

cp -r  /home/user-name /what-ever-destination

```

---

### Post by da burger on 2010-09-23
> **sikander3786 said:**
> For current directory I don't know. Otherwise the command is,

```

cp -r  /home/user-name /what-ever-destination

```

Of course you would then just replace "/what-ever-destination" with . to make it the current dir. However I'm not sure that's what the OP meant. Do you want to copy the entire directory structure, or just the files?

---

### Post by sikander3786 on 2010-09-23
> **da burger said:**
> Of course you would then just replace "/what-ever-destination" with . to make it the current dir. However I'm not sure that's what the OP meant. Do you want to copy the entire directory structure, or just the files?
Yeah that should be a simple "dot". I need to do some more hard work on that command line thing. :-) I like to use the gui's (whereever available) unless I'm forced to work in the terminal.

---

### Post by UnknownFear on 2010-09-23
> **da burger said:**
> Of course you would then just replace "/what-ever-destination" with . to make it the current dir. However I'm not sure that's what the OP meant. Do you want to copy the entire directory structure, or just the files?

I want to copy all the files that begin with a from my home directory to my current directory, but I'm not in my home directory. How would I do it without being in my home directory?

---

### Post by Lateralis on 2010-09-23
```

cp ~/a* .

```

~/ - shorthand for /home/<your username>
* - wild card.  
. - shorthand for "current directory" (same as .. is short hand for "parent directory")

Of course, that will only copy all files beginning with lowercase a to the current directory.  For uppercase use A*.

If you want to copy any directories which begin with a, put the -r (recursive) switch in.

---

