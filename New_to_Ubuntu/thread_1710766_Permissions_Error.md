---
title: "Permissions Error"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by sc298 on 2011-03-20
Hello!

I am having some trouble compiling a solver in OpenFOAM.
I'm trying to run wmake on the simpleWindFoam directory but am getting a permissions error.

Does anyone know how to get around this?

Thank you!



```
psypherdelic@Mooface:/opt/openfoam171/tutorials/incompressible/simpleWindFoam/simpleWindFoam$ wmake
mkdir: cannot create directory `linux64GccDPOpt': Permission denied
/bin/sh: cannot create linux64GccDPOpt/options: Directory nonexistent
make: *** [linux64GccDPOpt/options] Error 2
/opt/openfoam171/wmake/MakefileFiles:39: linux64GccDPOpt/options: No such file or directory
make: *** No rule to make target `linux64GccDPOpt/options'. Stop.
wmake error: file 'Make/linux64GccDPOpt/objectFiles' could not be created
```

---

### Post by kn0w-b1nary on 2011-03-20
prefix your command with: "sudo"

this would run your command as root, who has write permissions to that directory.

---

### Post by sc298 on 2011-03-20
The command:

```
sudo wmake
```

produces:

```
sudo: wmake: command not found
```

---

### Post by kn0w-b1nary on 2011-03-20
can you try:```
sudo bash
```
this will put you as root, then run wmake.

---

### Post by sc298 on 2011-03-20
brilliant, thank you!

---

### Post by kn0w-b1nary on 2011-03-20
You're welcome!

---

### Post by hakermania on 2011-03-20
Also, sudo /full/path/to/wmake I think it would work

---

### Post by DadsArmy on 2011-03-24
I have exactly this problem, and relatively little experience with Linux. Naïvely trying wmake gives:

```
mkdir: cannot create directory `linux64GccDPOpt': Permission denied
etc...
```

When I try the sudo bash method, wmake cannot be found anymore, I get the following message:

```
No command 'wmake' found, did you mean:
 Command 'tmake' from package 'tmake' (universe)
 Command 'wmaker' from package 'wmaker' (universe)
 Command 'jmake' from package 'dist' (universe)
 etc, etc...

```
Using sudo /full/path/to/wmake produces the error:

```
wmake error: environment variable $WM_OPTIONS not set
```

Any suggestions are very welcome.

Best regards,
Jelle

---

### Post by ltholmes on 2011-10-26
Big help, thank you as well!
-LTH

---

