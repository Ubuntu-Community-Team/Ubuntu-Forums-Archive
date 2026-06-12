---
title: "[SOLVED] Variables not exporting"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by kaspar_silas on 2008-12-17
Okay simple question, not sure if this counts as absolute beginner or not. Feel free to move it if you think not.

I have a file, lets say called STARTUP, full of declarations of environmental variables that I need to set up to run a program. It's pretty much just a text file with stuff like: 

```


export WORKSTUFF1=~/workdir/station1 
export WORKSTUFF2=~/workdir/desktop31 
export STARTLOCATION=~/software/identifer 
export TEMPBINN=~/software/identifer/binn
echo "ALL VARIABLES SET"
```

now I can just open a terminal and type these in and it works. However if I run the STARTUP file I get the message ALL VARIABLES SET but they aren't. None are set, so does anyone know why. 

Thanks for any help or suggestions.

---

### Post by ByteJuggler on 2008-12-17
Run the script using the "source" command (which can be abbreviated to "." if I remember correctly.)  This ensures the commands are run in the current shell, instead of a new shell (where the changes are  local to that shell and lost when it terminates.)

E.g. either

```

source STARTUP

```

or 

```

. STARTUP

```

Note/Aside:  Your shell (by default the "bash" shell) already has a startup file called ".profile" (or sometimes the bash specific one ".bash_profile" which bash will read in preference to ".profile" if present), which gets run whenever you log in with an interactive shell (and one called ".bashrc" which gets run for non-interactive shells.)  Anything you put in there will therefore be run "on startup" of the shell. ou'll notice when you look, that the ".profile" script typically contains code to run the ".bashrc" as well, if present, using the method explained above.

---

### Post by kaspar_silas on 2008-12-17
Cheers, exactly what I was looking for. 

I knew about the .profile/.bashrc way but I was looking a neater way.

---

