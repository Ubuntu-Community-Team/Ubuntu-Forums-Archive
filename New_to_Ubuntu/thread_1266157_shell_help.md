---
title: "shell help"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by kpholmes on 2009-09-14
what is the line between filename, and tar? and how do i produce it on a keyboard? im really confused about that whole line thing.

 gzip -cd filename | tar xvf -


its the second time ive seen it today and its driving me mad, haha. so any definition would be helpful. thanks

---

### Post by aeiah on 2009-09-14
its a pipe. you're literally piping the output from gzip -cd filename into the input for tar xvf

i think the hypen at the end ( - ) needs to be used because the pipe doesn't end with a file output, it ends with the results being shown in the terminal.

---

### Post by aeiah on 2009-09-14
this command is used to unpack a tar.gz in one go. as you may know if you use an archive browser, filename.tar.gz is a .tar file inside a .gz file.. so the command uses gzip to get the .tar out, and then pipes that straigh to tar to extract the .tar part.

another example is something i use quite often for finding commands ive used before. the terminal command 'history' shows the log of all commands issued in the terminal. the program 'grep' can be used to print all lines containing a keyword. i use them together so i can find, say, what ssh commands ive issued in the past:
```

history | grep ssh

```
the output from history is piped into grep, which looks for the keyword 'ssh'

---

### Post by aeiah on 2009-09-14
i dont know where your pipe key is, but mine is the uppercase version of \, located to the left of Z

---

### Post by stim on 2009-09-14
the '|' character you see is what is commonly referred to as a "pipe".  It is used to pass information from one program to another program.  

For example 
```
ls | grep bob
```


uses the program grep to search the results of executing the program 'ls' for the search parameter 'bob'.  This will display any files that are named bob.  

[http://en.wikipedia.org/wiki/Pipe_%28character%29#Unix]("http://en.wikipedia.org/wiki/Pipe_%28character%29#Unix")

You can create this character by holding shift and pressing the backslash key (above the enter/return key).

---

### Post by kpholmes on 2009-09-14
thanks, i appreciate the help!

---

