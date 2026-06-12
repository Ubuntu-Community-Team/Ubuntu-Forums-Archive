---
title: "x- Executable File"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by abhaypd on 2009-01-26
hello, I am absoultely new to linux world. I installed ubuntu in dual boot mode and it works perfect. I want to run a program which show application/x-executable as extension. In windows machine identical win program is A.exe; for linux it is 'A' with no extension. How do i run this program in Linux.
The program is a code for physics calculation and is not Source Code file. Like in fortran we compile the program and get a run file. I guess it is same run file.

---

### Post by llama320 on 2009-01-26
cd into the directory where the executable is and type
```
./name_of_file
```
this should run the program. If that for some reason doesn't work try
```
sh name_of_file
```
if that still doesn't work, I think we need more info, so give us the output of
```
head -5 name_of_file
```

Good Luck

---

### Post by bruce89 on 2009-01-26
file is a useful utility to find what sort of file something is.

---

### Post by abhaypd on 2009-01-26
thanks Randy. ./ worked; on the same issue 'would you recommend me a good PDF book for linux which will cover basics. 
thanks a lot.

---

### Post by emarkd on 2009-01-26
Just to explain what was happening, as a security measure Linux makes you type the path and the filename of any program you want to execute (unless its on the system path).  The ./ simply referrs to the current working directory.

For some more good info, check out [The Linux Documentation Project]("http://tldp.org/") and [Psychocats]("http://www.psychocats.net/ubuntu/index.php").

---

