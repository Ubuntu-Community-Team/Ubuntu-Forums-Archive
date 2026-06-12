---
title: "Why am I getting this when I gedit a file?"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by newport_j on 2010-04-28
I am using a computer remotely and I am programming on it. Whenever I type gedit the file I wish to edit is brought up and works ok.

However, I get the following output when I gedit some file;

errol@fermi:/home/james/Desktop/WEGtest$ gedit
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".


I am not sure what is going on and I think that I would like to eliminate that from happening. What is this output saying and how do I get rid of it?

Newport_j

---

### Post by phidia on 2010-04-28
If you search that output you will get a lot of hits including unresolved previous threads at the Ubuntu forums. Linux Questions did seem to partially address your question-see if that thead [here]("http://www.linuxquestions.org/questions/linux-networking-3/help-with-x11-forwarding-over-ssh-784428/") gives you any help.

---

### Post by randumnumber on 2010-04-28
If you are connected remotely via SSH then you cannot use graphical things like gedit. Unless you start ssh with X11 support ...basically you are asking a program on another computer to give you a graphical interface which it cannot do unless you specifically tell it to. you need to enable -X when starting a session
```
man ssh
```
and look for -X

if that doesnt help here is one way
[http://www.ssh.com/support/documentation/online/ssh/adminguide/32/X11_Forwarding.html](http://www.ssh.com/support/documentation/online/ssh/adminguide/32/X11_Forwarding.html)

---

### Post by tica vun on 2010-04-28
As the guy above me said, looks like you're trying to use a graphical program through a CLI ssh session.

If you're looking for full-featured text editors that don't require a graphical interface, try emacs and vim.

---

