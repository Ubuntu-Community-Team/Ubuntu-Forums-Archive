---
title: "dissapearing Shell variables"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by Rocafort8 on 2009-12-06
I installed the Go compiler and when I set the shell variables:
```

export GOROOT=$HOME/go
export GOARCH=386
export GOOS=linux
export GOBIN=$HOME/bin
export PATH=$PATH:$GOBIN

```And then it works fine, but when i close the console window, and then open again the shell variables have dissapeared :confused:

---

### Post by Some Penguin on 2009-12-06
Environments are on a per-shell basis.  That is, per-shell-instance -- multiple terminal windows will be running different instances of the shell and thus have different environments.

Add the 'export' commands to  your ~/.bash_profile file so that every bash invocation will use 'em.

---

### Post by falconindy on 2009-12-06
Better to put them in your .bashrc -- in my experience, .bash_profile isn't executed unless you log in through a tty.

---

### Post by Rocafort8 on 2009-12-07
It works perfectly now, thanks for helping.
So, .bashrc is a kind of script which executes everytime I open a console ?

---

### Post by falconindy on 2009-12-07
More or less, yes. To be more specific, its executed each time Bash is started by a user.

---

