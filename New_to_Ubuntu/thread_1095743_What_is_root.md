---
title: "What is root"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by imax_tm on 2009-03-14
Please i just installed ubuntu 8.10, im tryin to get it to surf with my mobile phone as a modem, i was told to edit the wvdial.conf file bit i cant it tells me i dont have do not have permmision to do so, so wall posts said i should open it as root. Please how do i do that...

---

### Post by sisco311 on 2009-03-14
> **imax_tm said:**
> Please i just installed ubuntu 8.10, im tryin to get it to surf with my mobile phone as a modem, i was told to edit the wvdial.conf file bit i cant it tells me i dont have do not have permmision to do so, so wall posts said i should open it as root. Please how do i do that...

Open a terminal (Applications -> Accessories -> Terminal)
and type:


```
gksu gedit /etc/wvdial.conf 
```

[uhelp]community/RootSudo[/uhelp]

---

### Post by mikewhatever on 2009-03-14
Read this [http://psychocats.net/ubuntu/permissions](http://psychocats.net/ubuntu/permissions).

In short, go alt+f2, type **gksudo nautilus** and edit whatever you like.

---

### Post by hansdown on 2009-03-14
Hi imax_tm.

See this.

[http://www.nfstuning.com/forum/blog.php?b=75](http://www.nfstuning.com/forum/blog.php?b=75)

---

### Post by pbpersson on 2009-03-14
root is the "super user" account in any Unix/Linux system.

In Ubuntu to perform root functions you use the "sudo" command.

For instance, if I wanted to edit a file called samba.conf I would use the cd command in terminal to get to the directory, then I would type:

sudo gedit samba.conf 

and when it asked for a password I would enter my own password.

When making any changes, it is a good idea to make a backup copy of the file before you start such as:

cp samba.conf samba.mybackup200903114

---

### Post by nelskurian on 2009-03-14
ooh delayed..

You created an admin user while on installation...He has the root privileges.For using the privileges ,You should use
```
sudo  
```before any terminal commands.
eg. ```
sudo gedit /foo/bar
gksu gedit /foo/bar
```
Also you can activate the root account by assigning a password to root
```
sudo passwd 
```
The above will activate the root account with the supplied password.

---

### Post by PryGuy on 2009-03-14
Well, root is a superuser in Linux/Unix systems. Root actually is God in Linux, it can do anything!
To do something as a root in Ubuntu you just have to enter the root password that is an exact copy of your password. So just type your password when Ubuntu asks you for that. If you do something it Terminal use the 'sudo' command. It allows you to execute a single command as a root being not root. Being in terminal compare the output of the following commands:
 ```
whoami
```and```
sudo whoami
```and you'll get it. As you you probably learnt 'whoami' is "Who Am I?" and shows what user are you at the moment.
Have Fun!

---

