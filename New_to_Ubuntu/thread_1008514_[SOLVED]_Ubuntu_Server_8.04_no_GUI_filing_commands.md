---
title: "[SOLVED] Ubuntu Server 8.04 no GUI filing commands"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by DrZoidy on 2008-12-11
hello all, I am totally new to Ubuntu server 8.04. when installing I was expecting a GUI as in the desktop edition but on completion I find its a text based interface like dos which I know my way around but I Haven't a clue how to navigate the this OS. I want to install UT 99 on my machine to have a dedicated development game server to play with and have found instructions to do this but I cant even copy a file to the hard drive from a CD-ROM as I don't know any commands. I have looked at help | more but cant make head nor tale of anything obvious. can anyone help with these simple tasks. thanks

---

### Post by beno1990 on 2008-12-11
The server edition of any Linux, or Unix OS for that matter, doesn't come with a GUI interface by default. If you want to install one you'll have to do it manually.

```

sudo apt-get install xubuntu-desktop

```

But installing a GUI on a server operating system is strongly discouraged, and for a good reason.

---

### Post by DrZoidy on 2008-12-11
no I don't want to install a GUI as this would eat resources that would impair the servers performance, what I need is some help on getting around. all I need to do is copy a file from a CD-ROM to the /home/my user/ directory so I can work on it. 

i have been goggling all day to fine a basic manual to do basic tasks like copying, deleting, moving and creating files. 

is there anyway to list the files and folders in the current directory like an equivalent to "dir" in dos, or do i need to install something to do that.

---

### Post by b0b138 on 2008-12-11
cd command to change directory (just like dos) ie. cd foldername  Also, cd .. to go up a level. cd /Full/Path/ToFolder (case sensetive)

Copy and move are cp and mv.  cp source destination  cp /media/cdrom/UTfilename /where/you/want/UTfilename  add -r to copy folders and everything in that folder including all subfolders cp -r /media/cdrom/UTfolder /where/you/want/UTfolder

You can add --help to any command to get help with that command and see all the options cp --help

Oh, ls will list contents of folder (dos equivalent of dir)

---

### Post by howefield on 2008-12-11
Try the first few chapters here

[http://gd.tuwien.ac.at/linuxcommand.org/learning_the_shell.php](http://gd.tuwien.ac.at/linuxcommand.org/learning_the_shell.php)

That should help you learn to navigate your system.

Also I think webmin might help you get certain things done without resorting to a GUI.

[http://www.webmin.com/](http://www.webmin.com/)

---

### Post by nhasian on 2008-12-11
here's a good place to start for beginners

[http://linuxcommand.org/](http://linuxcommand.org/)

and

[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

---

### Post by b0b138 on 2008-12-11
Thought of something else you'll want to know

linux does not really like spaces in names. To work with files and folder with spaces, you'll need to add \ with the space. ie. cp /home/user/filename\ with\ spaces  Or. put it in parenthesis  cp "/home/user/filename with spaces"

You can also you the tab to autocomplete your typing.  cp /home/user/fil at this point hit tab to have it fill in the rest (assuming a file name filxxxxx is unique. If there are more files starting with fil, it wont fill it in.

---

### Post by DrZoidy on 2008-12-11
That is awesome guys thanks for all your help, that will get me started getting around the system. thanks for responding so quickly:p:P:P:P

---

### Post by cornev5 on 2008-12-28
Thanks guys, this will get me started:)

---

