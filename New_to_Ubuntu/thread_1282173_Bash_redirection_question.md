---
title: "Bash redirection question"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by SteelCore on 2009-10-04
I'm trying to read a section about redirection in an online book ([http://tldp.org/LDP/intro-linux/html/sect_05_02.html](http://tldp.org/LDP/intro-linux/html/sect_05_02.html)) but was completely unable to comprehend the given example. Can someone plz help by explaining what do these 2 statements mean.

ls > dirlist 2>&1 
ls 2>&1 > dirlist 

Thanks in advance.

---

### Post by CatKiller on 2009-10-04
It redirects both the standard output and the standard error streams of the command *ls* to a text file called *dirlist*.

[This]("http://en.wikipedia.org/wiki/Standard_streams") might give you an overview.

---

### Post by SteelCore on 2009-10-04
The text says that the 1st statment directs both stdout and stderr to dirlist but the 2nd one only directs stdout.
Actually the exact meaning of these statements is still unclear to me but thanks for your answer anyway.

---

### Post by CatKiller on 2009-10-04
I think the text is mistaken, although it's not something I know a huge amount about.

Simply ```
ls > dirlist
``` would direct just  the stdout of *ls *to *dirlist*.

---

### Post by unutbu on 2009-10-04
Usually programs have file descriptors 1 and 2 hooked up to stdout and stderr like this:
```

1 ---> stdout
2 ---> stderr
```

When you say "ls > dirlist"  you are redirecting file descriptor 1 to the file dirlist:
```

1 ---> dirlist
2 ---> stderr
```

When you say "ls > dirlist 2>&1" you are redirecting file descriptor 2 to the address of file descriptor 1 (i.e. wherever 1 happens to be pointing):
```

1 ---> dirlist
2 ---> dirlist
```

When you say "ls 2>&1" you are redirecting file descriptor 2 to wherever file descriptor 1 happens to be pointing: 
```

1 ---> stdout
2 ---> stdout
```

When you say "ls 2>&1 > dirlist" you are redirecting file descriptor 1 to dirlist: 
```

1 ---> dirlist
2 ---> stdout
```

Note that this does not change where file descriptor 2 is pointing to.

So to recap:

"ls > dirlist 2>&1" results in 

```
1 ---> dirlist
2 ---> dirlist

```
But

"ls 2>&1 > dirlist" results in
```

1 ---> dirlist
2 ---> stdout
```


Here is a toy script with which you can test the above claims. Save this as test.sh
[PHP]
#!/bin/bash
echo "This is stdout"
echo "This is stderr" >&2[/PHP]

Then run
```

test.sh > dirlist 2>&1
test.sh 2>&1 > dirlist 

```

---

### Post by SteelCore on 2009-10-05
> **CatKiller said:**
> I think the text is mistaken

It isn't.  I found the exact wording in the bash reference on gnu.org with a bit more clear explanation
[http://www.gnu.org/software/bash/manual/bashref.html#Redirections](http://www.gnu.org/software/bash/manual/bashref.html#Redirections)

Overall the picture is clearer now.

---

### Post by lrbh on 2011-08-31
Thanks for the clear explanation -- the effect (1 --> file, 2 --> stdout) is just what I've been trying to achieve.

---

### Post by jzjavez on 2011-09-03
i got a software like backtrack linux and could any one tell me how to install that on the ubuntu

---

