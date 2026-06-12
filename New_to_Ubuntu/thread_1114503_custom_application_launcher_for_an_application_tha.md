---
title: "custom application launcher for an application that runs in the terminal?"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by karasuman on 2009-04-02
I have a sort of annoying thing I have to type to run HOL Light (below), and I'd like to create an application launcher for it.  I made a script with the following lines of code, set it to be executable, and pointed the launcher to the script.  When I click on it, nothing happens.  Is this because the ocaml top level runs in the terminal?  Is there a way to get it to launch the terminal?

```
cd ~/Desktop/shell/HOL/hol_light/
ocamlmktop -o ocamlnum nums.cma
./ocamlnum
```

At this point I'm in the ocaml top level, and I need to type

```
#use "hol.ml";;
```

---

### Post by cariboo on 2009-04-02
Can you create a script to do what you need and then create a Launcher to run in a terminal. See screenshot.

Jim

---

### Post by karasuman on 2009-04-02
Ha, yes, it was the "application in terminal" setting that I missed.  Thanks!

---

