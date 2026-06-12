---
title: "Uninstalling from source"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by TripleD on 2011-08-02
Howdy!

Is there an easy way to remove a program that you compiled from source? I used apt-get to install steel banks common lisp on my machine, but was told I needed to add a configuration file to the source folder so I removed the program (again using apt-get). So I downloaded the source code, added my file, ran "sudo sh make.sh", only to find that the file I was told to add was for an older version of sbcl.

I'd like to go back to the apt-get version of sbcl, but I don't know how to remove the version I have now. Any advice would be much appreciated.

---

### Post by Furball588 on 2011-08-02
Did install.sh ever run?  

If so, then if the docs are correct everything should be in /usr/local

If it didn't run, then just remove the source directory you downloaded.

---

### Post by EkuquoL on 2011-08-02
You shouldn't have to insert manual install commands using the modified get program aka apt-get . 

apt-get automatically does clean install and installs all needed files and removes temporary files. Too uninsiatall that file you installed I believe the command would be 

# apt-get uninstall <file/program-name>

---

### Post by Furball588 on 2011-08-02
> **EkuquoL said:**
> apt-get automatically does clean install and installs all needed files and removes temporary files. Too uninsiatall that file you installed I believe the command would be 

That may be true for the sources he downloaded through apt, but not for the binaries he may have manually built.  

Think of it like this.  apt-get kernel-source does not compile and install a new kernel for me :)

---

### Post by jtarin on 2011-08-02
Simply put......if it's not ".deb".....it's a manual uninstall.

---

### Post by EkuquoL on 2011-08-02
Then manually uninstall it.

---

### Post by Furball588 on 2011-08-02
If it was only that easy...

---

### Post by EkuquoL on 2011-08-02
I imagine he did not use make uninstall when installing it.

Well... Go into the folders as root and delete it. Manually.

---

### Post by jtarin on 2011-08-02
> **Furball588 said:**
> If it was only that easy...No one said it was but if your going to install software that is not packaged for your system you should know how to uninstall it before. Most resources will include configuration files that will tell you where they place things. You can always search for any left-overs.

---

### Post by TripleD on 2011-08-02
> **EkuquoL said:**
> I imagine he did not use make uninstall when installing it.

Well... Go into the folders as root and delete it. Manually.

Done and done.

I was afraid to do a manual uninstall because of my inexperience with the linux file system, thus hoping there was some uninstall command or flag I was ignorant of. But after reading up  I removed all the sbcl files from /usr/local/lib and /usr/local/bin, re-installed via apt-get, and everything seems to be running fine.

Thanks for all the replies (this is by far the fastest forum I've ever been on)

---

### Post by bodhi.zazen on 2011-08-02
> **Furball588 said:**
> If it was only that easy...

That is what you get for installing something outside of your package manager :p

sort of depends on what and how you installed it. Read the README, sometimes that file will give you directions. look at the files, is there an uninstall.sh or other uninstall script ?

You can always try```
sudo make uninstall
```

If that fails, you have to find and manually delete all the files. Sometimes it is easier to look at the source code and identify the files, sometimes it is easier to use find or other tools sometimes it is easier to simply run make install again and watch what it puts where.

If the package you are trying to install is in the Ubuntu repositories or a ppa, use that.

If the package is not in the repos or a ppa, you will have to contact the project mailing list or bug report.

---

### Post by Furball588 on 2011-08-02
> **jtarin said:**
> No one said it was but if your going to install software that is not packaged for your system you should know how to uninstall it before. Most resources will include configuration files that will tell you where they place things. You can always search for any left-overs.

> **bodhi.zazen said:**
> That is what you get for installing something outside of your package manager :razz:

Perhaps both of these comments would be better meant for the original poster...:confused:

Of coarse I might be missing something since I was quoted by both.

---

### Post by TripleD on 2011-08-02
> **bodhi.zazen said:**
> 
Read the README, sometimes that file will give you directions. look at the files, is there an uninstall.sh or other uninstall script ?

You can always try```
sudo make uninstall
```


Another site had suggested "sudo make uninstall", but that didn't work when I tried it.

The README was one of the first places I looked when I ran into trouble. It wasn't until later that I noticed a separate INSTALL document with information on where the files ended up. Once I'd removed them and run apt-get install again, everything proceeded smoothly.

---

### Post by EkuquoL on 2011-08-02
During manual installs... you can 
make uninstall ... That will auto uninstall all the files it created during install.

---

### Post by Furball588 on 2011-08-02
> **EkuquoL said:**
> During manual installs... you can 
make uninstall ... That will auto uninstall all the files it created during install.

That's assuming you have an uninstall option in the makefile

---

### Post by TheGrave on 2012-03-14
CheckInstall is the package that will ease your pain :)

---

