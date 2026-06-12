---
title: "Graphical Alias?"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by Tidus0515 on 2010-04-08
Ok...I was able to edit the .bashrc file to essentially return "program doesn't exist yada whatever" if through terminal I try to executre my encryption program cryptkeeper. However, when I run cryptkeeper through alt f2...it runs fine. I want to alias it to something else because I do not want somebody who knows of the cryptkeeper program to be able to run it and see that i have it. I have made a sym link to the program so I can run it under a different command...but I cannot seem to get the graphical interface to return an error when running the command "cryptkeeper"....

This is the end of my .bashrc file...

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
alias cryptkeeper='echo "The program Cryptkeeper is currently not installed. You can install it by typing: sudo apt-get install cryptkeeper"'

Is there another file I can edit so the graphical launching of the cryptkeeper program will also return a problem?

---

