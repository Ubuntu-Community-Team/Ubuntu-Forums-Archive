---
title: "Help in installing Borland C++ for DOS in Ubuntu"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by Lunkwill on 2008-12-10
Sorry, but I'm a newbie. 
I installed Wine and Dosbox on my Gutsy Gibbon, but when I run the Turbo C++ 3.0 for Dos installation, it sort of stops on the command
SEARCHING ZIP: D:/TURBOC30/BGI.ZIP
Another thing. I installed the C++ 4.5 for Windows (again using Wine). The installation was successful, but I can't find the installed files. Help?

---

### Post by Titan8990 on 2008-12-10
Have you considered using gcc that is native to Linux and UNIX based systems?

---

### Post by DGortze380 on 2008-12-10
> **Lunkwill said:**
> Sorry, but I'm a newbie. 
I installed Wine and Dosbox on my Gutsy Gibbon, but when I run the Turbo C++ 3.0 for Dos installation, it sort of stops on the command
SEARCHING ZIP: D:/TURBOC30/BGI.ZIP
Another thing. I installed the C++ 4.5 for Windows (again using Wine). The installation was successful, but I can't find the installed files. Help?

Is there a particular reason you want Borland and C++ 4.5??

gcc is a standard c compiler on all UNIX systems, g++ is included in gcc and is the c++ compiler.

there are a number of IDEs for linux which utilizes those free, native, and tested compilers.

---

### Post by Lunkwill on 2008-12-11
No, my class is using Borland Turbo C++ 3.0 for Dos only.

---

### Post by PmDematagoda on 2008-12-11
> **Lunkwill said:**
> No, my class is using Borland Turbo C++ 3.0 for Dos only.

Isn't trying to learn programming in DOS a bit of a, well, dead-end?(Correct me if mistaken please.) In any case, if you are using standard syntax and code, you should be able to use g++ just as well.

---

### Post by Sirron on 2008-12-11
If you can't use anything else but Borland and DOS, perhaps you'd be better off using a virtual machine? For which I recommend [www.VirtualBox.org](www.VirtualBox.org).

As to DOS, you may need to... obtain... a copy of MSDOS, but it's worth trying [_FreeDOS_]("http://www.freedos.org/") which may be compatible.

Try [_this_]("http://virtualbox.wordpress.com/images/freedos/") image. Sorry, I'm not at linux machine at the moment so I can't try it.

---

### Post by ashwin.kj on 2009-01-06
> **Lunkwill said:**
> Sorry, but I'm a newbie. 
I installed Wine and Dosbox on my Gutsy Gibbon, but when I run the Turbo C++ 3.0 for Dos installation, it sort of stops on the command
SEARCHING ZIP: D:/TURBOC30/BGI.ZIP
Another thing. I installed the C++ 4.5 for Windows (again using Wine). The installation was successful, but I can't find the installed files. Help?

I understand UR problem.The gcc and all IDE available 4 Ubuntu does not match the codes that I learn at school and throws a lot of errors.

I think u can slove UR problem using dosbox and installing the Turbo c++ or any other variant of it.
Detailed procedure of it given in the link below
[http://dogbuntu.wordpress.com/2007/07/05/using-dosbox-to-run-turbo-c-in-ubuntu-linux/](http://dogbuntu.wordpress.com/2007/07/05/using-dosbox-to-run-turbo-c-in-ubuntu-linux/)

Try it out.It worked 4 me



Do add the [SOLVED] to your thread if you have recieved a satisfactory solution by going into Thread Tools.

---

### Post by DGortze380 on 2009-01-06
> **ashwin.kj said:**
> I understand UR problem.The gcc and all IDE available 4 Ubuntu does not match the codes that I learn at school and throws a lot of errors.

No offense, but if you can't adapt your code for a different compiler, you have bigger issues. ANSI C will compile on on C compiler... look at a few tutorials and figure out why you're getting errors. It's make you a stronger programmer than wasting time on dosbox will.

---

### Post by bhadotia on 2009-01-06
> **Lunkwill said:**
> Sorry, but I'm a newbie. 
I installed Wine and Dosbox on my Gutsy Gibbon, but when I run the Turbo C++ 3.0 for Dos installation, it sort of stops on the command
SEARCHING ZIP: D:/TURBOC30/BGI.ZIP
Another thing. I installed the C++ 4.5 for Windows (again using Wine). The installation was successful, but I can't find the installed files. Help?

Just searched around google and found [this]("http://helpforlinux.blogspot.com/2008/12/install-borland-turbo-c-in-ubuntu.html"). 
My class also uses Turbo C++ but I use Code Blocks and Geany in ubuntu. When I was new, I was also a little reluctant to use these native IDEs, but, in my course, I don't find any difference whether I use a Win IDE or a native Linux one.
To install the above to IDEs in ubuntu, give the command below in the terminal:
```
sudo apt-get install codeblocks geany
```
Other native IDEs include eclipse, netbeans, anjuta which are not for learners in my opinion.

---

