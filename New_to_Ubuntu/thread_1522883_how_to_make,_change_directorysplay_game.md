---
title: "how to make, change directorys/play game"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by ECET on 2010-07-02
Hello all, I was trying to install a game and the instructions I got from a friend of mine shows me this line:   

#!/bin/bash

cd /home/matt/games/portal-prelude
wine hl2.exe -game portal

Now I realize I would have to have this in my name of course, but I have no idea how to make the "home" or "games" or "portal-prelude" directory's. Right now when I open terminal, I have this:    michael@michael-laptop:~$ 
 So, unlike windows with the MKDIR.....I am now lost. I have this particular game extracted in a folder on my desktop. Can I please get some assistance?

---

### Post by -humanaut- on 2010-07-02
hmm... I honestly recommend checking the wine homepage and wiki for instructions on it I don't use wine but heres a link to there site/wiki [http://www.winehq.org/](http://www.winehq.org/) that should tell you everything you need to know.

---

### Post by ECET on 2010-07-02
thanks, but I already have wine installed....I just need to know the command structure....how to make, change directorys.....

---

### Post by Penguin Guy on 2010-07-02
```

~ = /home/<username>
cd = change directory
mkdir = make directory
ls = list files

```
You can read more about the CLI here: [http://linuxcommand.org](http://linuxcommand.org)
I don't know about the Wine part, but I'm sure someone can give you some pointers there.

---

### Post by sgosnell on 2010-07-02
#!/bin/bash is the start of a shell script.  That's a text file placed somewhere on your computer, presumably in your home directory somewhere.  Running that script will perform all the actions in the script.

You should install the game via wine, not manually.  You should be able to click on the install file, presumably a .exe, and open it with wine.  You may need to set the executable bit by right-clicking on it, selecting Properties, and on the Permissions tab check the box for "Allow executing file as a program".

---

### Post by ECET on 2010-07-02
THANKS GUYS!!! I appreciate the help, and I'll check back in an let cha' know how it went.....:D

---

### Post by dinamic1 on 2010-07-02
the terminal is case sensitive meaning "MKDIR" is not the same as "mkdir", the command for making a directory is the same as in dos: mkdir <dir_name>

ls - list all the files in directory/subdirectory

if you like a visual way of doing this operations you can use nautilus or install mc (midnight commander) similar to norton commander.

---

### Post by sgosnell on 2010-07-02
You don't need to make /home, it's made during the install and mounted automatically, along with your user subdirectory.  You can make the games/portal-prelude subdirectories either from the command line or with Nautilus file manager.  I still think installing the game will be a better idea, and will make the necessary directories, although not necessarily the ones you posted.  Just because your friend has them there doesn't mean you have to, or should.  Installing it with wine will make the proper directories, put the files where they should be, and put a shortcut on your desktop if you like.  You won't need a separate shell script.

If you do it manually, and use the script, you run that in a terminal via ```
./scriptname
```, where scriptname is the filename of the script.  You need to make it executable, and you can also run it by double-clicking on it in Nautilus.

---

### Post by ECET on 2010-07-02
well.........IT WORKS!!!!.......thanks sgosnell!!!....I followed your advice and made the exe. executable by checking that box......its as simple as your instructions made it seem.....so thank you...thank you!!!!.....:D:D:D:D:D

---

### Post by sgosnell on 2010-07-02
You're welcome.  Glad I could help.

---

