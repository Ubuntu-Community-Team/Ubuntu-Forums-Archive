---
title: "sed \ into \\?"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by outleradam on 2010-05-02
I need to know how to turn "\" into "\\" using a POSIX command.  Any command will work.  I just need to figure out how to turn a \ into a \\

I tried 
```
echo "\\ \\\\ \\"| sed s/"\\"/"\\\\"/n 
```
which should return the exact same thing that went in, but it does not act right.   It gives me an error.  sed: -e expression #1, char 8: unterminated `s' command

How can I do this?

---

### Post by outleradam on 2010-05-02
ok.  I found the problem

I was doing a echo -e which only produces 1 "\" per "\\\\"
```
adam@adam-desktop:~/.mythicalLibrarian/mythicalSetup$ echo \\
\
adam@adam-desktop:~/.mythicalLibrarian/mythicalSetup$ echo -e \\
\
adam@adam-desktop:~/.mythicalLibrarian/mythicalSetup$ echo -e \\\\
\
adam@adam-desktop:~/.mythicalLibrarian/mythicalSetup$ echo -e \\\\\\
\\
adam@adam-desktop:~/.mythicalLibrarian/mythicalSetup$ echo -e \\\\\\\\
\\
adam@adam-desktop:~/.mythicalLibrarian/mythicalSetup$ echo -e \\\\\\\\\\
\\\
adam@adam-desktop:~/.mythicalLibrarian/mythicalSetup$ echo -e \\\\\\\\\\\\
\\\
adam@adam-desktop:~/.mythicalLibrarian/mythicalSetup$ echo -e \\\\\\\\\\\\\\
\\\\

```The final solution to the sed problem is 

```
echo "\\ \\\\ \\"  | sed s/'\\'/'\\\\'/g
``` the ' operator is required instead of the " operator.    This is solved..  However, do you think the non-linear act of echo -e should be reported as a bug?

---

