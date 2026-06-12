---
title: "What does #!/bin/sh mean?"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by newport_j on 2010-01-22
I was examining some shell files I use when compiling a very large C program. I am sure of the syntax since I use it many times durig the day. I am unsure as to why I have the line:
 
 
#!/bin/sh
 
 
at the top of the file. I have Googled the term, but it is not clear what it does. Each of my shell scripts has it at the top of the file on the first line. I cannot remember what is it there for, can anyone tell me?
 
Newport_j

---

### Post by muteXe on 2010-01-22
Weird, i googled and got some good links.
[http://www.google.co.uk/search?hl=en&source=hp&q=%22%23%21%2Fbin%2Fsh%22&meta=&aq=f&oq=](http://www.google.co.uk/search?hl=en&source=hp&q=%22%23%21%2Fbin%2Fsh%22&meta=&aq=f&oq=)

---

### Post by Barrucadu on 2010-01-22
It means &#8220;execute this file with that program&#8221;, so you can run it with `/path/to/the/script`, rather than as `sh /path/to/the/script` (if the file is executable).

---

### Post by VCoolio on 2010-01-22
It's a nice trick; you can do it with any file, like
to open with conky:
#!/usr/bin/conky -c
to open with emacs in terminal-mode 
#!/usr/bin/emacs -nw
etc.

---

### Post by Diametric on 2010-01-22
I was under the impression that it identified the code as as shell script - meaning the code was intended to execute in the terminal.

---

### Post by Mornedhel on 2010-01-22
> **Diametric said:**
> I was under the impression that it identified the code as as shell script - meaning the code was intended to execute in the terminal.

Adding the shebang line (from "sharp bang", #!) serves two purposes.

It tells the shell that if the file is run as an executable, and it is not a binary, run it with the executable described in the line.

It also tells humans reading the file that it's supposed to be run with that executable, so you are right, in a way: a file that begins with #!/bin/sh is likely to be an sh-compatible shell script.

However, nothing prevents you from writing a #! line and executing it manually (e.g. "sh blah.pl") with something else (well, except you can't run a Perl script with bash).

You see shebang lines a lot when interpreted scripts are involved, e.g. /usr/bin/perl, /usr/bin/python, /usr/bin/ruby, /bin/sh, /bin/bash, etc.

---

### Post by juancarlospaco on 2010-01-22
Shell Script on Na'vi language

---

