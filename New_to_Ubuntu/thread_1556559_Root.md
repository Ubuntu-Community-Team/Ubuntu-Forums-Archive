---
title: "Root"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by justin43384 on 2010-08-19
This is probably a really stupid question, but how do run Terminal as Root?

---

### Post by endotherm on 2010-08-19
Alt + F2 and enter
gksu gnome-terminal

or from within a terminal, issue the command:
```
sudo -s
```

---

### Post by Rumpletumbler on 2010-08-19
> **justin43384 said:**
> This is probably a really stupid question, but how do run Terminal as Root?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jakupl on 2010-08-19
> **justin43384 said:**
> This is probably a really stupid question, but how do run Terminal as Root?

```
sudo -i
```

---

### Post by justin43384 on 2010-08-19
thanks man

---

### Post by linux18 on 2010-08-19
you use sudo to temporarily become root, example:
sudo apt-get update
 if you need to run a lot of commands as root then type
 sudo -s 
to become root in that terminal, however it is not recommended to become root in any normal situation

---

### Post by endotherm on 2010-08-19
here is a quick demo of the diff between sudo -i and -s. -s preserves the users profile info, while -i uses roots:
```

user@Lucid:~$ sudo -s
[sudo] password for user: 
root@Lucid:~# pwd
/home/user
root@Lucid:~# exit
exit
user@Lucid:~$ sudo -i
user@Lucid:~# pwd
/root


```

---

### Post by jakupl on 2010-08-19
@Rumpletumbler
This is pretty weird. I think it's against forum policy to post links on how to aquire root login.
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
However, I'm not sure about it, when the link is official ubuntu documentation.

---

### Post by lisati on 2010-08-19
The links I would have posted have already been mentioned:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by endotherm on 2010-08-19
> **jakupl said:**
> @Rumpletumbler
This is pretty weird. I think it's against forum policy to post links on how to aquire root login.
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
However, I'm not sure about it, when the link is official ubuntu documentation.
they are kind of relaxing on that point, as long as the consequences are made clear. personally I've just come to the conclusion that the need to actually enable root is so rare and so esoteric, that anyone who actually needs to do it, already knows how, or knows how to find out inside 10 clicks.

---

### Post by KdotJ on 2010-08-19
It is not recommended to login or use things as root. That's why we have sudo. Though the steps you need to take so are documented, here on the forums we do not talk about it. Using sudo for commands is the preferred way to carry out administrative tasks in the terminal. 

As a side note, using sudo actually gives you a 'grace period' which I think is about 15 mins by default (the time limit can be changed in some config file). This means you only have to use sudo for the first command

---

### Post by linux18 on 2010-08-19
> **KdotJ said:**
> It is not recommended to login or use things as root. That's why we have sudo. Though the steps you need to take so are documented, here on the forums we do not talk about it. Using sudo for commands is the preferred way to carry out administrative tasks in the terminal. 

As a side note, using sudo actually gives you a 'grace period' which I think is about 15 mins by default (the time limit can be changed in some config file). This means you only have to use sudo for the first command
you still have to use sudo, the grace period is for entering your password

---

### Post by KdotJ on 2010-08-19
> **linux18 said:**
> you still have to use sudo, the grace period is for entering your password

Lol you do indeed, my mistake. Thanks for the correction :)

---

