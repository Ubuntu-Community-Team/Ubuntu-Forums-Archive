---
title: "Newbie question about Linux shell"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by HighCommander4 on 2009-02-01
Hi everyone,

I have a question about the Linux shell.

What is the difference between

1) typing "sudo <command>"; and
2) typing "sudo bash", and then typing "<command>" at the next prompt

where <command> is the command I want to execute with root privileges? Often the second one works for me but not the first.

Note: My shell is bash to begin with, so I don't think it's an issue of different shells.

---

### Post by NeuralEskimo on 2009-02-01
Good question.

The answer is that in the first case, you have one instance of the bash shell and the command executes with root user privilages. In the second case, you get a second instance of the bash shell, which runs with root user privilages. In this later case, the command also runs as root, but only because the shell is run as root.

Does that help?

---

### Post by HighCommander4 on 2009-02-01
> **NeuralEskimo said:**
> Good question.

The answer is that in the first case, you have one instance of the bash shell and the command executes with root user privilages. In the second case, you get a second instance of the bash shell, which runs with root user privilages. In this later case, the command also runs as root, but only because the shell is run as root.

Does that help?

That makes sense... but if the command is running as root in both cases, how is it that some commands run successfuly when invoked the second way, but fail when ivnvoked the first way?

---

### Post by NeuralEskimo on 2009-02-01
There should be no difference, unless it is syntax issue with complex commands. For example, the following would not run both commands as root:

   sudo command1;command2

Also, the following would not run both as root either:

    sudo command1 && command2

Give me an example of a command that does not work for you.

---

### Post by HighCommander4 on 2009-02-05
Here's an example:

botond@botond-laptop:~$ find django
/usr/bin/find: `./.subversion/auth': Permission denied
./basie/bin/django
./basie/parts/django
./basie/parts/django/django
botond@botond-laptop:~$ sudo find django
find: `django': No such file or directory
botond@botond-laptop:~$ sudo bash
root@botond-laptop:~# find django
./basie/bin/django
./basie/parts/django
./basie/parts/django/django
root@botond-laptop:~# 

When I do "sudo find django", something weird happens, but when I do "sudo bash" followed by "find django", it works fine.

---

### Post by NeuralEskimo on 2009-02-05
Ahhh. Try the following instead:

find -name django     # tell find you are searching for a name
find . -name django   # same as above, execpt search from the current directory
find . -iname django  # same as above, except, the search is not case sensitive

It is true that many commands, under the right conditions, will perform the correct action when presented with a little ambiguity; however, as in any language, human or computer, it often pays to be a little more specific. ;-)

---

