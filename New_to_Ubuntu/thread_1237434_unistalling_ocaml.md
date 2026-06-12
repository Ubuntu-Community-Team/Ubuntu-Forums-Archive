---
title: "unistalling ocaml"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by newport_j on 2009-08-11
I want to uninstall ocaml-3.11.1. I tried make unistall and got:

make: *** No rule to make target `unistall'.  Stop..

So I have no uninstall file. I just want to uninstall this version of ocaml and put in the 3.09 version which works with CCured. So how do I get this  ocaml-3.11.1 out off the computer? I want to pull it out by its roots and get all the other files etc. that were installed in other directories. I do not think just deleting the ocaml-3.11.1 directory will do it. So how do I get it off of the computer.?

When I installed CCUred it gave me a warning to go back to ocaml-3.09. The newest version of ocaml (which is what I have installed) may not work correctly with CCured. This is unusual, but I will do what they say.

newport_j

---

### Post by Simian Man on 2009-08-11
In your post, you typed 'make unistall' instead of 'make uni**n**stall'.  Is that just a typo?

If there is no uninstall target, then you may have to remove the files manually.  Hopefully the makefile installed stuff to /usr/local as that will make it much easier to find, but I've never installed ocaml from source before.

---

### Post by newport_j on 2009-08-11
yes. unistall is just a typo. 


I need to know how to generate the install rules so that I may then use make uninstall. As I said, I want to pull it out by its roots. If I just remove the ocaml 3-11 directory that will not work. I would rather do a clean uninstall that a piece by piece hunt 'n peck uninstall.

What if I installed ocaml 3-11 again? Would that make the rules that make uninstall is looking for? I do not remember how I installed it. I just know that I do not have the rules that make uninstall is looking for.

This ocaml is not in the Ubuntu repositories. they only go up to ocaml 3-10. I have ocaml 3-11.

 
newport_j

---

### Post by Simian Man on 2009-08-11
> **newport_j said:**
> 
What if I installed ocaml 3-11 again? Would that make the rules that make uninstall is looking for? I do not remember how I installed it. I just know that I do not have the rules that make uninstall is looking for.

No if there is no uninstall in the Makefile, reinstalling won't add one in.  What you need to do is find out where ocaml installed to so that you can remove it manually.  The following should give you the commands it ran to install itself:
```
make -n install
```
The -n flag means "dry run" and causes make to just print out the commands it uses for a target without actually executing them.  You should see a lot of cp commands that copy Ocaml binaries, headers and libraries to places in your filesystem.  This will tell you what files and directories you need to remove.

---

