---
title: "Sequewnce of gcc install commands"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by newport_j on 2009-09-08
What is the sequence of gcc install commands after untaring and moving to the gcc directory?

I have tired :

./configure  --prefix=/usr/local/gcc2


now that give no problem since this is a basic command. The --prefix=/usr/local/gcc2 option simply puts the earlier version of gcc at this location instead of over the most current version of gcc.

The second command is:

make bootstrap

this creates a very long compile sequence with no errors.

The final command is what:

make or

make install or 

something else.

I do not know.

---

### Post by Hospadar on 2009-09-08
Why not install it from the repositories?

sudo apt-get install build-essential will get all basic build tools (make, gcc, g++, etc)

---

### Post by newport_j on 2009-09-08
That is a good question. I am trying to install an earlier version of gcc. That would be gcc-3.3.5. This is not in the repositories. I must install and compile it myself.

I have used

./configure   --prefix=/usr/local/gcc2

make bootstrap
newport_j
make install


All from the super user mode. It works. It installs gcc-4.2.4 where I want gcc-3.3.5. A perfect installation of the wrong software. I already have gcc-4.2.4. installed; I want gcc-3.3.5 installed in /usr/local/gcc2. Why does it not do this?

I get at that /usr/local gcc-4.2.4  instead?

Respectfully,

newport_j

---

