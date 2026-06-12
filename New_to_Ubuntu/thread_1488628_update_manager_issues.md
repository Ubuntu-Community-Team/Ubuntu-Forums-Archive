---
title: "update manager issues"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by jmitche1 on 2010-05-20
Trying to run my update manager and seeing a message stating:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure-a' to correct the problem

When I try to run that command I receive: Command not found.

I feel it may have been a problem with my computer shutting off while in the middle of an update. Can anyone help me? I tried a search but if I overlooked something, my apologizes.

---

### Post by blazemore on 2010-05-20
I think you may have mis-typed the command!
Copy and paste this:
```
sudo dpkg --configure -a; sudo apt-get -f install
```This happens if you turn the computer off while the updates are installing (not downloading)

---

### Post by jmitche1 on 2010-05-20
Thanks for your help. Again I'm pretty new to this but willing to learn.

I type that in the terminal and recieve this:
dpkg: unknown option --configure-a

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
guest@guest-laptop:~$

---

### Post by Peter09 on 2010-05-20
I Think that the command needed a space between configure and -a - see below.
 
```
sudo dpkg --configure -a; sudo apt-get -f install
```

---

### Post by blazemore on 2010-05-20
> **Peter09 said:**
> I Think that the command needed a space between configure and -a - see below.
 
```
sudo dpkg --configure -a; sudo apt-get -f install
```

Very sorry, my mistake. I've updated the post above, but yes, that's the problem.

---

