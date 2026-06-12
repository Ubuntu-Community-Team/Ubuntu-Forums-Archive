---
title: "How to uninstall a compiled gtk-splitter app"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Mega_Fauna on 2009-01-27
Hi,

How do I uninstall a compiled program which doesn't have it's own uninstaller script?


I installed gtk-splitter-2.2.1 by downloading the tar file and following the compile/install instructions included with it.

The program didn't work so I downloaded the rpm and converted to a deb with alien. That now won't install as it says a later version already exists.

What is my next step please?

---

### Post by taurus on 2009-01-27
How did you install it from source?  Did you do something like

```
./configure
make
sudo make install
```

---

### Post by Mega_Fauna on 2009-01-27
> **taurus said:**
> How did you install it from source?  Did you do something like

```
./configure
make
sudo make install
```

Thanks for the rapid response.

Yes, The following is from the README file and it's exactly what I did:

 Building a .deb package from source ]

 $tar -xzvf gtk-splitter-2.2.1.tar.gz
 $cd gtk-splitter-VERSION
 $./configure
 $./build_deb.sh

[ Installing the .deb package ]

 As root:
 $dpkg -i gtk-splitter-2.2.1-i386.deb

---

### Post by cariboo on 2009-01-27
You should be able to find the package in Synaptic or at the command line type:

```
sudo apt-get purge gtk-splitter-2.2.1-i386.deb
```

Easy.

Jim

---

### Post by Mega_Fauna on 2009-01-27
> **cariboo907 said:**
> You should be able to find the package in Synaptic or at the command line type:

```
sudo apt-get purge gtk-splitter-2.2.1-i386.deb
```

Easy.

Jim

Thanks for the code, however it doesn't uninstall for some reason, here is the Bash output:

```
sudo apt-get purge gtk-splitter-2.2.1-i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gtk-splitter-2.2.1-i386.deb
```

---

### Post by taurus on 2009-01-27
Couldn't you just uninstall it with dpkg?

```
sudo dpkg -r gtk-splitter
```

---

### Post by Mega_Fauna on 2009-01-27
> **taurus said:**
> Couldn't you just uninstall it with dpkg?

```
sudo dpkg -r gtk-splitter
```

Thanks! That worked and the new one is in.

I haven't used dpkg in at least a year, I've managed to use only .deb files and Synaptic, I know to use one or the other as they dpkg and Synaptic don't communicate, and so it hadn't occured to me to use it.

---

### Post by bruce89 on 2009-01-27
The package is called gtk-splitter, so *sudo apt-get purge gtk-splitter* would have worked.

> **Mega_Fauna said:**
> I haven't used dpkg in at least a year, I've managed to use only .deb files and Synaptic, I know to use one or the other as they dpkg and Synaptic don't communicate, and so it hadn't occured to me to use it.

That's not quite the case. dpkg is the program that is called by apt (or a frontend like Synaptic) which depackages Debian packages (hence the name).

---

