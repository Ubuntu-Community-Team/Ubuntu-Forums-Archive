---
title: "Sun Java 6 on Ubuntu 10.04"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by Ikith on 2010-05-01
So I just installed Ubuntu 10.04 again after having an issue with my laptop hard drive and now all of a sudden I cannot apt-get sun-java6 packages which I would like. I don't really like open java never really have for some reason. I had it on my laptop before I ran into hard drive issues and now I just can't get it anymore and whenever I try I get this:

mearle@mearle-laptop:~$ sudo apt-get install sun-java6-doc sun-java6-fonts sun-java6-jdk sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-doc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-doc has no installation candidate

Really annoying.

---

### Post by cap10Ibraim on 2010-05-01
java is included in the Ubuntu restricted extras in the software center

---

### Post by luckymancvp on 2010-05-01
After installed ubuntu, I install Ubuntu restricted extras + Netbean 6.8 + Eclise .

Now I can run java with java docs. (In ubuntu 9.10, I install java-doc but always fail).

---

### Post by mickie.kext on 2010-05-01
Why not use OpenJDK? It is in standard repos.

---

### Post by alexcckll on 2010-05-01
Sun Java has been moved to the Partner repository, and is being maintained by Oracle themselves.

Go into Software Sources and enable the partner repos... and allow a reload..

---

### Post by Linuxforall on 2010-05-01
This is good news indeed, now we don't need to use the hack method to install Sun Java latest.

---

### Post by lkraemer on 2010-05-01
To enable Partner Repo:
SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES -> OTHER SOFTWARE -> ADD
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

Then CLOSE window and RELOAD, then search for Sun Java
You should find Version 6.20 ..... Install

(deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
is added to the end of /etc/apt/sources.list)
ie...  sudo nano /etc/apt/sources.list

lk

---

### Post by RikardSvenningsen on 2010-05-01
> **lkraemer said:**
> To enable Partner Repo:
SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES -> OTHER SOFTWARE -> ADD
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

Then CLOSE window and RELOAD, then search for Sun Java
You should find Version 6.20 ..... Install

(deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
is added to the end of /etc/apt/sources.list)

lk

This solved my problem whit missing sun-java6
Thanks...

---

### Post by ArionKrause on 2010-05-01
> **RikardSvenningsen said:**
> This solved my problem whit missing sun-java6
Thanks...

Solved for me too! Thanks!

---

### Post by grackleman on 2010-05-01
Hi
I tried it and was told the repository was not available.

I tried 'sudo add-apt-repository &#8220;deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner&#8221;' and got the message that it needed a repository as an argument.

Is the partner repository still there?

Thanks

---

### Post by howefield on 2010-05-01
> **grackleman said:**
> Is the partner repository still there?

Yes, it's still there, try adding via software sources.

System > Administration > Software Sources > Other Software tab.

---

### Post by scottishbloke on 2010-05-01
I now use the ubuntu restricted extra's and ive got to say i think thats the best way to go where java etc is concerned, seems to run a lot better than sun java IMHO\\:D/

---

### Post by philinux on 2010-05-01
Just to clarify.

Sun java has been deprecated in 10.04
Openjdk is now the default, i.e installing ubuntu-restricted-extras with recommends, will install openjdk and the icedtea plugin. Openjdk has been certified by Java SE Test Compatibility Kit (TCK) and is compatible with the Java(TM) SE 6 platform on the amd64 (x86_64) and i386 (ix86) architectures. However sun-java is in the partner repo.
There's a bug regarding the icedtea plugin and certain applets.
[https://bugs.launchpad.net/ubuntu/+s...-6/+bug/551328](https://bugs.launchpad.net/ubuntu/+s...-6/+bug/551328).
Not fixed yet. Workaround may be to create a new Firefox profile.

---

### Post by voooova on 2010-05-09
> **lkraemer said:**
> To enable Partner Repo:
SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES -> OTHER SOFTWARE -> ADD
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

Then CLOSE window and RELOAD, then search for Sun Java
You should find Version 6.20 ..... Install

(deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
is added to the end of /etc/apt/sources.list)
ie...  sudo nano /etc/apt/sources.list

lk
I add this repo, but sun-java6-doc is still missing and Netbeans autocomplete don't show javadocs. I use sun java because it is compatible with windows and my teachers use only it..

---

### Post by lkraemer on 2010-05-09
Google search for Documentation finds:

[http://java.sun.com/javase/6/docs/](http://java.sun.com/javase/6/docs/)
[http://java.sun.com/javase/downloads/index.jsp#docs](http://java.sun.com/javase/downloads/index.jsp#docs)


Google is Amazing........You need to check it out!

lk

---

### Post by kc0dhb on 2010-06-15
lkraemer: Not really helpful. The sun-java6-doc package is (well was) a nice way to install the docs locally using the built in package managers.

I ran into the same issue today. My workaround to get it installed. I basically grabbed a prior package (that worked) and used it with lynx.

Get this sun-java6-doc package
```
http://packages.ubuntu.com/en/karmic-updates/sun-java6-doc
```

Install it
```
sudo dpkg -i ${package_name}
```

Then do what it tells you and download the jdk docs.
```
http://java.sun.com/javase/downloads/index.jsp#docs
```

---

### Post by wojox on 2010-06-15
This will install Java on Lucid [ Install Java on Lucid]("http://wojox.homelinux.org/?p=78")

---

### Post by rockberto on 2010-11-18
I got the documentation working with this steps:

1) Download the documentation from
> [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

2) Unzip it to
> /usr/lib/jvm/java-6-sun

In my case I downloaded jdk-6u22-docs.zip and extracted it to /usr/lib/jvm/java-6-sun-1.6.0.22

I guess I'll have to do this by hand every time java is updated.

---

