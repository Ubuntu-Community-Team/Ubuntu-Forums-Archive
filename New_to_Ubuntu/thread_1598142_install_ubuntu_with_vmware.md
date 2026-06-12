---
title: "install ubuntu with vmware"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by romulusro on 2010-10-16
Hi,
I can't install ubuntu 10.10 on my computer with vmware 6.0.3. 
I've read the instalation guide, it didn't help me because I don't see boot menu for ubuntu instalation.

After starting vmware I don't get the boot menu to start the instalation(in graphical mode)- I get the screen like this:
"
Linux ubuntu 2.6.35-22-generic #33- Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu !
* Documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)

To run a command as administrator (user "root), use "sudo <command". See "man sudo_root" for details
ubuntu@ubuntu: ~$
"

Sorry for this beginner question, but I don't know how to continue to go to the next step and I didn't find the answer.

Thanks in advance

---

### Post by romulusro on 2010-10-18
a small hint please.... what I am doing wrong ?

---

### Post by romulusro on 2010-10-22
I don't know why nobody replied...either my question was too simple or too complex :confused:
Hopefully I managed it - I installed the latest version of vmware and now it works. I don't know if there are other solutions, but I am happy that I found one.

good day !

---

### Post by Paqman on 2010-10-22
The problem was most likely that your virtual graphics weren't set up, or that Ubuntu didn't recognise them. In cases like that, you'll get dropped to a command line system. Entering the command:
```
startx
```
...can be useful, as it will spit out errors that will hint at where the problem is. Glad you've got your system up and running though!

One question though: did you actually use Wubi to install Ubuntu into a VM? Unless you're testing Wubi it's a bit of an odd thing to do.

---

### Post by romulusro on 2010-10-22
Thanks for your reply, at least now I will know other solutions to solve the problem.
The tag was inserted by mistake, so actually I used the normal way for installation(I didn't find a way to change the tag after posting the message)

---

