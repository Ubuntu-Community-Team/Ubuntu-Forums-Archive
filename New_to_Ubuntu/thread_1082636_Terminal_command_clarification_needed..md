---
title: "Terminal command clarification needed."
date: 2009-02-28
forum: New to Ubuntu
---

### Post by CRIMPS on 2009-02-28
So I have been making some changes to my xorg.conf file.  My changes worked and I am quite satisfied.  However, I was hoping someone could clarify why running this command creates a new file instead of just opening the current file.
```
sudo gedit /etc/x11/xorg.conf
```

I usually just close the newly created file without saving and reopen the original file in Nautilus.  I guess a better question would be how should I change my script to open the current file instead of creating a new file called xorg.conf.  

Thanks!

---

### Post by adult swim on 2009-02-28
youve got the wrong path to xorg.conf,
it is /etc/X11/xorg.conf, the X must be captial, not x
also when using sudo for a graphical program like gedit, it is best to use gksudo.
the command gksudo gedit /etc/X11/xorg.conf should be what you enter in

---

### Post by CRIMPS on 2009-02-28
Perfect!  What is frustrating is that I knew that terminal commands are case sensitive.  I should have figured that out.  Thanks for you help!

---

### Post by bodhi.zazen on 2009-02-28
first, you should use gksu for graphical applications

```
gksu gedit /etc/**X**11/xorg.conf
```gksu prevents root from over writing config files in your home directory, which can cause problems. It also give access to X (your gui) in a safe and sane way. If you want to read the gory details see :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Second, it is an X in X11, not an x. Linux is case sensitive.

---

### Post by Xiong Chiamiov on 2009-02-28
You'll avoid a lot of problems like that if you use tab-completion.  If a file doesn't exist, then tab won't expand out to it.  That's often how I know I'm off a directory or I've made a typo.

---

