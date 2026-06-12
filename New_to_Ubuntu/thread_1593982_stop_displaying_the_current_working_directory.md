---
title: "stop displaying the current working directory?"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by bronquel on 2010-10-11
I'm working in a directory that has a number of parent directories, and this is cluttering up my command line.
here is an example:
bronquel@bronquel-laptop:~/Dropbox/alg exp2/Exploration 2 Algorithm Efficiency/perl sorts$

how can i stop displaying the current working directory?  

something like this is what i want:
bronquel$
or 
bronquel-laptop$

I've tried googling this, but my google-foo is failing me today (i keeping getting information about 'pwd')

thanks!

---

### Post by bronquel on 2010-10-11
[http://www.computing.net/answers/unix/how-to-set-my-prompt-to-display-current-directory/1106.html](http://www.computing.net/answers/unix/how-to-set-my-prompt-to-display-current-directory/1106.html)  was the answer.

to set only the computer name to be displayed:
PS1="`uname -n`\$ "
to set only your user name to be displayed:
PS1="$LOGNAME\$ "

---

### Post by CharlesA on 2010-10-11
You have to change the PS1 prompt in .bash-rc.

Check [here]("http://ubuntuforums.org/showthread.php?t=614743").

---

### Post by bronquel on 2010-10-11
how do i mark that this is solved?

---

### Post by CharlesA on 2010-10-11
It's under thread tools. :)

---

### Post by bronquel on 2010-10-11
Thanks mate!

---

