---
title: "how to compile a program?"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by zzzonked on 2009-06-18
I have no knowledge on programming whatsoever. Recently I downloaded a program that required me to compile it before I use it. The zip file I downloaded contained a text file named "makefile" and a whole lot of other xxx.c and xxx.h files.

So how do I compile this? (I have no idea what compiling means, it just says so in the how-to.)

---

### Post by nothingspecial on 2009-06-18
What is the program

Is there a README file?

What does it say?

You will probably need the build-essential package.

Are you sure it is not available in the repos or failing that, is a .deb available anywhere?

---

### Post by zzzonked on 2009-06-18
As I've mentioned, there's only a textfile called "makefile" and a whole bunch of .c and .h files. No readme. No .deb.

It's a cubesolver program if that interests you.

I've searched some other tutorials on Google, but there's no file called configure in the folder, so ./configure won't work. When I tried typing make in terminal, I got an error message.

---

### Post by Mornedhel on 2009-06-18
Could you post the contents of the error message ?

---

### Post by nothingspecial on 2009-06-18
The reason I asked what program it is, is so that I could have a look at it myself and see if I could figure out what you needed to do.

As you have already read it`s usually just a matter of installing dependencies and

./configure
make
sudo make install

but not always.

Maybe you just need to make and sudo make install. There must be some installation documentation somewhere.

---

### Post by Trebaruna on 2009-06-18
Actually I would recommend against "sudo make install" because there is no easy way to uninstall.

Instead, run "sudo checkinstall make install". This makes a Debian package out of the code and installs it. Uninstalling works like any other software package. (in Synaptic it's easiest: if you sort by status it will be under "Installed (local or obsolete)"
You need to have the package checkinstall installed. It's in the repositories.

---

### Post by nothingspecial on 2009-06-18
> **Trebaruna said:**
> Actually I would recommend against "sudo make install" because there is no easy way to uninstall.

Instead, run "sudo checkinstall make install". This makes a Debian package out of the code and installs it. Uninstalling works like any other software package. (in Synaptic it's easiest: if you sort by status it will be under "Installed (local or obsolete)"
You need to have the package checkinstall installed. It's in the repositories.


Sound advice. See [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/CheckInstall") for details

---

### Post by falkTX on 2009-06-18
I usually just try first './configure'; if it says the file doesn't exist I do 'make'.
If make says "can be done anything for all" I skip to 'make install'.

Just try it

---

### Post by zzzonked on 2009-06-18
Got this error message after typing make:

g++ -o fill_rotate.o -c fill_rotate.c -Wall -ansi -O3 -march=pentium-m
make: g++: Command not found
make: *** [fill_rotate.o] Error 127

---

### Post by nothingspecial on 2009-06-18
Do you have the build-essential package installed.

```
sudo apt-get install build-essential
```

It is necessary for compiling.

---

### Post by tarps87 on 2009-06-18
> **zzzonked said:**
> Got this error message after typing make:

g++ -o fill_rotate.o -c fill_rotate.c -Wall -ansi -O3 -march=pentium-m
make: g++: Command not found
make: *** [fill_rotate.o] Error 127

In that case you need to install the g++ compiler which is part of the build-essential package stated above
```
sudo apt-get install build-essential
```

Edit: Never mind nothingspecial got the first

---

### Post by FourthCoffee on 2009-06-18
Hi,
Im trying to install realtek audio drivers because my sound is really **** and im having some problems.
The file is in tar.bz2 format
I've done dozens of Google searches to find out how to install it and they've all said to use tar zxf or something along thoses lines. And that dosent work so i try to change directory by using cd /desktop or cd /downloads and many other variations but i just cant change directories for some strange reason.

Can someone help

---

### Post by LewRockwell on 2009-06-18
Here is a fairly current article/tutorial:

[http://www.justlinux.com/nhf/Software/Compiling_Software.html](http://www.justlinux.com/nhf/Software/Compiling_Software.html)

and I'd also like to point out that there is a vast amount of *nix resources/guides/tutorials strung out across the interwebs so if you find one that doesn't work for you...there will usually be several others as well

obviously: [http://www.justlinux.com/](http://www.justlinux.com/)

and a few other examples include:

[http://www.desktoplinux.com/](http://www.desktoplinux.com/)

[http://www.linuxdevices.com/](http://www.linuxdevices.com/)

[http://www.linuxinsider.com/](http://www.linuxinsider.com/)

[http://www.linuxjournal.com/](http://www.linuxjournal.com/)

[http://www.lxer.com/](http://www.lxer.com/)

and then there are websites like Sara's: [http://sarah.thesharps.us/](http://sarah.thesharps.us/)

and psychocats: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by zzzonked on 2009-06-18
Thanks everyone. The build-essential download worked :)

---

### Post by tarps87 on 2009-06-18
> **FourthCoffee said:**
> Hi,
Im trying to install realtek audio drivers because my sound is really **** and im having some problems.
The file is in tar.bz2 format
I've done dozens of Google searches to find out how to install it and they've all said to use tar zxf or something along thoses lines. And that dosent work so i try to change directory by using cd /desktop or cd /downloads and many other variations but i just cant change directories for some strange reason.

Can someone help

Try form you home dir:

cd Desktop
or
cd Downloads

or from anywhere:

cd ~/Desktop
or
cd ~/Downloads

Remember Unix is case sensitive

I recommend that you start a new thread with a descriptive title when asking a question, it will make it easier for people answering posts and you will probably get help quicker

---

### Post by oldos2er on 2009-06-18
"Actually I would recommend against "sudo make install" because there is no easy way to uninstall."

 I've never had any problem with "sudo make uninstall".

---

### Post by oldos2er on 2009-06-18
> **FourthCoffee said:**
>  im having some problems.
The file is in tar.bz2 format


 I see you've gotten some suggestions; I'll add a couple. First, install the package nautilus-open-terminal (**sudo apt-get install nautilus-open-terminal**), then logout and log back in to activate it. Right-click on the tar.bz2 file, click 'Extract here'. Double-click on the new folder, right-click on an empty spot and choose 'Open terminal here'. Now you're in the correct folder to run ./configure, make, sudo make install.

 Also see [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by SteveNorman on 2009-06-18
just so you know, compiling is translation of the program into language that means something to the computer. ie 1's and 0's. When a program is written it is written in a language that (some)humans can understand, and must be converted into  "machine" language.

Some programs will be precompiled, some will be packaged in .tar.bz, .tar.gz., .zip, some will need to be ran as a script, and some will need to be compiled. Its on a case by case scenario. You are safer sticking to apt-get, aptitude, and synaptic till you know how to trust your sources.

---

### Post by Mornedhel on 2009-06-18
> **oldos2er said:**
> "Actually I would recommend against "sudo make install" because there is no easy way to uninstall."

 I've never had any problem with "sudo make uninstall".

You got lucky.

---

### Post by achase79 on 2009-06-18
to easily change directories just type "cd " then drag & drop the directory you want to change to into the terminal.  It will automatically put in the correct path.

---

### Post by nothingspecial on 2009-06-18
> **achase79 said:**
> to easily change directories just type "cd " then drag & drop the directory you want to change to into the terminal.  It will automatically put in the correct path.

Wow, I didn`t know that!

Not much use to a keyboard kind of guy but cool never the less.

---

### Post by SteveNorman on 2009-06-19
> **achase79 said:**
> to easily change directories just type "cd " then drag & drop the directory you want to change to into the terminal.  It will automatically put in the correct path.


so its almost windows! weeeeeeeeeeeeeeeeeeee

---

### Post by tarps87 on 2009-06-19
> **achase79 said:**
> to easily change directories just type "cd " then drag & drop the directory you want to change to into the terminal.  It will automatically put in the correct path.

You learn something new every day, although I prefer tab complete, especially on my server

---

### Post by 3rdalbum on 2009-06-19
> **nothingspecial said:**
> Wow, I didn`t know that!

Not much use to a keyboard kind of guy but cool never the less.

It's amazing how many people don't know that you can do that. Current and former Windows users don't tend to think about using drag 'n' drop.

---

