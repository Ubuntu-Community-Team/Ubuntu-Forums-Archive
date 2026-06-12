---
title: "quite new/trying to understand relative directories"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-02-23
So I run a program from my desktop that is an editor, it then invokes bash commands that I send to it (ie: ruby /filepath/filename.rb) I take it that it is running in /home/username/Desktop   ? So, I am trying to run a Ruby file with **relative** file references in it like this (from back when I used to be on Windows)


require '../gsi/Meter'


It looks like the only way I can get it to compile is to put the absolute reference in it... /home/username/ruby/gsi/Meter'


So what I want to know how to is to get the relative file references working again.

---

### Post by Ozymandias_117 on 2010-02-23
Usually your terminal defaults to "/home/username" which would make "../gsi/Meter" to be in "/home/gsi/Meter"... But you would have to have root privileges to save there... Are you sure it's starting in "/home/username"?

---

### Post by TurnOfTide on 2010-02-23
Didn't run it in root.

But yes, it is starting /home/username/


I saw logfiles that were generated there from my ruby script. (they were generated in /home/username/, basically the '.' directory)


Also, this program wasn't installed as a package, it was installed manually from their website. I basically just ran the install binary, and gave it a symbolic link.

Nothing is being *saved* in /home. It was just trying to reference /home/gsi in the "require" line.

---

### Post by TurnOfTide on 2010-02-23
Basically, what is the windows equivalent of "Start in: [folder]" ? (in windows you can launch a program and tell it what its current directory is).

---

### Post by patchwork on 2010-02-24
I'm not sure if it will expand correctly in a script,or if it's what you are looking for, but ~-/<directory> will return to <directory> in the previous working directory.


EDIT:  You can also prompt the user for a path, if you like:

path="";
echo -e "\nEnter Path";
read path

<command> $path/gsi/Meter

---

