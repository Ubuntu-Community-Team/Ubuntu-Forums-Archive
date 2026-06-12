---
title: "Questions about write permissions of manually installed programs in /usr/local/"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by MrPok on 2010-01-15
Hello,

I have been using Ubuntu for about a year now and I am happy with it, but even after reading a lot of manuals and forum posts I am confused about the following matter concerning manually installed programs. For the sake of readability I have defined a *general* questions and my *case-specific* questions. Any response on the following is more than welcome:

[SIZE="3"]General question:[/SIZE]
[LIST]
[*]When I place a program consisting of java jars in */usr/local/<programname>* and run it with *java -jar* will it be able to _add_ or _change_ files in this directory (or in */usr/local/*) during its runtime?
[/LIST]
[SIZE="3"]Case-specific question:[/SIZE]
I am trying to run and use a platform for developing multi-agent systems called *Jadex*. (info: [website]("https://sourceforge.net/projects/jadex/"))
I have placed it in */usr/local/jadex-2.0-beta4/* and start it from the commandline using a self-made script containing an *export CLASSPATH* and a *java -jar* command. 
When executed as normal user, the program starts but is unable to save its settings. When I run the script as *sudo*, the program starts and is able to save the settings. 
To the novice ubuntu ("or *nix" for that matter ;)) user this sounds like a permission problem.
The file that saves the configuration of the program is located in a sub-directory of the program* /usr/local/jadex-2.0-beta4/lib/*; the previous version of the program used to store the file in the root of *home/<username>*, but not this version. 
[LIST]
[*]Can I circumvent this problem by changing the ownership (chown) or permissions of the directory and its sub-directories to something else than *root* so the program can save its setting, or would this be very unwise (security or something)? 
[*]Or should I place java programs, not in *usr/local/* but somewhere else (for example in *home/<username>*)?
[/LIST]

If you need me to include more details on the problem or what I want to do please let me know.

Any advice is highly appreciated!

Kind regards,
Paul

---

### Post by tom4everitt on 2010-01-15
First, the readability is great! 

Generally the idea in *nix systems is that the same program should be possible to use for several users, and that simply backing up your home folder will back up all files and all settings. Therefore *nix-programs generally store user settings in a hidden file/directory in the users home folder. 
And since everyone expects to find their settings for their program in their home folder, it might be unwise to go against this convention. 


As you suspect, it is most likely a permission problem you're experiencing. You should be able to fix this by the following command:

sudo chmod 777 /usr/local/<folder-name>

which will allow the program (and any other program) to write to this folder no matter which user is executing it. 

This will possibly lead to other problems however:
- As mentioned, any program, run by any user, will be able to change the settings for your program.
- If your program creates files, you must make sure these new files also has full permissions. This can be achieved by running:

sudo chmod -R 777 /usr/local/<folder>

every time you quit the program or something.


EDIT: I'm not sure I was clear enough on the point that I would recommend you to use the home folder for settings :) I REALLY DO.

---

### Post by tom4everitt on 2010-01-15
I'm not sure I was clear enough on another general *nix idea:

A program (or process, rather) will always be limited by the same permissions that's limiting the user owning it.

---

