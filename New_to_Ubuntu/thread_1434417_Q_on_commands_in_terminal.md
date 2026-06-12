---
title: "Q: on commands in terminal"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by Trandre on 2010-03-20
I am starting to understand the Linux Ubuntu logics a bit more, but the following puzzels me. Could anyone answer or direct be to a page wich describes the logics behind the commands in the terminal? 

(correct me if the logic is wrong)I see that the commands have two attributes, the first attribute is an action command, the gives an instruction on what to do with the path you descibe in the end of the command. Example sudo, gksudo, apt and so on. The 2nd attribute explans the path as "/var/lib/dpkg/status"

Questions:
What does the commands do?
1.sudo ?
2.gksudo?
3.apt- ?

Example:"gksudo gedit /var/lib/dpkg/status"
4. What part of this string gives the command to unlock an protected file?
5. is Gedit in the command because you have to tell the OS to use that software to edit the file?

Trandre
:popcorn:

---

### Post by ankspo71 on 2010-03-20
In your example:
gksudo gedit /var/lib/dpkg/status

gksudo, gives the user "superuser" administrative rights to do anything on the system.
the same applies to the commands sudo and su
Being that the location of the file is not in your personal home directory, the sudo command is required.

gedit is command name to the text editor.

/var/lib/dpkg/status is the path to the file you want to edit with the text editor.

Here is a good link about the differences betweeen sudo and gksudo
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Here is a tutorial site I'm creating, and part of it deals with working from the command line.
[http://sites.google.com/site/forthelinuxbeginners/](http://sites.google.com/site/forthelinuxbeginners/)

Hope this helps.

---

### Post by r-senior on 2010-03-20
> **Trandre said:**
> (correct me if the logic is wrong)I see that the commands have two attributes, the first attribute is an action command, the gives an instruction on what to do with the path you descibe in the end of the command. Example sudo, gksudo, apt and so on. The 2nd attribute explans the path as "/var/lib/dpkg/status"


Every command is different, there's not always a consistent pattern but in general terms the first word is the command, words that begin with '-' or '--' are options (they modify the command in some way) and other words are parameters to the command.

For example

$ ls (lists files in current directory)
$ ls -l (lists files in current directory using a "long" format option)
$ ls -l /home/trandre (lists files in long format in a specific directory)


> **Trandre said:**
> 
Questions:
What does the commands do?
1.sudo ?
2.gksudo?
3.apt- ?

Example:"gksudo gedit /var/lib/dpkg/status"
4. What part of this string gives the command to unlock an protected file?
5. is Gedit in the command because you have to tell the OS to use that software to edit the file?

1. sudo runs a command in a terminal with admin (root) privileges
2. gksudo runs a graphical command with admin (root) privileges
3. apt-get is a command for managing software and has various options
4. gksudo or sudo gives you temporary admin privileges for the following command
5. gedit is a text editor, running gksudo gedit edits with admin privs

There's a guide on using the command line here:

[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")

---

### Post by Trandre on 2010-03-20
Thanks alot for the answers, ankspo71 and r-senior. _This is what I was looking for.


Trandre
;)

---

