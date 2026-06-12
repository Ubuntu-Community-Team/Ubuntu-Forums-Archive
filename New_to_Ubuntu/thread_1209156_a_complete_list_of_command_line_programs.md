---
title: "a complete list of command line programs"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by Chapter&amp;Moon on 2009-07-10
Is there a command that gives me a complete list of tools and applications and a short description of each?

---

### Post by credobyte on 2009-07-10
Sorry, your title differs from what you are asking ! Take a look at this page : [http://www.ss64.com/bash/](http://www.ss64.com/bash/) ;)

---

### Post by QIII on 2009-07-10
Here's a good list:

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

If you want to learn specifics, say about grep, just type

man grep

in the CLI.

---

### Post by Chapter&amp;Moon on 2009-07-10
thanks. part of what I wanted. But, there is apparently no command that gives me this list, and I would assume there are deeper, housekeeping commands not on this list. maybe they are outside of bash or debian.

---

### Post by credobyte on 2009-07-10
> **Chapter&Moon said:**
> thanks. part of what I wanted. But, there is apparently no command that gives me this list, and I would assume there are deeper, housekeeping commands not on this list. maybe they are outside of bash or debian.

Any examples ( I'm not really sure what you mean by "outside of bash" .. there's no way to get a list of currently installed CLI applications ) ?

---

### Post by Mornedhel on 2009-07-10
```
apropos "" -s <number>
```

(yes, with the empty quotes)

This should give you a list of all man pages available on your system, with a short description. The value of number can be (the following taken from the man manpage) :

```

       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions eg /etc/passwd
       6   Games
       7   Miscellaneous (including macro  packages  and  conven&#8208;
           tions), e.g. man(7), groff(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]
```

It is advisable to maximize the terminal window before using this command since it typically outputs a lot of lines. Using | less at the end of the command (apropos "" -s 1 | less) would also be a good idea.

---

