---
title: "I have no idea how to compile source code."
date: 2009-04-26
forum: New to Ubuntu
---

### Post by odysseus1138 on 2009-04-26
I am new to Linux in any form. One thing I find that needs to be done is compiling source code. There are many applications that I have the source code for, but I don't know what to do with it.

Could somebody please help?

---

### Post by cariboo on 2009-04-26
There should be no reason why a new user has to compile a program from source. The program you need is more than likely in the repositories.

Go to System-->Abministration-->Synaptic Package Manager and click the search button to search for the package you need.

---

### Post by steve101101 on 2009-04-26
+1 also if you need to compile source code. I rarely have to do this if at all, you can find many articles already on this by searching google or these forums.

---

### Post by kellemes on 2009-04-26
And if you happen to need stuff not available in some repository you'll find all the info about compiling in the standard docs.
[https://help.ubuntu.com/community/CompilingSoftware]("https://help.ubuntu.com/community/CompilingSoftware")
[https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

---

### Post by wsonar on 2009-04-26
If you just want to  know how most of the apps should have a read me file in them 

that will usually have some make instructions
usually goes something like

./configure

make

make install

depending on what your installing and you may need appropriate permissions or sudo

you usually have to have the appropriate dependencies

that why other methods that get the dependencies for you are recommended

---

### Post by jimreynold2nd on 2009-04-26
In case you still want to compile something from source (for the fun of it, duh), you generally have to a) extract the tarball to somewhere, b) read the INSTALL or README file comes with the source c) either follow the README or INSTALL instruction or do a configure-make-make install.

for a) **tar -zxvf your-tar-gz-file.tar.gz** or **tar -jxvf you-tar-bz-file.tar.bz2**
for b) **vi README** or **vi INSTALL**. Exit **vi** by typing **:q!**<enter>
for c) If you did not read the README and INSTALL, or they don't have any useful information, then do **./configure**, then **make**, then **sudo make install**.
done. tada. was fun, wasn't it?

---

### Post by oldos2er on 2009-04-26
> **odysseus1138 said:**
> There are many applications that I have the source code for, but I don't know what to do with it.
  

 Which applications?

---

