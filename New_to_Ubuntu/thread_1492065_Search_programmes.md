---
title: "Search programmes"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by Lemuel111 on 2010-05-24
I'm trying to find a file (I know the text in it) but I don't know its name. Is their a search programme I can use which allows me to type the text which is included in the file & then it will find the file I want?

Thanks

---

### Post by KdotJ on 2010-05-24
I'm not 100% but you may be able to do this with Gnome-Do. You can install it from the software centre, search for Gnome Do. You may have to enable extra plugins to search through files... Worth a shot I guess

---

### Post by Lemuel111 on 2010-05-24
Have given it a try and didn't work.

---

### Post by jvector on 2010-05-24
If you prefer a GUI solution, there is a 'Search for Files...' under the Places menu (yeh, not the most obvious place ). Under 'select more options' you can fill in a field and say 'Contains the text:' to have it search for files with the text you need. This will work for plain text files and html files as well as .doc files in Open Office format but will not work for all other formats - does not find text in PDF files, for example.

The best way to do this depends on a couple of things: what kind of files contain the txt you want (plain text, documents, other types..) and how happy you are with the command-line terminal. If you are happy with the shell, then the 'find' and 'grep' commands can do a lot for you.

---

### Post by the_doc on 2010-05-24
Yes, grep will get the job done.  Something like the following basic command will search for "TEXT" in "DIRECTORY" and recursively through its sub directories:

grep -r "TEXT" DIRECTORY/

May take a while though.

---

### Post by Lemuel111 on 2010-05-25
Thanks for that. That has done the job! How do you kill the process i.e. press an equivalent "stop" button?

---

### Post by RiceMonster on 2010-05-25
> **Lemuel111 said:**
> Thanks for that. That has done the job! How do you kill the process i.e. press an equivalent "stop" button?

Ctrl c

---

### Post by houseworkshy on 2010-05-25
Closeing a terminal terminates the process, it should warn you of this if a process is running when you close.  One thing linux is superb at is finding things, there are quite a few ways in the terminal and GUI interphases can be installed too.  Two commands which have become favorites of mine may help you learn about it and almost anything else command line related.
The first is "apropos" This searches for whatever word follows it in the various manual pages.  This is very useful for when you know what you want but don't have a clue what the command may be.  So, for example, "apropos find" or "apropos search" would be a good bets for getting the command you want.  With a bit of creative thinking one can usually dig out relevent commands.  I remember it with the mnemonic "all processes possible" I've no idea if that is why it is called that but as linux is often logical it may be.
The other is "man", this pulls up the manual page for each command.  Same format.   So relating to find one may have tried "apropos find" and got a list of commands which may serve your purpose.  Then one would look closely at them one at a time with man, eg "man locate", which would give details of what the command does and how to use it.  To clear the manual just enter "q".
One can open many terminal so one can have the manual in one whilst working in another, one can also copy and paste.  Very nice 
When ever you install a command the manual page comes with it so even if the problem is not not being able to get online help is always there.  One is never quite stranded with linux.   I like this feature a lot, I hope you find it useful too.

---

