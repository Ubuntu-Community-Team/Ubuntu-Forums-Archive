---
title: "Dont understand find command"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by slik33 on 2009-09-25
[COLOR=#000000]root#  find / -type f \( -perm -04000 -o -perm -02000 \)

I understand that / is the directory and what -type f is, right after that
I don't understand. I know what perm does but not really the codes and the spacing
and the syntax. Can someone please explain.

Also on a separate note how do I use find to find all directories with sticky
bit set. I understand the -perm but what would I put after that. 

Thanks in advance
[/COLOR]

---

### Post by nothingspecial on 2009-09-25
Have a look at [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1128937")

---

### Post by slik33 on 2009-09-25
Yes thank you that was an interesting post. I still would like a step by step break down of what that find command does. Also I do not understand why you have to put a / to protect from shell. Im not sure what that means. Thanks

---

### Post by toupeiro on 2009-09-25
Here's a common find statement I use.

find . -name ".cshrc" -depth -print

the . in this case means the current directory I am in.  the -name and " " is anything in that directory named .cshrc (this does accept wildcards) -depth means search subdirectories as well and -print is to print a full path line for every result.

type: man find

this may help you as well.

---

### Post by akelsall on 2010-06-20
slik33, another option is to use the **locate** command. To me, it's easier to use. The following link explains the differences between find and locate:

[http://www.devdaily.com/blog/post/linux-unix/use-linux-locate-command](http://www.devdaily.com/blog/post/linux-unix/use-linux-locate-command)

[COLOR="Blue"]find[/COLOR] is "real time", while [COLOR="DarkOrange"]locate[/COLOR] searches a database containing your PCs file and directory names. It runs in the background (typically at night), building the database. If you have made recent changes (add/removed files for example), you can force [COLOR="DarkOrange"]locate[/COLOR] to update its database **now** using the command updatedb (must be run as root:  i.e.   sudo updatedb).

Andy

---

