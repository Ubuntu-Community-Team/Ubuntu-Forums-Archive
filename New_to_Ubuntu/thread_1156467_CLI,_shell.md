---
title: "CLI, shell?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by Toliot on 2009-05-11
I was wondering what I should start with, I honestly have no clue with linux, what should I learn? Bash? C? 

if you don't mind sharring your knowledge please do, and any resources are greatly appreciated

-toliot

---

### Post by Simian Man on 2009-05-11
C is a programming language, not a shell language like bash.  There are other shells like csh, tcsh and sh, but just stick to bash because it is the most common one.

Start off by learning the basics like ls, cd, cp, mv and so on.  There are a *lot* of things you can do with the shell but don't try to learn them all.  Just learn them as you need them.

---

### Post by Toliot on 2009-05-11
Roger, ill try to learn what i can

do you know a site to teach me the "basics"?

---

### Post by starcannon on 2009-05-11
[The Linux Command Line For Beginners]("http://www.linuxplanet.com/linuxplanet/tutorials/6630/1/")

[http://www.linuxplanet.com/linuxplanet/tutorials/6630/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6630/1/)

Enjoy

---

### Post by Dill on 2009-05-11
The way I would suggest starting is to learn how the shell works. C is a bit more advanced, and knowledge of C isn't essential to using Linux well. C is certainly a lot of fun, though, and I definitely suggest you check it out, too!

There are plenty of good references online and in print for new shell users. Just Google for "Learning bash", "Linux command line", "learning Linux shell", etc. . I found the "Linux Pocket Guide" a great text reference, and it really does fit in your pocket (well, your back pocket, but you can't expect a book on such a powerful concept to be _that_ small : ) ).

The way I started out learning the shell was to stop myself from doing something on the user interface and try to figure out how to do it through the shell. Chances are you'll find a way, and chances are it will be easier... eventually. For instance, instead of using the Synaptic interface to install a piece of software, try typing 

```
sudo apt-get install <package_name>
```

instead. Instead of using nautilus to browse and drag-and-drop files, try using 'cd' to navigate through directories and 'mv' or 'cp' to move or copy files to a given location. It does take a while to _really_ get comfy with the shell, but once you do, your fingers will fly.

Tab completion is your friend, and will increase your shell-speed exponentially: [http://en.wikipedia.org/wiki/Command_line_completion](http://en.wikipedia.org/wiki/Command_line_completion)

Once you feel comfortable using a handful of commands on their own, try linking them together with pipes: [http://www.linfo.org/pipe.html](http://www.linfo.org/pipe.html). Basically, pipes allow you to take the output of one command and feed it as input to another command. For instance, if you wanted to see all the users logged into a computer, you could take the output of 'finger' and play around with it to get you what you want:

By itself, 'finger' prints output like this:

```
satherdy@euler:~$ finger
Login     Name                Tty      Idle  Login Time   Office     Office Phone
estipona  NAME   pts/7      3d  May  7 21:03 HOST
root      NAME               *tty1     169d  Nov 23 11:53
satherdy  NAME        pts/2          May 11 18:28 HOST
tapesamu  NAME         pts/1      2d  May  9 01:17 HOST
walker    NAME        pts/4   10:54  May 10 20:49 HOST

```

But if we wanted to narrow it down to just the unique users, we could use 'awk' to print just the first column:

```
satherdy@euler:~$ finger | awk '{print $1}'
Login
estipona
root
satherdy
tapesamu
walker

```

But of course, "Login" isn't a user -- it's a heading -- so we can take that first line out with 'sed':

```
satherdy@euler:~/bash$ finger | awk '{print $1}' | sed 1,1d
estipona
root
satherdy
tapesamu
walker

```

... etc., etc. . Piping allows you full control over the data with which you're working, and allows you to use a set of small programs to apply a series of operations to that data, multiplying your power far beyond what the creators of each individual program intended...

But yeah, in essence, just play around and learn all you can... keep trying out new commands and try to rock and roll. Good luck, and have fun!

Cheers,
Dill

---

### Post by Dr Small on 2009-05-11
Here is a website that will teach you some of the basics:
[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by orange-wedge on 2009-05-11
the best place to start is with each command's installed manual to explain the syntax necessary to use it:

[html]
man commandname
[/html]for example try running this:

[html]
man ls
[/html]

EDIT:  to navigate the manual use your space bar to perform a "page down", return to go down a line at a time, and the 'q' to exit the manual.

---

### Post by starcannon on 2009-05-11
Heres a nice little list of basic commands with a brief description of each:
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

