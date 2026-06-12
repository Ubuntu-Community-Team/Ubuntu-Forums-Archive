---
title: "How to make terminal commands and installing scripts"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by I[AM]SMRT on 2009-01-25
I've got a script here:

[http://www.ugrad.physics.mcgill.ca/wiki/index.php/Gnuview#Log](http://www.ugrad.physics.mcgill.ca/wiki/index.php/Gnuview#Log)

That someone helped me "install" but I'd like to know how to "install" it myself.

Now, when I type "gnuview" in the terminal, it works, displaying gnu files as graphs. However, the other commands (e.g. gnueps) don't work in the terminal. Someone said it has something to do with symlinks but I'm not sure how to make one and what to make it with.

Cheers,
SMRT

---

### Post by jamesrl on 2009-01-25
Looking at the script quickly, it seems that to make it run correctly you need to go into the directory it is in, and type:
```

[S]ln -s gnuprint gnuview 
ln -s gnuprintp gnuview[/S]
ln -s gnuview gnuprint
ln -s gnuview gnuprintp 


```
etc. for all the commands you want to use.  This is assuming you saved the script as gnuview.

---

### Post by I[AM]SMRT on 2009-01-25
> **jamesrl said:**
> Looking at the script quickly, it seems that to make it run correctly you need to go into the directory it is in, and type:
```

ln -s gnuprint gnuview 
ln -s gnuprintp gnuview

```
etc. for all the commands you want to use.  This is assuming you saved the script as gnuview.
EDIT: Wow, I'm an idiot. This is what I get using the right command:

```
root@brian-laptop:/usr/local/bin# ln -s gnueps gnuview
ln: creating symbolic link `gnuview': File exists
```

However, when I try to gnueps, it still doesn't work.

---

### Post by jamesrl on 2009-01-25
I should add that I am not sure what your friend did to install it, as there are several ways to 'install' a script.
1). Just put it in a text file called script.sh, and every time you want to run it, type:
bash script.sh
2). Put it in a text file called script.sh, and then type 
chmod 755 script.sh 
(to give everyone execute privileges of the script).  Then when you want to execute all you have to do is type
./script.sh 
from the directory the script is in.
3).  Put the script in some directory that is already part of your path.  If you type 
echo $PATH 
you can see the list of your path.  Make sure the script is executable (chmod 755 script.sh).  Then to run it from anywhere, you can now just type
script.sh
and don't have to worry about being in the right directory.

4). If you don't have sudo/root privileges, you can edit your .bashrc and add a line like 
export PATH=$PATH:$HOME/local/bin 
(anywhere within .bashrc)
and then type
mkdir ~/local
mkdir ~/local/bin
and put the script in the directory ~/local/bin (and give it executable permissions.


Note, the .sh part of the file name is entirely optional, so you could have put it in a file just called script.

---

### Post by jamesrl on 2009-01-25
Oops sorry.  I typed it backwards
its supposed to be 
ln -s gnuview gnueps
(makes more sense as you can always do things like 
ln -s /some/link/to/another/place
and then in your current directory you have a link to place.  [So you specify where you want to link first, and then have the name.  The -s is for its a symbolic link rather than hard link.]
  Its a link to gnuview called gnueps

---

### Post by I[AM]SMRT on 2009-01-25
Yea, I read the ln man file and figured that out. It doesn't really seem to be working though:

```
brian@brian-laptop:~/Desktop$ gnueps DAC1.gnu DAC1.eps
Usage: /usr/local/bin/gnueps script
```

And it doesn't do what it's supposed to (make a .eps file from the .gnu file).

> 3). Put the script in some directory that is already part of your path. If you type
echo $PATH
you can see the list of your path. Make sure the script is executable (chmod 755 script.sh). Then to run it from anywhere, you can now just type
script.sh
and don't have to worry about being in the right directory.
It seems like he did this because I can run the script from any directory. I don't know what you mean by my "path" though.

EDIT: I'm an idiot again, messed up the syntax of the command, it works great, thanks!

---

### Post by jamesrl on 2009-01-25
Normally when you try to run an executable you have to be in the same directory as the executable.  Your path is a list of directories that bash looks in to search for executables (even when you aren't in that directory).  Therefore you can type things like rm rather than /usr/bin/rm everytime you need to delete a file.

---

