---
title: "&quot;applications&quot; equivalent"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by Erom on 2009-02-24
Hey all. I just downloaded a program I need that wasn't in the package repositories, got it built with make, no problems there. But now it's sitting on my desktop - is there some convention for where programs get placed on linux? This one happens to be a command line utility, so I guess making it so I don't have to navigate to it's directory to use it would be best, but I'm also curious what I would do with a gui program to get it into the ubuntu "applications" menu.

Thanks!

---

### Post by taurus on 2009-02-24
If you want to install the program to your system, then you have to run the **sudo make install** from a terminal, after you have successfully ran **./configure && make**.  That will most likely install the binary to /usr/local/bin and the libraries to /usr/local/lib.  Then, you can just run it anywhere you want by typing in the name of the program since /usr/local/bin should be on your path.

---

### Post by Erom on 2009-02-24
Hm. I get "configure: command not found" when I try to do that step. Running make just works even without doing configure, do I need to run configure first?

Edit: Thanks for the help. I had to look up the whole configure-make-make install chain. I didn't realize how common it was, I've never used it before (and I've been coding for 7 years! Java though, so that's why).

---

### Post by taurus on 2009-02-24
Not all sources require you to run ./configure first.  However, there should be a readme.txt (Readme.txt/README.txt) or INSTALL telling you what you need to do to build and install it.  If it says run make && make install to compile and install it, then you just have to run

```
make
sudo make install
```

---

### Post by Erom on 2009-02-24
Well, sudo make install returns "make: *** No rule to make target 'install'. Stop." and a look through the readme has build instructions but no install instructions. Looks like the install instructions were never written. I guess I'm going to look into doing it manually (near as I can tell, it's just one binary, so I'm going to drop it into /usr/local/bin and see what happens).

Thanks again for all your help.

---

### Post by taurus on 2009-02-24
Try running it (from a terminal) from where it is right now and see if it runs.

What are you trying to install anyway?

---

### Post by Erom on 2009-02-24
Yeah, it does run from where it is now. It's a little app that copies HEX files to and from microchip PIC's that have the appropriate USB bootloaders on them. It's pretty down in the weeds, so I'm not concerned about it lacking an install script - the critical piece of information you've given me is the existence of /usr/local/bin. It makes sense to me now that bin = binary, my first interpretation was literally a "bin", like a place to hold stuff, so I assumed it was a folder for temporary files or something, hah.

---

