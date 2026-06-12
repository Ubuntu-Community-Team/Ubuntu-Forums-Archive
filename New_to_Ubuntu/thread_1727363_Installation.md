---
title: "Installation"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by Greg93 on 2011-04-12
Can I install Ubuntu desktop on top of an Ubuntu LAMP install?
 
Greg

---

### Post by grvsaxena419 on 2011-04-12
> Can I install Ubuntu desktop on top of an Ubuntu LAMP install?
Could you please explain a bit what do you mean by Ubuntu LAMP install ?

---

### Post by Rex Bouwense on 2011-04-12
Are you talking about replacing the server with a desktop edition?

---

### Post by Blasphemist on 2011-04-12
Are you wanting to downgrade to desktop from server edition and if so are you having an issue? LAMP can be installed on a desktop without changing the system from desktop. How did you install LAMP. If you started with desktop and installed LAMP and now want to kill apache, mysql, php and whatever other development environment you may have installed, you may want to do a clean install over your Ubuntu install.

I have natty Ubuntu, LAMP and other development environment components installed on this laptop. The desktop and netbook editions have been combined and with natty are now just Ubuntu. There is also Ubuntu Server. I installed natty Ubuntu (11.04) and then LAMP and the rest. That doesn't put me on Ubuntu Server.

If you want to start over with a clean install, backup home and during the install choose to have it erase and reinstall.

---

### Post by earthpigg on 2011-04-12
> **Greg93 said:**
> Can I install Ubuntu desktop on top of an Ubuntu LAMP install?
 
Greg

yup.

```
sudo apt-get install ubuntu-desktop
```

i'd be wary of playing any games or doing anything CPU-intensive, though, as it may degrade the server's performance if it is a high-workload server. avoid flash-heavy websites, for example.

i'd even go so far as to say that you should keep a terminal window open with htop, so you can ensure that nothing you are doing is stressing the system.

---

### Post by earthpigg on 2011-04-12
> **grvsaxena419@gmail.com said:**
> Could you please explain a bit what do you mean by Ubuntu LAMP install ?

Linux, Apache, MySQL, PHP/Python.

[Standard webserver]("http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29"). :)

---

### Post by wep940 on 2011-04-12
You can always install a GUI desktop with the server version of Ubuntu, but there are many posts out, from some extremely knowledgable people, that say not to - I think it's something to do with security on the server, but I'm not sure.

---

### Post by 3rdalbum on 2011-04-12
> **wep940 said:**
> You can always install a GUI desktop with the server version of Ubuntu, but there are many posts out, from some extremely knowledgable people, that say not to - I think it's something to do with security on the server, but I'm not sure.

If you want to, then do it. Servers generally only run the software that they actually need to be running in order to operate as a server; this is done for performance reasons as well as security reasons (less software == less possible security holes).

But for your own server, there won't really be a problem. The Ubuntu desktop is pretty secure anyway.

---

### Post by earthpigg on 2011-04-12
> **3rdalbum said:**
> If you want to, then do it. Servers generally only run the software that they actually need to be running in order to operate as a server; this is done for performance reasons as well as security reasons (less software == less possible security holes).

and that is generally the only reason people say "dont run desktop software on a server!"

a lot of time has been spent making server software hardened against attacks, whereas new firefox security vulnerabilities are discovered every month.

---

### Post by grvsaxena419 on 2011-04-13
> Linux, Apache, MySQL, PHP/Python.

Standard webserver. 

Thanks for explaining. I knew the meaning of LAMP i just wanted to know which type of installation was that server or desktop :)

---

