---
title: "How do i login as root ??"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by aravindc26 on 2009-05-20
How do i login as rooot ?   :confused:

---

### Post by zeroseven0183 on 2009-05-20
Hi! Why do you need to login as root?

---

### Post by kerry_s on 2009-05-20
> **aravindc26 said:**
> How do i login as rooot ?   :confused:

you don't, use **sudo** in command line and **gksudo** for gui programs, there's no reason to log in as root.

---

### Post by anjilslaire on 2009-05-20
In Debian-based distros like ubuntu, root is disabled by default, and is generally unnecessary.
Use sudo to perform administrative/root tasks, such as
```
 sudo apt-get install nameofapplication
```

or to edit config files
```

sudo gedit /path/to/file
```

---

### Post by aravindc26 on 2009-05-20
> **kerry_s said:**
> you don't, use **sudo** in command line and **gksudo** for gui programs, there's no reason to log in as root.
I rexently installed an app called kiso.
It asks me to login as root to launch the app.

---

### Post by lisati on 2009-05-20
As anjilslaire has pointed out, the preferred method of using root in Ubuntu is with sudo.

These web pages might be of interest:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/linux-hn/sudo.htm](http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/linux-hn/sudo.htm)

---

### Post by kerry_s on 2009-05-20
> **aravindc26 said:**
> I rexently installed an app called kiso.
It asks me to login as root to launch the app.

try this:
press **alt+f2**
type: **gksudo kiso**

---

### Post by zeroseven0183 on 2009-05-20
Launch it by typing **sudo kiso** on the Terminal

---

### Post by kerry_s on 2009-05-21
> **zeroseven0183 said:**
> Launch it by typing **sudo kiso** on the Terminal

you my friend need to learn. kiso is a gui program so gksudo or even gksu should be used for gui programs, while sudo shouldn't hurt, it's just wrong.

---

### Post by zeroseven0183 on 2009-05-21
> **kerry_s said:**
> you my friend need to learn. kiso is a gui program so gksudo or even gksu should be used for gui programs, while sudo shouldn't hurt, it's just wrong.

Yeah... sorry to miss the "gk" there. Thanks for reminding.

---

### Post by aravindc26 on 2009-05-21
> **kerry_s said:**
> try this:
press **alt+f2**
type: **gksudo kiso**
dude this method is gr8

---

### Post by kerry_s on 2009-05-21
> **zeroseven0183 said:**
> Yeah... sorry to miss the "gk" there. Thanks for reminding.

no big, i use to do it to. now a days i try to be more careful of any commands i give, hopefully 1 day policykit will take care of that and will no longer need to su,sudo,gksu,gksudo anything, just click on it, if requires a password it will ask, do your thing and done. wishfull thinking ;)

---

### Post by kerry_s on 2009-05-21
> **aravindc26 said:**
> dude this method is gr8

see, no root needed. ):P

---

### Post by adamogardner on 2009-05-21
> **kerry_s said:**
> you my friend need to learn. kiso is a gui program so gksudo or even gksu should be used for gui programs, while sudo shouldn't hurt, it's just wrong.

so "sudo synaptic" to open the package manager is incorrect?  it should be "gksudo synaptic"?

---

### Post by Marvin666 on 2009-05-21
Use gksudo for anything that dosn't run from a command line. Sudo is only for command line programs.

---

### Post by finer recliner on 2009-05-21
> **adamogardner said:**
> so "sudo synaptic" to open the package manager is incorrect?  it should be "gksudo synaptic"?

correct. any time you launch a GUI application (something with a window and buttons) such as synaptic, use gksudo. if you are just running an application in the terminal, such as apt-get, use sudo.

its a minor issue, but important to know.
more info here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by meganox on 2009-05-21
Yes.

To summarise:

gksudo for GUI apps:
 ```
Alt-F2
gksudo gedit /etc/foo
```sudo for terminal apps:
```
$ sudo apt-get install foo
```sudo -i to get a root shell (enter your own password):
```
user@machine:~$ sudo -i
[sudo] password for user: 
root@machine:~# 
```

These should be all you ever need

---

### Post by aravindc26 on 2009-05-21
> **meganox said:**
> Yes.

To summarise:

gksudo for GUI apps:
 ```
Alt-F2
gksudo gedit /etc/foo
```sudo for terminal apps:
```
$ sudo apt-get install foo
```sudo -i to get a root shell (enter your own password):
```
user@machine:~$ sudo -i
[sudo] password for user: 
root@machine:~# 
```These should be all you ever need


instead u can login as root with this code:

```
 sudo su 
```
enter your password.
when you are leaving don't forget to type exit.

---

### Post by Sef on 2009-05-21
Read the '[forum policy on login-as-root']("http://ubuntuforums.org/showthread.php?t=716201").   It explains why this thread is now locked.

---

