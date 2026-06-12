---
title: "Need help installing XAMPP"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by ApacheOmega on 2011-02-03
I'm trying to install XAMPP - where do I find the Linux shell?

---

### Post by DiSTORT3D on 2011-02-03
you mean terminal?

accesoires > terminal

---

### Post by ApacheOmega on 2011-02-03
Thank You

---

### Post by ApacheOmega on 2011-02-03
OK I typed in SU and when I try to put in My Password it wont even lat me type the curser just sits there

---

### Post by Thetherumcompound on 2011-02-03
It's fine. The password prompt won't show anything when you enter stuff in. Just type it in and press enter.

---

### Post by ApacheOmega on 2011-02-03
Man I  dont know if some A hole has already hacked into my stuff but I enter su when asked and when I type in my password and I know it's the right one because it works for everything else it says authentication failure and thats the problem I've been having any time something has to do with servers - I'm getting Highly suspicious.

---

### Post by sandyd on 2011-02-03
> **ApacheOmega said:**
> Man I  dont know if some A hole has already hacked into my stuff but I enter su when asked and when I type in my password and I know it's the right one because it works for everything else it says authentication failure and thats the problem I've been having any time something has to do with servers - I'm getting Highly suspicious.
```

sudo -i
```
or just prefix each command with
```
sudo
```

---

### Post by Thetherumcompound on 2011-02-03
You need to enter sudo su

---

### Post by damispyderbyte on 2011-02-03
In ubuntu there is a randomized root password. Sudo is the command you are looking for. Noone hacked you, trust me - its almost impossible.

---

### Post by ApacheOmega on 2011-02-03
thanks fellas I'm at step 2 and this is what it wants me to enter at extraction point - tar xvfz xampp-linux-1.7.4.tar.gz -C /opt - do I just paste this into the given field? - and sorry I'm asking all these questions I'm new to this but I want to totally get away from windows....

---

### Post by lkjoel on 2011-02-03
> **ApacheOmega said:**
> thanks fellas I'm at step 2 and this is what it wants me to enter at extraction point - tar xvfz xampp-linux-1.7.4.tar.gz -C /opt - do I just paste this into the given field? - and sorry I'm asking all these questions I'm new to this but I want to totally get away from windows....
Yes.
You might be interested in LAMP instead of XAMPP.
LAMP is much easier to install, and is optimized for Linux.
LAMP is installed using the official Ubuntu repositories.
To install, simply type in a Terminal window:
```
sudo tasksel install lamp-server
```
It's better for people new to Ubuntu.

---

### Post by DiSTORT3D on 2011-02-03
xampp is easier, more addons in 1 single simple install, but then again alot of it most users dont use.

```
tar xvfz xampp-linux-*.tar.gz -C /opt
``````
/opt/lampp/lampp start
```

---

### Post by sandyd on 2011-02-03
> **lkjoel said:**
> Yes.
You might be interested in LAMP instead of XAMPP.
LAMP is much easier to install, and is optimized for Linux.
LAMP is installed using the official Ubuntu repositories.
To install, simply type in a Terminal window:
```
sudo tasksel install lamp-server
```It's better for people new to Ubuntu.
tasksel isnt installed by default now on desktop

---

### Post by lkjoel on 2011-02-03
> **sandyd said:**
> tasksel isnt installed by default now on desktop
I think it is.
Take a look at [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by DiSTORT3D on 2011-02-03
> **lkjoel said:**
> I think it is.
Take a look at [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


```
root@Machine:/home/distort3d# sudo tasksel install lamp-server
sudo: tasksel: command not found
root@Machine:/home/distort3d# 
```

---

### Post by sandyd on 2011-02-04
> **lkjoel said:**
> I think it is.
Take a look at [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
Read [https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel).
The ApacheMySQLPHP is currently immutable, so ill just let it be...

---

### Post by ssaeidd on 2011-05-11
i install xampp 1.7.4 on linux 11.04 from [this method]("http://www.matsearle.com/blog/install-xampp-ubuntu-linux") but at the end when i trying to start xampp i recive this error :
```
xampp is currently only available as 32 bit application.please us a 32 bit compatibility library for your system .
```
whats the problem ????

---

