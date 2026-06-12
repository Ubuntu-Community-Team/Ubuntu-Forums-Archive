---
title: "Where is .bash_profile ?"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by le_phoceen on 2011-02-06
Hi,

I've just installed ubuntu and I would like to create and set some environment variable permanently. Usually I think there is a .bash_profile file in the home directory but I don't find it. Even when I create one and make an export MY_VARIABLE=$HOME/my/directory and reboot it seems not to work.

Has someone an idea ?

---

### Post by AlphaLexman on 2011-02-06
> **le_phoceen said:**
> I think there is a .bash_profile file in the home directory but I don't find it. Even when I create one and make an export MY_VARIABLE=$HOME/my/directory and reboot it seems not to work.
Yes it should be in $HOME a file with a dot [.] in front of the filename denotes a 'hidden' file you can see hidden file in Nautilus by hitting 'Ctrl-h' or on the command line with```
ls -a
```The following code should confirm your .bash_profile exists and contains the information you want:```
cat ~/.bash_profile
```
EDIT: removed bad code

---

### Post by le_phoceen on 2011-02-06
Thank you AlphaLexman, there was not the file but I created it. In it I put ```
export JAVA_HOME=$HOME/lib/jdk1.6.0_23
```, and I logged out and in but then when I type echo $JAVA_HOME I get a blank line, I wonder if the .bash_profile file is not taken into account at the start-up or if it is my export syntax that is incorrect ?

Thank you very much for your help, I'm beginner to Ubuntu and trying to learn here and there :)

---

### Post by ianc1 on 2011-02-06
Is it .bash_profile you want or .bashrc.  I thought the profile was .bashrc but a quick google resulted in [http://www.joshstaiger.org/archives/2005/07/bash_profile_vs.html](http://www.joshstaiger.org/archives/2005/07/bash_profile_vs.html) which shows both exist.  But if you want to modify how the shell appears after your logged in I think its .bashrc you want.

---

### Post by AlphaLexman on 2011-02-06
I don't think my previous post 'edit' will work because of the single quotes, sorry, just put double quotes around the variable like this:```
export JAVA_HOME="$HOME/lib/jdk1.6.0_23"
``` and give it another try... you can just source ~/.bash_profile like this```
. ~/.bash_profile
```without having to logout and login.

---

### Post by asmoore82 on 2011-02-06
".bash_profile" is only read by true *login* shells.
Modern desktop environments never run bash as a login shell.

The solution is to put your customizations in ".bashrc" instead.

The catch to this is, ".bashrc" is *not* read by true login shells.
So, it is also good practice to "hook" your .bashrc in to the end of your
.bash_profile - in case of a login shell, like an SSH session, for example.

On a side note, you should be generous with the quotations.
Just for fun, some safety logic couldn't hurt either.
Your .bashrc should be like:
```
#.bashrc

#...

JAVA_HOME="$HOME/lib/jdk1.6.0_23"
if [ -d "$JAVA_HOME" ]
then
    export JAVA_HOME
fi
```
And your .bash_profile:
```
#.bash_profile

#...

if [ -f "$HOME/.bashrc" ]
then
    source "$HOME/.bashrc"
fi
```

---

### Post by le_phoceen on 2011-02-06
Indeed it works well now with .bashrc ! And I begin to understand the difference between these .bash_profile and .bashrc files.

Thank you all :)

---

