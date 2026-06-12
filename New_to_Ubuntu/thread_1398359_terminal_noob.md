---
title: "terminal noob"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by serkit on 2010-02-04
i wanna start messing wit the terminal ..i was watching a friend mess wit it last night and i learned a couple commands like ls & sude make  

just to start off i wanna try to go to my pictures..but im not to sure how
 i tried the sudo make pictures.documents but it wouldnt let me

any help

---

### Post by Enigmapond on 2010-02-04
[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)

---

### Post by bkratz on 2010-02-04
Here is another

[https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=Terminal](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=Terminal)

---

### Post by oldos2er on 2010-02-04
[https://help.ubuntu.com/9.10/basic-commands/C/](https://help.ubuntu.com/9.10/basic-commands/C/)

---

### Post by doas777 on 2010-02-04
learn the basics of navigation first (cd, ls, cat, mk/rmdir, touch, pwd, etc), and then just take it as it comes (unless you really wanna be a shell guru). the rest will come with time, exposure, and experience.

the commmand you are looking for is:
cd /home/<username>/Pictures 

(replace <username> with your username).

cd is change directory, so you use it to move around from dir to dir.
ls lists the files in a directory

don't use 'sudo make' (it's sudo not sude) unless you are compiling an application package from source code. you will know when you are doing that.

---

### Post by steveneddy on 2010-02-04
To navigate to your Pictures folder the command is:

```
cd ~/Pictures
```

**cd** means **[COLOR="Red"]c[/COLOR]hange [COLOR="red"]d[/COLOR]irectory**

the **tilde** **[COLOR="red"]~[/COLOR]** means go to the Home folder

/Pictures is the name of the folder. The names of all folders must match, caps and all.

To see what's in the Pictures folder after you have navigated to Pictures in terminal, simply type

```
ls
```

to see a **[COLOR="red"]l[/COLOR]i[COLOR="red"]s[/COLOR]t** of files in that folder.

---

### Post by BT1 on 2010-02-04
Best way to learn terminal ('m learning it too) is to make a list of all the programs and stuff that you normally use on a daily basis, and find out how to do it through terminal and not a program. Remember that many programs with an icon in Ubuntu are really programs that run commands in its own terminal off screen. So why can't you do that too? It'll take more time to type in the variables and stuff but then you'll learn the backbone of most Linux systems on the net.

When you get down what you do on a daily basis, explore the Ubuntu Software Center and see what other nifty programs are out there, and then do what you did with the stuff you normally do. Just find out how to do what those programs do. By the time you branch out into new stuff, you'll know the basics.

Have fun!

---

### Post by nothingspecial on 2010-02-04
> **serkit said:**
> sude make  


typing things incorrectly can lead to problems.

---

### Post by audiomick on 2010-02-04
Do not use "rm" until you know exactly what it does.
Look at
```
man rm
```

---

### Post by thameera on 2010-02-04
> **BT1 said:**
> Best way to learn terminal ('m learning it too) is to make a list of all the programs and stuff that you normally use on a daily basis, and find out how to do it through terminal and not a program. Remember that many programs with an icon in Ubuntu are really programs that run commands in its own terminal off screen. So why can't you do that too? It'll take more time to type in the variables and stuff but then you'll learn the backbone of most Linux systems on the net.

Agree with BT1. What I did was the same. Trying to get your things done through the terminal is fun and makes you learn the terminal a lot.

---

