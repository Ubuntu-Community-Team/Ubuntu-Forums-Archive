---
title: "Ubuntu 9.04: How to add to PATH?"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by ItecKid on 2009-06-08
Hello,

I am trying to install application perl2exe on my system.  When I run 
```

./setup

```
on my system, I get this:

```

Please add the following directories to your PATH:
<dir1>
<dir2>

```

How to do this?

Thanks for the help.

---

### Post by Mornedhel on 2009-06-08
```
export PATH=<dir1>:<dir2>:$PATH
```Works only for that instance of bash, and only until you close the terminal.

Add it to the end of your .bashrc if you need it to be permanent.

Out of curiosity (I code in Perl myself), what do you need perl2exe for ?

---

### Post by kevdog on 2009-06-08
Your PATH environment variable is either located in your:

~/.bashrc
or
~/.bash_profile
or
~/.profile

file, depending on your setup.  Open the appropriate file -- it should be only included in one of these files, (please note that it should be located in your .bashrc file since this file is read in both gui and nongui logins), and then simply add the directories to the PATH line, separating the directories by semicolons.  Its pretty easy to figure out, so don't sweat it.  When you are done editing, do a 
source ~/.bashrc (or whatever file you edited)

You're good to go!

---

### Post by ItecKid on 2009-06-08
Ah.  Thank you very much!

---

### Post by jmvbxx on 2009-12-18
The problem I have is that if I make a change to ~/.bashrc as follows:

PATH=/home/user/dir

What that does is removes all other directories from $PATH and leaves me with just that one.

How can I add just the one directory into .bashrc and still maintain my existing $PATH.

Where are those other directories coming from?

---

### Post by nothingspecial on 2009-12-18
> **kevdog said:**
> Your PATH environment variable is either located in your:

~/.bashrc
or
~/.bash_profile
or
~/.profile

file, depending on your setup.  Open the appropriate file -- it should be only included in one of these files, (please note that it should be located in your .bashrc file since this file is read in both gui and nongui logins), and then simply[COLOR="Red"] add the directories to the PATH line, separating the directories by semicolons[/COLOR].  Its pretty easy to figure out, so don't sweat it.  When you are done editing, do a 
source ~/.bashrc (or whatever file you edited)

You're good to go!

See the red bit.

---

### Post by jmvbxx on 2009-12-18
Yup just found that .. I mistakenly thought that adding a new path to bashrc simply added it to $PATH.  I didn't realize that it would overwrite it completely.

I solved as follows:

PATH=$PATH:/home/user/scripts/ ;export PATH


Thanks for the quick feedback!

---

### Post by nothingspecial on 2009-12-18
You know, if you don`t want to mess about too much with your file system that ~/bin is in your path in a default Ubuntu install.

This means that all your bash scripts and stuff can be kept there without getting into the bones of your system.

Simply issue mkdir ~/bin and put all the funny stuff in there. You`ll be able to execute it but it cant harm your install...........I think?????

---

### Post by Mornedhel on 2009-12-18
> **nothingspecial said:**
> You know, if you don`t want to mess about too much with your file system that ~/bin is in your path in a default Ubuntu install.

This means that all your bash scripts and stuff can be kept there without getting into the bones of your system.

Simply issue mkdir ~/bin and put all the funny stuff in there. You`ll be able to execute it but it cant harm your install...........I think?????

Yup. This is The Right Way To Do It (tm).

My default PATH looks like this : /home/myusername/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

(Although the scripts not being able to harm your install only depends on what permissions they have : if they are root-owned and executable, they can do some damage, just as any other executable. Being in a user-owned directory doesn't magically mean that they're safe.)

---

