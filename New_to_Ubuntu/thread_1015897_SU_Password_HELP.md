---
title: "SU Password HELP"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by lenelson on 2008-12-19
I have Ubuntu 8.0.4 running on two computers in my home and when in Terminal mode, when I type su and it comes back asking for password, nothing works! Am I missing something? I always thought that the default was my user password (I am the only user) but that doesn't work and I am stumped. Any help at all??
Lyle Nelson (I am not smarter than a 5th grader)

---

### Post by sisco311 on 2008-12-19
by default, the root account is locked.
you can use *sudo* to run a command as root.

start a root shell with:
```
sudo -i
```

or run a command as root:
```
sudo *command*
```

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by rlunger on 2008-12-19
> **sisco311 said:**
> by default, the root account is locked.
you can use *sudo* to run a command as root.

start a root shell with:
```
sudo -i
```

or run a command as root:
```
sudo *command*
```



The sudo command will run any other programs as root, but only temporarily - just for that one command.  Note that while the command 'su' doesn't seem to work like you think it would, you have to prefix it with 'sudo'.  You can become root (for the entire terminal session) via:

    sudo su -

If you want to enable the root account for direct access (not that you would necessarily need to) use:

    sudo su -
    passwd

Now you can become root with 'su' without the 'sudo' wrapper.  Also note: you cannot login to a desktop session as root even if you have enabled direct access to the account.  This provides an extra level of security than you would normally have.

---

### Post by laurielegit on 2008-12-19
If you are planning to run a graphical application in this way, I recommend you use gksudo as sudo can muck up certain applications. See here for more info: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by jerome1232 on 2008-12-19
> **rlunger said:**
> The sudo command will run any other programs as root, but only temporarily

Actually, as previously mentioned, sudo -i gets you to a root shell where you can run as many commands as root as you like. Sudo pretty much replaces su in Ubuntu. (Admins can run commands as any user on the system with just the admin's password)

---

### Post by Michael.Godawski on 2008-12-19
Have a look on this short Introduction to the Concept of Root and Sudo.


[LIST]
[*][http://godawski.oxyhost.com/rootsudo.html](http://godawski.oxyhost.com/rootsudo.html)
[/LIST]

---

### Post by lenelson on 2008-12-20
I am fairly new to Linux but I worked with Unix some 20 years ago. My question is "how do you get a password for SU? I have only a single user on each of the machines I am using Ubuntu on and that password does not work! I am pretty crippled without Super User! Can I get help?????

---

### Post by Carl Hamlin on 2008-12-20
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

In Ubuntu by default the root account is disabled. Use of sudo is encouraged instead.

Syntax: sudo <command> <arguments>

When it asks for your password, it's the same one you're using to login.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklNOFEACgkQyLm4ydrABvdhyACgnPfjnzbWZbqA7RmSKJnwHxRa
0nUAniu/jW3BIZVF4vaMbFoEpqgSz4DG
=8jD0
-----END PGP SIGNATURE-----

---

### Post by perspectoff on 2008-12-20
You can also sudo -s and use your user password. sudo -s gives you root privileges.

More info and tips:

Kubuntu guide at [http://kubuntuguide.org](http://kubuntuguide.org)

Ubuntu guide at [http://ubuntuguide.org](http://ubuntuguide.org)

> **lenelson said:**
> I am fairly new to Linux but I worked with Unix some 20 years ago. My question is "how do you get a password for SU? I have only a single user on each of the machines I am using Ubuntu on and that password does not work! I am pretty crippled without Super User! Can I get help?????

---

### Post by perspectoff on 2008-12-20
You can also sudo -s and use your user password. sudo -s gives you root privileges.

More info and tips:

Kubuntu guide at [http://kubuntuguide.org](http://kubuntuguide.org)

Ubuntu guide at [http://ubuntuguide.org](http://ubuntuguide.org)

> **lenelson said:**
> I am fairly new to Linux but I worked with Unix some 20 years ago. My question is "how do you get a password for SU? I have only a single user on each of the machines I am using Ubuntu on and that password does not work! I am pretty crippled without Super User! Can I get help?????

---

### Post by Squid Tamer on 2008-12-20
Ignore this post.

---

### Post by bodhi.zazen on 2008-12-20
> **lenelson said:**
> I am fairly new to Linux but I worked with Unix some 20 years ago. My question is "how do you get a password for SU? I have only a single user on each of the machines I am using Ubuntu on and that password does not work! I am pretty crippled without Super User! Can I get help?????

As has been said many times on this therad, Ubuntu uses sudo not su :twisted;

so ....

```
sudo -i
```

> **Squid Tamer said:**
> I think that you can unlock it with something like

```
sudo passwd root
```Then give your password.

Setting a root password is un necessary and can cause breakage. As such we try to discourage this practice and it is rarely necessary.

---

### Post by lenelson on 2008-12-20
Thanks all of you, I think this thread can be closed now, I don't know how.
Lyle (lenelson)

---

