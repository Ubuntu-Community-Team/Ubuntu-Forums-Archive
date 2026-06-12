---
title: "Purpose of makeinfo"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by newport_j on 2009-08-28
What is the purpose of the makeinfo file. What is in it. When I ran ./configure to install a second and earlier version of gcc (actually gcc-3.3.5) it came back said it either could not find makeinfo or it was too old. I think it is an important file. I just wish that error was not there.

Bottom line: reason for having a makeinfo file.


newport_j

---

### Post by Penguin Guy on 2009-08-28
[COLOR="Green"]Makeinfo[/COLOR] is not a file, it's a program, more information about it can be found [[COLOR="Blue"]here[/COLOR]]("http://www.cs.utah.edu/dept/old/texinfo/makeinfo/makeinfo.html").

From [[COLOR="Blue"]this topic[/COLOR]]("http://ubuntuforums.org/showthread.php?t=16734") I found that these commands may help you:
```
sudo apt-get install build-essential
sudo apt-get install texinfo
```

---

### Post by newport_j on 2009-09-08
What you say is true, but I believe incomplete. The two commands build-essential and texinfo will solve the problem. However, I believe that you must do more. As shown in yur own hyperlink the use of these commands is not the total solution. Some damage that is done when you initially run the ./configurre program must be undone before those comands can be effective. 
 
That is what I am concerned about. I have used both build-essential and texinfo and I have not resovled the issue of "modern makeinfo not found". What else do I have to do to get those two commands to work?
 
Respectfully,
 
newport_j

---

