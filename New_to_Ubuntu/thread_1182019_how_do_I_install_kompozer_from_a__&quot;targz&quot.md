---
title: "how do I install kompozer from a  &quot;tar/gz&quot;"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by jonpon on 2009-06-08
Hi I got a new computer last week and installed 8.10 on it, but I've been having problems with kompoZer. I read in in this forum that the problem is a known one and that if I Uninstall the "Synaptic" version I can install a bug free version from the kompozer website. I've downloaded it (a tar.gz) and extracted it with the package manager to a file in my home folder, but How Do I Install It?

---

### Post by wpshooter on 2009-06-08
If there is some type of installation file that was extracted the issue a command something like:  sudo ./installer

---

### Post by SuperSonic4 on 2009-06-08
If you'd like the alpha then open a terminal (System -> Administation -> Terminal) and type in ```
cd kompozer-0.8a4
``` (or whatever your version is)

You might be able to run ```
./kompozer
``` or ```
run-mozilla.sh
``` but google isn't getting anything

---

### Post by jonpon on 2009-06-08
I found a file called "nsinstall"
and did this,  

```
jonpon@jonpon-laptop:~$ cd .kompozer
jonpon@jonpon-laptop:~/.kompozer$ sudo ./nsinstall
[sudo] password for jonpon: 
usage: ./nsinstall [-C cwd] [-L linkprefix] [-m mode] [-o owner] [-g group]
                   [-DdltR] file [file ...] directory
jonpon@jonpon-laptop:~/.kompozer$ 
```


not sure though what to do now...

---

### Post by wpshooter on 2009-06-08
Did you look to see if there is a text or help me file in the kompozer directory ?

---

### Post by jonpon on 2009-06-08
I'm not sure if it's useful but  here's a list

```
jonpon@jonpon-laptop:~$ dir .kompozer
bloaturls.txt	    libfreebl3.so      libsoftokn3.so	       res
chrome		    libgfxpsshar.so    libssl3.so	       run-mozilla.sh
components	    libgkgfx.so        libxpcom_compat.so      shlibsign
defaults	    libgtkembedmoz.so  libxpcom_core.so        TestGtkEmbed
dependentlibs.list  libgtkxtbin.so     libxpcom.so	       updater
dictionaries	    libjsj.so	       libxpistub.so	       updates
elf-dynstr-gc	    libmozjs.so        LICENSE		       xpcshell
extensions	    libnspr4.so        mangle		       xpicleanup
greprefs	    libnss3.so	       mozilla-installer-bin   xpidl
icons		    libnssckbi.so      mozilla-xremote-client  xpt_dump
kompozer-bin	    libplc4.so	       nsinstall	       xpt_link
kompozer-config     libplds4.so        plugins
kr5m3y1g.default    libsmime3.so       profiles.ini
libfreebl3.chk	    libsoftokn3.chk    regxpcom
jonpon@jonpon-laptop:~$ 
```

---

### Post by empty_spaces on 2009-06-08
If you downloaded the latest Kompozer tar.gz (called **kompozer-0.8a4-gcc4.2-i686.tar.gz**),
then just extract the contents to a folder and doubleclick on the file called **kompozer** in that folder. Kompozer should run as if it is installed.

---

### Post by jonpon on 2009-06-08
Thank you guys for your help.

---

### Post by paul0075 on 2009-10-13
Hi,

I am having the same issue, but also cannot run the kompozer executable unless I type in sudo ./kompozer in the terminal. Any suggestions? The permissions on the file are 755

Paul

---

### Post by tchoklat on 2009-10-13
... you will often run into issues if you run programs that are not in the repos. How do you update them etc? I run Kompozer from the repo with no issue. Stick with the tried and true!
 
tchoklat

---

### Post by paul0075 on 2009-10-13
I normally run the repo, but it has a known issue with my version of Ubuntu, and newer versions have been written to work around it. The repo version crashes when you change file manager settings and when you try to save.

---

### Post by vinutux on 2009-10-13
> **empty_spaces said:**
> If you downloaded the latest Kompozer tar.gz (called **kompozer-0.8a4-gcc4.2-i686.tar.gz**),
then just extract the contents to a folder and doubleclick on the file called **kompozer** in that folder. Kompozer should run as if it is installed.

+1 right...........xtract and run ...simple

---

