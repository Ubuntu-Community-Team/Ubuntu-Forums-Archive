---
title: "tar.gz files installation"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by patilkaustubhv on 2009-05-04
Please can ne1 tell me how to install tar.gz files......???????


I am a newbie and would prefer gui.......

if terminal has no option please explain in detail.....

Thanks

---

### Post by canadiandude007 on 2009-05-04
Hello, I am not sure I understand you correctly.

tar.gz files are compressed files (like Zipped files in Windows)

To extract or decompress them, you can run a command like this:

> tar zxvf <name of file>.tar.gz

to extract or decompress the file to the same directory (or folder) it is in.

Does that help?

---

### Post by Marat Galiev on 2009-05-04
True way - install from repos and *.deb packages.
But if you want:
tar -zxf arc.tar.gz
cd arc
./configure
make
make install

And read README file)))

---

### Post by 3rdalbum on 2009-05-04
1. Have you looked in Synaptic Package Manager to see if the program is available for easy download and install from there?

2. Have you looked inside the tar.gz file at the installation instructions? Usually there is a file that is called INSTALL or README.

---

### Post by patilkaustubhv on 2009-05-04
I downloaded tightVNC it was only offered in tar.gz files and not the .deb package..... so.... have i downloaded wrong files?????????/

---

### Post by halitech on 2009-05-04
if you need a vnc program, vnc4server is in the repos (or was last time I used it)

---

### Post by Skrynesaver on 2009-05-04
tightvnc is available in the universe repository, go to System >Administration> Software sources.
Select "Comunity maintained Open Source Software".
Now open System>Administration>Synaptic Package Manager.
In Synaptic, search for VNC, select the packages you wish to install.
Apply changes. tightvnc will be installed.

This is better than installing from a tarball as the package management system will keep your system up to date with any improvements (security improvements in a package like tightVNC are essential and so should always be installed via Synaptic or apt)

Hope this helps

---

### Post by patilkaustubhv on 2009-05-04
Thanks

---

