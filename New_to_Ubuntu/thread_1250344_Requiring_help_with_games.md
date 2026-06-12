---
title: "Requiring help with games"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by Paraboo on 2009-08-26
Hello.

I've been a Mac user for basically my whole life, but recently my Mac decided to never work again.
So I got a laptop running Ubuntu from my dad. (with GNOME, I think)

Everything works great, but I can't figure out how to install anything, i.e, Tuxracer.

I have no understanding of the terminal at all, save for cd and ls.
Could anyone please help in simple english?

Thanks!

---

### Post by philcamlin on 2009-08-26
Hi,

To extract and unzip a tar.gz or tgz file do this:

# tar -xzvf your-software.tar.gz

This will likely create a directory named something similar to the name of the tarball hanging directly from the directory you are located right now.

Then, cd into that directory and look for the configure script.

*** how to cd 

cd means 'change directory'

so you'll do something like..

cd '/home/user/folder'
(but without the ' marks and the directory you are actually looking for)

that will get you to the directory, just like clicking through folders in a gui.

---

### Post by achase79 on 2009-08-26
just open add/remove or synaptic from the menu and use them to find, download, and install the software for you.

---

### Post by philcamlin on 2009-08-26
> **achase79 said:**
> just open add/remove or synaptic from the menu and use them to find, download, and install the software for you.
the op says he wants tux racer** its not** in synaptic only extreme tux racer is there

---

### Post by Mark Phelps on 2009-08-26
Installing anything in Ubuntu is done using one of the following approaches -- in increasing level of difficulty:

1) Add/remove applications. Select what you want and it's installed.

2) Synaptic.  Select the package you want, it's downloaded, along with any dependencies, click apply, and it's installed.  This tool retrieves packages from repositories -- known as repos.

3) Locate the specific package (.deb file): Can install the package but you have to track down and resolve dependencies and conflicts yourself.

3) Download the source and build the executable yourself:  Lots of work, lots of time, lots of difficulties -- but sometimes the only alternative if the latest version has not yet been packaged or is not in the repos.

So ... would recommend using this sequence to locate the Unix games you want.  The higher up the list they are, the easier they will be to install.

---

### Post by pedro3005 on 2009-08-26
> To extract and unzip a tar.gz or tgz file do this:

# tar -xzvf your-software.tar.gz

This will likely create a directory named something similar to the name of the tarball hanging directly from the directory you are located right now.

Then, cd into that directory and look for the configure script.

*** how to cd 

cd means 'change directory'

so you'll do something like..

cd '/home/user/folder'
(but without the ' marks and the directory you are actually looking for)

that will get you to the directory, just like clicking through folders in a gui.

Or maybe you double click, then click extract. Then you double click the directory created. See, I like the terminal also, but this is an exaggeration, using a bunch of commands to do a 3 clicks task. This is the kind of thing that drags some people away from linux.

---

### Post by Paraboo on 2009-08-26
Thank you!

Now that I know, I'm looking more fondly on Ubuntu.

---

