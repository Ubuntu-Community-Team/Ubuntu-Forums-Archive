---
title: "Terminal Questions"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-08
Hi,

Just wondering what ./ does when running something in terminal?

I've used it to get certain things to run, but I don't know what it's actually doing differently.

Also, is sh for running/installing something?


wheres the best place to find about these particular commands and a complete list of commands? On the terminal wiki?

---

### Post by issih on 2009-03-08
[http://linux.about.com/od/linux101/l/blnewbie3_1_3.htm](http://linux.about.com/od/linux101/l/blnewbie3_1_3.htm)

Basically, unless you drop the executable program file into a directory already in the system path, such as one of the bin directories, you have to give the full path to the executable file. Prepending ./ basically means look in the current directory.

sh is one of the shell programs (basically terminal environments), System scripts are often written in shell commands, but bash is more commonly used than sh.

[http://penguin.dcs.bbk.ac.uk/academic/unix/linux/shells/index.php](http://penguin.dcs.bbk.ac.uk/academic/unix/linux/shells/index.php)

Hope that helps

---

### Post by Kareeser on 2009-03-08
Yup. Just like issih said.

Unlike Windows, Linux won't search the current directory when you type in an executable. It looks in the directories specified in $PATH, and stops if it can't find a match.

Appending ./ is like telling the computer: "In THIS directory, run..."

---

