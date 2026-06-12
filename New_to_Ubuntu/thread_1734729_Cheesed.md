---
title: "Cheesed"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by doppel.ganger on 2011-04-20
I recently downloaded the Cheese 3.0.0 tarball from their official website. How on earth do I compile a tar.gz file? I already extracted it and it is in 'Downloads' in 'cheese-3.0.0'
Tarballs have angered me for a long time. Help Please!:confused:

---

### Post by TeoBigusGeekus on 2011-04-20
[https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

---

### Post by doppel.ganger on 2011-04-20
That didn't help.

---

### Post by nickleboyblue on 2011-04-20
The how-to above should have worked.  Did you try what it suggested?  How far did you get, and when did you run into a problem?

For tar files, the first step is to extract, and the how-to above has those commands listed in it.  The second step is to move into the new file created by extracting the tarball, and again, the how-to above covers this.  If there are dependencies, you need to find them and install them before installing your program.  Once you have that done, you simply run make, then sudo checkinstall, and it should install without problems unless the programming is faulty.

If this process didn't work for you, please let us know where it went wrong and we'll be glad to try and find out what's wrong.

Other information that might be important is your version of ubuntu, what commands you did try, which directory you were in when you tried them, and anything else that you did while trying to install the program.  There is also a chance that the program is installed, but isn't in the menus, and you'll have to manually put a menu item in the menus in order for you to access the program without having to run a terminal.

---

### Post by yeats on 2011-04-20
Assuming you know this, but cheese is available in the repositories:

```
sudo apt-get install cheese
```

from a terminal.

Unless there's a particular reason you're installing from source, I would advise just going with the repo version.

---

### Post by doppel.ganger on 2011-04-20
I want cheese 3.0, not in software center.
Can I add 3.0 to the software center?

---

### Post by yeats on 2011-04-20
> **doppel.ganger said:**
> I want cheese 3.0

Well if you're wanting to be on the bleeding edge, you'll definitely want to get comfortable installing from source.  

One step you might want to take that might make things easier is to 

```
sudo apt-get build-dep cheese
```

which should pull in the dependencies for the cheese package (as packaged by Ubuntu - there may be newer dependencies, which you will discover with the ./configure step).

You might do better with the "not easy" compiling how-to which is more universal (not just limited to Ubuntu/Debian):

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by doppel.ganger on 2011-04-20
Didn't help. Specs still say 2.??? in center

---

### Post by deconstrained on 2011-04-20
> **doppel.ganger said:**
> How on earth do I compile a tar.gz file? I already extracted it and it is in 'Downloads' in 'cheese-3.0.0'
Tarballs have angered me for a long time. Help Please!:confused:
As you've probably guessed by now, **you don't compile a .tar.gz file.** A .tar.gz (a.k.a. "tarball") is like a .zip; it's a compressed archive.

Open up a terminal, change directory into the extracted folder with the source code in it and run ./configure and make (there should be a README file in there, so have a look at that to get an idea of what will be required).

Also, this:
> **yeats said:**
> ```
sudo apt-get build-dep cheese
```

---

