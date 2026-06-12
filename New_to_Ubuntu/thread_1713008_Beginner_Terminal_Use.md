---
title: "Beginner Terminal Use"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by kevinvug on 2011-03-23
I need a complete terminal beginners manual. I have looked at the documentation on these forums and other sources from other places on the internet. I have not found a complete set of commands and other faq for complete beginners.

---

### Post by TeoBigusGeekus on 2011-03-23
[http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download")

---

### Post by fabricator4 on 2011-03-23
> **kevinvug said:**
> I need a complete terminal beginners manual. I have looked at the documentation on these forums and other sources from other places on the internet. I have not found a complete set of commands and other faq for complete beginners.

Don't Google 'terminal', Google the name of the shell, which is bash.  This guide always comes up in searches, and I've used it myself:

[Bash Reference Manual]("http://www.gnu.org/software/bash/manual/bashref.html")


Chris

---

### Post by Frogs Hair on 2011-03-23
I have not found anything all inclusive , but these along with the Ubuntu Pocket Guide  were useful to me .[http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/)
[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by Hippytaff on 2011-03-23
I find these useful 
[http://wiki.bash-hackers.org/doku.php](http://wiki.bash-hackers.org/doku.php)
and
[http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/](http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/)

Ignore the title...it's not advanced to begin with

---

### Post by Ghost_Mazal on 2011-03-23
> **Frogs Hair said:**
> I have not found anything all inclusive , but these along with the Ubuntu Pocket Guide  were useful to me .[http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/)
[http://linuxcommand.org/](http://linuxcommand.org/)

I used the linuxcommand downloadable pdf a lot. +1 for that one.

Takes you step by step right from the start.

---

### Post by kevinvug on 2011-03-23
Thank you all for the quick replies... However I am a little stumped. I have use mkdir from terminal to creat Folder_1 on my desktop and am denied when invoking rm Folder_1... It says that rm: cannot remove `Folder_1': Is a directory, What gives?

---

### Post by The Cog on 2011-03-23
The command for removing a directory is ```
rmdir Folder_1
```
although the folder must be empty for that to work. A command that will remove a folder and all its contents is ```
rm -rf Folder_1
```

---

### Post by kevinvug on 2011-03-23
Sorry, was a matter of reading... Syntax should have been  rm -r Folder_1 

Thank you folks

---

### Post by KL_72_TR on 2011-03-23
> **kevinvug said:**
> Thank you all for the quick replies... However I am a little stumped. I have use mkdir from terminal to creat Folder_1 on my desktop and am denied when invoking rm Folder_1... It says that rm: cannot remove `Folder_1': Is a directory, What gives?
Use: [rm -r] [/home/user-name/Desktop/Folder]
Remember to user [-r] for 'recursive' or use both [-rf], f-force. If you want to remove a directory you created and its content.
Happy Linux :-)

---

### Post by CVGH on 2011-03-23
> **TeoBigusGeekus said:**
> [http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download](http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download)

WOW! Fantasic resource!! Many Thanks!!

---

### Post by KL_72_TR on 2011-03-23
> **The Cog said:**
> although the folder must be empty for that to work. ```
rm -rf Folder_1
```
For me the command [rm -r] works fine even if the folders have contents inside.

---

### Post by kevinvug on 2011-03-25
Thank you all for the reference. I am feeling quite confident after only a day of reading and executing commands from the terminal.

---

### Post by Joeb454 on 2011-03-25
> **KL_72_TR said:**
> For me the command [rm -r] works fine even if the folders have contents inside.

From what I recall, the -f option will assume you definitely want to, and won't ask before removing anything.
I think it only asks for files with certain permissions though, I can't remember exactly.

---

