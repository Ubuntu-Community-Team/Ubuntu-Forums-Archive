---
title: "Setting A Class Path In Ubuntu"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by sylar petrelli on 2010-11-26
Hello everyone,

My question is quick.  I need to set the PATH variable to /usr/games and keep all the other fields in the PATH variable.  How would I do that in Ubuntu>  Most other posts I have seen are for Java.


Thanks In Advance,
SP

---

### Post by d3v1150m471c on 2010-11-26
you mean something like this?
```

GAMES='/usr/games'

echo $GAMES

```You can add the first line of that code to your ~/.bashrc file to make it system wide.
reboot or:
```

. ~/.bashrc

```

---

### Post by marnixava on 2010-11-26
I'm not sure why you call it setting a "Class Path".  I think you just want to add a path (/usr/games) to your "PATH" environmental variable.  So nothing to do with "Class".  To do what I think you want, read on.

At the end of your ".bashrc" file, put:

  PATH="/usr/games:$PATH"

You could do this by typing the following command in a terminal window:

  echo 'PATH="/usr/games:$PATH"' >> $HOME/.bashrc

If that doesn't work for some reason, you can try appending that line to one or both files, "/etc/bashrc" and/or "/etc/profile" .

---
Marnix


> **sylar petrelli said:**
> Hello everyone,

My question is quick.  I need to set the PATH variable to /usr/games and keep all the other fields in the PATH variable.  How would I do that in Ubuntu>  Most other posts I have seen are for Java.


Thanks In Advance,
SP

---

### Post by sylar petrelli on 2010-11-26
Thank you that really helped.  I was originally trying to launch my games from the application menu under games and I kept getting "Failed to execute child process "whatevergame" (No such file or directory)". I tried to launch it from the terminal and it said the PATH variable needed to be set.  I have gotten them to run from the bash shell, but I still can get my games to run from the menu bar.

---

