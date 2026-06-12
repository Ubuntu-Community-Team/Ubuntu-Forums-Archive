---
title: "Installing software without internet connection"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by manojps on 2010-01-30
I want to install Kdbg in one of my computers which doesn't have an internet connection. I have downloaded the kdbg i386 deb file and on installing it asks for dependency files one after other. Is there any method to install the software. This is a generalised question. What can i do when similar cases arise in installing other packages....

---

### Post by chaanakya_chiraag on 2010-01-30
I guess you could use apt-get build-dep to get an idea of all the dependencies, download them manually (or using a script), and then have dpkg install them one-by-one.

---

### Post by synapsys on 2010-01-31
You can go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and type in the name of the package you want to install. This way you can find out what dependencies you need to download in order to install the package.>         
      
                  **Other Packages Related to kdbg**


[LIST]
[*]            dep:     [kdelibs4c2a]("http://packages.ubuntu.com/hardy/kdelibs4c2a")      (>= 4:3.5.8-1)         core libraries and binaries for all KDE applications
[*]            dep:     [libc6]("http://packages.ubuntu.com/hardy/libc6")      (>= 2.7-1)         GNU C Library: Shared libraries      
also a virtual package provided by                 [libc6-udeb]("http://packages.ubuntu.com/hardy/libc6-udeb")
[*]            dep:     [libgcc1]("http://packages.ubuntu.com/hardy/libgcc1")              GCC support library
[*]            dep:     [libqt3-mt]("http://packages.ubuntu.com/hardy/libqt3-mt")      (>= 3:3.3.8really3.3.7)         Qt GUI Library (Threaded runtime version), Version 3
[*]            dep:     [libstdc++6]("http://packages.ubuntu.com/hardy/libstdc++6")      (>= 4.1.1-21)         The GNU Standard C++ Library v3
[/LIST]
            
[LIST]
[*]            rec:     [gdb]("http://packages.ubuntu.com/hardy/gdb")      (>= 5.0)         The GNU Debugger
[/LIST]
            
[LIST]
[*]            sug:     [kxsldbg]("http://packages.ubuntu.com/hardy/kxsldbg")              graphical XSLT debugger for KDE
[/LIST]
        


---

### Post by manojps on 2010-01-31
> **synapsys said:**
> You can go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and type in the name of the package you want to install. This way you can find out what dependencies you need to download in order to install the package.
But each of these dependency files are having its own dependency. :sad:

---

### Post by manojps on 2010-01-31
> **chaanakya_chiraag said:**
> I guess you could use apt-get build-dep to get an idea of all the dependencies, download them manually (or using a script), and then have dpkg install them one-by-one.
On submitting :apt-get build-dep kdbg the following message comes

Could not open file /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_karmic_main_source_Sources - open (2: No such file or directory)
:sad:

---

### Post by NightwishFan on 2010-01-31
With the internet access machine, use synaptic to select the packages you want, and when you apply check "download only".

Then install [aptoncd]("apt://aptoncd"). (Click to install)
```
sudo apt-get install aptoncd
```

Use aptoncd to make a CD/DVD to add to the offline system.

You could also try this to get packages on a Windows/Mac system:
[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by manojps on 2010-01-31
> **NightwishFan said:**
> With the internet access machine, use synaptic to select the packages you want, and when you apply check "download only".

Then install [aptoncd]("apt://aptoncd"). (Click to install)
```
sudo apt-get install aptoncd
```Use aptoncd to make a CD/DVD to add to the offline system.

You could also try this to get packages on a Windows/Mac system:
[http://keryxproject.org/](http://keryxproject.org/)

It worked

Thank you very much....:popcorn::KS

---

### Post by NightwishFan on 2010-01-31
No problem, my main system is very unreliable on the net, and I am used to working offline.

---

### Post by chaanakya_chiraag on 2010-01-31
If this is fixed, please mark the thread as solved (Thread Tools -> Mark as Solved).  Thanks :)

---

