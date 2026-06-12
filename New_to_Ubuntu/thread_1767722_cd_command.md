---
title: "cd command"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by Advait on 2011-05-26
I did some googling but didn't find what I was looking for. I'm a noob. Where do I find the full documentation for the cd command? How do I display the cd command options? Thanks.

---

### Post by sunshine4ever on 2011-05-26
Try **help cd** at the terminal.

---

### Post by azim.charaniya on 2011-05-26
[http://www.computerhope.com/unix/ucd.htm](http://www.computerhope.com/unix/ucd.htm)
[http://ss64.com/bash/cd.html](http://ss64.com/bash/cd.html)
 > 
All the shell commands 
[http://ss64.com/bash/](http://ss64.com/bash/)
:popcorn::popcorn:

---

### Post by powerpleb on 2011-05-26
I'm not sure if there is documentation as such. Usually to find documentation of commands you type ```
man command
```

What do you want to know about cd anyway. There really isn't much to it.

---

### Post by ajaybhat999 on 2011-05-26
Go to Accessories and to "Terminal"
In the terminal type "man cd"..
You will get the documentation for it...

---

### Post by Advait on 2011-05-26
> **ajaybhat999 said:**
> Go to Accessories and to "Terminal"
In the terminal type "man cd"..
You will get the documentation for it...

advait@advait-laptop:~/Apps/Imagination$ man cd
No manual entry for cd

"man cd" doesn't seem to work. See above. Thanks.

---

### Post by Legendary_Bibo on 2011-05-26
> **Advait said:**
> advait@advait-laptop:~/Apps/Imagination$ man cd
No manual entry for cd

"man cd" doesn't seem to work. See above. Thanks.

cd is very basic. It changes your current directory

Full Directory pathname method
cd /directory/path

Starting from current directory (so you don't have to put the whole path name on it

cd ./file/within/directory/you're/in

---

### Post by Advait on 2011-05-26
OK, thanks. all set

---

### Post by Dave_L on 2011-05-26
It's a command built into the shell, so it doesn't have its own man page.

"echo $SHELL" displays the current shell.

For the bash shell, you can find the documentation for built-in commands in "man bash" or "info bash".

---

