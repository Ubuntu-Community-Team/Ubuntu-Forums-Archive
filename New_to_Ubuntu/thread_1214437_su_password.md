---
title: "su password?"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by Java Geek on 2009-07-15
I am the administrator on my kubuntu system and I know the root password.

When I type sudo into the konsole and it asks me for my password, it works, however, when i type su and enter the same password, it is incorrect, Is there a way to fix this?

---

### Post by jerome1232 on 2009-07-15
If you enabled the root account than su will require whatever password you setup for root not your user accounts password like sudo requires.

Unlocking the root account is discouraged in Ubuntu as it goes against the security model.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by philcamlin on 2009-07-15
sudo su 
 then type your admin pass and your good to go 

thats what i did

---

### Post by Java Geek on 2009-07-15
> **jerome1232 said:**
> If you enabled the root account than su will require whatever password you setup for root not your user accounts password like sudo requires.

Unlocking the root account is discouraged in Ubuntu as it goes against the security model.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

OH! Ok, Well how do you run a file with sudo from the terminal?

---

### Post by lavinog on 2009-07-15
> **Java Geek said:**
> OH! Ok, Well how do you run a file with sudo from the terminal?

sudo command

you can also use sudo -s to start a root shell

---

### Post by n8bounds on 2009-07-15
> **philcamlin said:**
> sudo su 
 then type your admin pass and your good to go 

thats what i did
actually, the wiki says that 

```

sudo -i

```

is the preferred way of becomming root without actually "enabling" the root account

---

### Post by aysiu on 2009-07-15
> **Java Geek said:**
> OH! Ok, Well how do you run a file with sudo from the terminal?
As in run a shell script? ```
sudo ./nameofscript.sh
```

---

### Post by aysiu on 2009-07-15
> **lavinog said:**
> sudo command

you can also use sudo -s to start a root shell
Please don't use *sudo -s*

*sudo -s* runs with root privileges but with the user's environment. This can lead to breakage (user configuration files changing to root ownership).

If you need a persistent root login, use ```
sudo -i
```

---

### Post by philcamlin on 2009-07-15
> **n8bounds said:**
> actually, the wiki says that 

```

sudo -i

```is the preferred way of becomming root without actually "enabling" the root account

aha thanks i learned somethign today :)

---

### Post by thiebaude on 2009-07-15
gksudo.

---

### Post by jerome1232 on 2009-07-15
Just prepend sudo to the front of it, if you need to run alot of commands as root one after the other you can use sudo -i or sudo su to gain a root shell and run them. If you want to run a graphical app you use gksu or kdesu depending on if you are using gnome or kde

ie

```
sudo apt-get upgrade
```

```
sudo -i
apt-get upgrade
exit
```

```
gksu gparted
```

hope that helps

---

### Post by lavinog on 2009-07-15
> **aysiu said:**
> Please don't use *sudo -s*

*sudo -s* runs with root privileges but with the user's environment. This can lead to breakage (user configuration files changing to root ownership).

If you need a persistent root login, use ```
sudo -i
```

Good to know.
I always used -s because it was easier to associate 's' with shell.

---

### Post by aysiu on 2009-07-15
> **lavinog said:**
> Good to know.
I always used -s because it was easier to associate 's' with shell.
Well, now that you know the risk, you're welcome to do it on your own machine, but I think it's probably best if you avoid recommending it to other users on the forums. ```
username@ubuntu:~$ **sudo -s**
[sudo] password for username: 
root@ubuntu:~# $HOME
bash: **/home/username:** is a directory
root@ubuntu:~# exit
exit
username@ubuntu:~$ **sudo -i**
root@ubuntu:~# $HOME
-bash: **/root:** is a directory
root@ubuntu:~# exit
logout
username@ubuntu:~$ **sudo su**
root@ubuntu:/home/username# $HOME
bash: **/root:** is a directory
root@ubuntu:/home/username# exit
exit
username@ubuntu:~$ 
```

---

### Post by Java Geek on 2009-07-15
> **aysiu said:**
> As in run a shell script? ```
sudo ./nameofscript.sh
```

yes exactly.

---

