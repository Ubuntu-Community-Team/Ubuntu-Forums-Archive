---
title: "Installing OpenOffice"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by webwiller on 2010-05-20
Hi guys!
I downloaded Openoffice "*.deb.tar.gz" from the official site and now I have my directory with plenty of ".deb" files in it. I remember, cause I did last time, that I can install it with a simple command from terminal or launching the right file from the list, but I dont remember wich is the command or the file.
Another time I isntalled it the wrong way and I had to install each file following a right order and it took ages!
Can anybody help?
Tx in advance!

---

### Post by HereInOz on 2010-05-20
But, is it not already installed with every Ubuntu release?  Why would you want to install what is already there - unless you are after the latest and greatest version.

---

### Post by webwiller on 2010-05-20
I need the complete version

---

### Post by sandyd on 2010-05-20
cd /path/to/extracted/zip/OOO*/DEBS && cd desktop* && mv * ../ && cd ../ && sudo dpkg -i *.deb  make sure you remove the current openoffice (all of it!) before attempting the above commands. and just replace /path/to/extracted/zip with the path to where you extracted the zip to.

---

### Post by Paqman on 2010-05-20
> **webwiller said:**
> I need the complete version

Have you tried looking in Synaptic? What does the "complete" version have that's extra? You might find it's already packaged and ready to go.

---

### Post by magnus0 on 2010-05-20
just cd into the directory you have the debs and:
```
sudo dpkg -i *.deb
```

---

### Post by themusicalduck on 2010-05-20
I'm sure that all of open office is available in the software centre if you search for it. The default open office programs that are installed isn't all that's available.

I would search for open office in the software centre and try installing the OpenOffice.org Office Suite package.

---

### Post by ctimko on 2010-05-20
'sudo apt-cache search' is your friend.  Otherwise, untarball that: tar -zxf openoffice.deb.tar.gz and then and sudo dpkg -i openoffice.deb.  Good luck, and I will again reinforce that you should have the old Open office uninstalled. sudo apt-get purge openoffice (i don't know the package name off the top of my head).

---

