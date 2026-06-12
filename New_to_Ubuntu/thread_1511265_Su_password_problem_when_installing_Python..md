---
title: "Su password problem when installing Python."
date: 2010-06-16
forum: New to Ubuntu
---

### Post by Krolblach on 2010-06-16
Hi all,
Second time I've asked for basic help in as many days...ah well.
I'm trying to install Python programming language and am having a bit of difficulty. In the README file it says:

To start building right away (on UNIX): type "./configure" in the
current directory and when it finishes, type "make".  This creates an
executable "./python"; to install in /usr/local, first do "su root"
and then "make install".

I got past the ./configure part (after some immediate uncertainty) and proceeded to type in 'make'. Lots of lines flashed by on the screen for the best part of 5 mins, which I assume is normal when starting up a new program. However, when this had finished, I typed in 'su root' as instructed and was asked for 'password'. I entered my user password (I am the only user on my computer and have, to my knowledge, full admin rights.). However, it came up with:

su: Authentication failure

Is there some password I should have entered earlier in the ubuntu setup process? How different is 'su' to 'sudo' and can someone explain to me in detail what they do?

Hope someone can help.
Cheers,
Sam

---

### Post by Bachstelze on 2010-06-16
Python is installed in Ubuntu by default. No need to do that.

---

### Post by bodhi.zazen on 2010-06-16
Is there some reason you are compiling Python and not using python from the Ubuntu repositories ?

Also, Ubuntu uses sudo, not su

So:```
sudo -i
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by QIII on 2010-06-16
Bachstelze probably is on to what is the final solution.

With regard to "su root"...

By default, the root user is disabled in Ubuntu.  I won't tell you how to enable it, as it is against forum rules and I wouldn't do it anyway.  If you know how to do it, you probably know what you are doing.  If you don't know how to do it, you probably don't know the damage you can do.

So if you try to become root, you won't be able to.  You aren't root.  You are a user in the sudoers file.

Just use "sudo" ("gksudo" for graphical interfaces), which elevates your privileges temporarily so you can do things like this.

---

### Post by Krolblach on 2010-06-16
I had no idea Python was an automatic Ubuntu program. Can I get it by looking in Applications>Ubuntu Software Centre?

Also, I did manage to enable root user and set a password, but if you tell me not to mess around with that in any way, I'll listen to you.

Thanks for the numerous responses,

Sam

---

### Post by The Cog on 2010-06-16
> **Krolblach said:**
> I had no idea Python was an automatic Ubuntu program. Can I get it by looking in Applications>Ubuntu Software Centre?
No. Python is not an application, it is an interpreter that runs programs. 

You can get a python command prompt (most tutorials for python start by using the interactive interpreter) by launching a normal command prompt (Applications, Accessories, Terminal) adn entering the command **python**. This gives you a >>> prompt where you can enter python statements like **print 3 * 5**.

When you come to writing python programs, you need to put the python commands into a text file, then run the text file. For instance, from the command line, create and edit a python program file by entering the command **gedit test.py**. Put these lines into the file:
```
for x in range(1, 11):
    print x, "times", x, "equals", x * x
```
Save the file and quit the editor, then run the program with the command **python test.py**

You might prefer the editor **geany** to gedit - it's in the repositories, and I recommend you try it some time. However, gedit is certainly enough to get you started.

> Also, I did manage to enable root user and set a password, but if you tell me not to mess around with that in any way, I'll listen to you.I would advise restoring the root account to its locked state with the command
**sudo passwd -l** (that -l is a lower-case L, not one).

---

