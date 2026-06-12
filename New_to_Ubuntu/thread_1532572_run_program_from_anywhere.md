---
title: "run program from anywhere?"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by erjoalgo on 2010-07-16
This is a very simple question.
There are some commands that can be run from directory from a terminal, such as, gedit, etc.
I installed google earth, but when I type "googlearth" from a terminal, I get command not found. Also, the "run application" program does not recognize google earth. I can run google earth by running the binary from the path where it is installed, but not from anywhere.
The larger question, how do I add custom commands to the "run application" dialog?

---

### Post by emoguitarist06 on 2010-07-16
I can't answer your question directly but the way I've worked it is

Right click on Applications and choose edit menus
Choose the folder I want the App to be and add new item
Navigate to that app and save
(and possible search for or make my own svg file for a nice pic)

EDIT: I just thought about it and Google Earth is probably around in your Applications menu though.

---

### Post by Zeike on 2010-07-16
> **erjoalgo said:**
> This is a very simple question.
There are some commands that can be run from directory from a terminal, such as, gedit, etc.
I installed google earth, but when I type "googlearth" from a terminal, I get command not found. Also, the "run application" program does not recognize google earth. I can run google earth by running the binary from the path where it is installed, but not from anywhere.
The larger question, how do I add custom commands to the "run application" dialog?

The google earth executable is called 'googleearth' not 'googlearth'  If you type it with both e's it should run fine.

---

### Post by erjoalgo on 2010-07-16
I obviously tried that before posting, and it doesnt work. But the larger question is, how to add custom commands to this list of "global" commands that can be run from anywhere without specifying their path. Thanks for the response anyway.

edit:
@[emoguitarist06]("http://ubuntuforums.org/member.php?u=555068")
sorry I didnt read your response, it is also useful, thanks

---

### Post by Zeike on 2010-07-16
> **erjoalgo said:**
> I obviously tried that before posting, and it doesnt work. But the larger question is, how to add custom commands to this list of "global" commands that can be run from anywhere without specifying their path. Thanks for the response anyway.

The 'global' commands are specified by the path variable.  Open a terminal and try "echo $PATH".  You'll see a bunch of directories.  Bash (or another shell) looks into these directories when you type a command.  If you want to add a directory to your path, you can put something like this in your .bashrc:

```

PATH=/home/brandon/bin:$PATH

```
Which will add the directory /home/brandon/bin to the front of your path variable.

In the event of conflicts (ie. two executables with the same name in different directories in your PATH, the one that occurs in the PATH first will be choosen. (I think)

---

### Post by erjoalgo on 2010-07-16
Thank you!
For others who read:

echo $PATH

Shows a list of directories, I picked /usr/sbin, then I created a symlink to googleeearth, like this, 
ln -s ~/.google-earth/googleearth /usr/sbin/
Make sure you can run /usr/sbin/googleearth, or whatever directory you chose, and that the directory is listed in 
echo $PATH
Then you should be able to run it from anywhere.

If someone knows how to associate an image to show on the "run application" to a specific command, that would be nice too.

---

### Post by Zeike on 2010-07-16
> **erjoalgo said:**
> I picked /usr/sbin, then I created a symlink to googleeearth, like this, 
ln -s ~/.google-earth/googleearth /usr/sbin/
Make sure you can run /usr/sbin/googleearth, or whatever directory you chose, and that the directory is listed in 
echo $PATH
Then you should be able to run it from anywhere.

directories named sbin are generally reserved for programs that need to run with superuser privileges. You should put your symlink in /usr/bin instead.

---

