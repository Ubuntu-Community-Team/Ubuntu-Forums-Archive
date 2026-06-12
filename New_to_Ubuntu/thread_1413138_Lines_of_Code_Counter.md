---
title: "Lines of Code Counter"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-02-22
Is there a program, command, or group of commands that will count the source lines of code of all the .cpp files in one folder (not including comments and whitespace)? I wrote a program a while back that would do that, but it's for Windows.

---

### Post by blazemore on 2010-02-22
[http://freshmeat.net/projects/loc/](http://freshmeat.net/projects/loc/)
is that what you're looking for?

---

### Post by d3v1150m471c on 2010-02-22
```

wc -l /path/to/file

```

Or perhaps

```

wc -l /path/to/folder/*

```

---

### Post by blazemore on 2010-02-22
> **d3v1150m471c said:**
> ```

wc -l /path/to/file

```
That won't ignore whitespace and comments, and it won't count multiple files.

---

### Post by d3v1150m471c on 2010-02-22
> **blazemore said:**
> That won't ignore whitespace and comments, and it won't count multiple files.

The second command I gave will

```

d3v11@d3v11m4ch1n3:~$ wc -l ~/Projects/yahquick_1_2/*
     36 /home/d3v11/Projects/yahquick_1_2/Read Me
wc: /home/d3v11/Projects/yahquick_1_2/system32: Is a directory
      0 /home/d3v11/Projects/yahquick_1_2/system32
   3296 /home/d3v11/Projects/yahquick_1_2/winetricks
   2876 /home/d3v11/Projects/yahquick_1_2/yahelitefull.exe
    169 /home/d3v11/Projects/yahquick_1_2/yahelite_on_linux.png
     25 /home/d3v11/Projects/yahquick_1_2/yahinstall.x
     36 /home/d3v11/Projects/yahquick_1_2/ycabby.exe
   6438 total

```

---

### Post by blazemore on 2010-02-22
> **d3v1150m471c said:**
> The second command I gave will


It won't ignore comments.
Don't forget you can have block comments, and also comments on the same line as an expression, both of which prevent simple grep commands.

---

### Post by gmargo on 2010-02-22
I did "**apt-cache search code count**" and found two in the repositories:

```

cccc - C and C++ Code Counter, a software metrics tool
sloccount - programs for counting physical source lines of code (SLOC)

```

---

### Post by EnigmaticCoder on 2010-02-24
Thanks everybody.

---

