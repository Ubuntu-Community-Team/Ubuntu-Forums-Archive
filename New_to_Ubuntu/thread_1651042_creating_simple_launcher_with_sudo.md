---
title: "creating simple launcher with sudo"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by degarb on 2010-12-22
I wan't to create a startup and desktop launcher that will roughly read:
  sudo  "./home/dennis/abyssws/abyssws"

But cannot get abyssws to start.

---

### Post by degarb on 2010-12-22
also, I really must run in sudo since Ubuntu blocks all ports under 1024 ish without sudo.

However, this will make the server non runnable on reboot if I am not home.

---

### Post by bodhi.zazen on 2010-12-22
Depending on what that application is, you should either write an upstart script or add the command to /etc/rc.local

---

### Post by degarb on 2010-12-22
> **bodhi.zazen said:**
> Depending on what that application is, you should either write an upstart script or add the command to /etc/rc.local

1. Reading this rc.local   I don't understand why running something on logout will help start something at bootup.  Even it this is poor commenting, and will run on startup, she doesn't say what is the run directory.

2. Most new linux user cannot write scripts and just want sudo stuff to run.  I have written a script that works from desktop, except I must type my password, which will kill my webserver if wife or kids reboot the machine.  This isn't an issue running the web server in windows. 

3.  Even If I run the sript of desktop on startup, probably it wont work due to relative folder locations.

---

### Post by sisco311 on 2010-12-22
> **degarb said:**
> 1. Reading this rc.local   I don't understand why running something on logout will help start something at bootup.  Even it this is poor commenting, and will run on startup, she doesn't say what is the run directory.


*...at the end of each multiuser runlevel* means it's executed after all other init scripts have run.

> **degarb said:**
> 
2. Most new linux user cannot write scripts and just want sudo stuff to run.  I have written a script that works from desktop, except I must type my password, which will kill my webserver if wife or kids reboot the machine.  This isn't an issue running the web server in windows. 


That's why they provide a System-V style init script which should work in Ubuntu. 

Did you read the Installation Instructions? 

You have to go to the directory where you have installed Abyss Web Server and execute: 

```
./autostart-setup install
```

> **degarb said:**
> 
3.  Even If I run the sript of desktop on startup, probably it wont work due to relative folder locations.

I'm not sure if I understand this. Do you have to run the script from the directory where you have installed?

```
cd /home/dennis/abyssws 
./abyssws
```

---

### Post by bodhi.zazen on 2010-12-22
> **degarb said:**
> 1. Reading this rc.local   I don't understand why running something on logout will help start something at bootup.  Even it this is poor commenting, and will run on startup, she doesn't say what is the run directory.

I think you misunderstood rc.local . rc.local runs every time you boot and putting the command in there is easier then writing an init script.

> 2. Most new linux user cannot write scripts and just want sudo stuff to run.  I have written a script that works from desktop, except I must type my password, which will kill my webserver if wife or kids reboot the machine.  This isn't an issue running the web server in windows. 

Well, you do not need to write scripts if you use applications from the repositories. There are several web servers in the repos, from apache to nginx.

You installed something from outside the repos, so yes you are then expected to be able to configure it.

Also it is not "official" Ubuntu software, so, you should direct your feedback / frustration to the people who developed the package.

Personally I am extremely cautious installing a package that lacks documentation, including a README.

> 3.  Even If I run the script of desktop on startup, probably it wont work due to relative folder locations.

I suggest you take a look at the documentation then. You should be able to move the entire package to /usr/local

IMO anything run as root should be owned by root, and not a user.

---

