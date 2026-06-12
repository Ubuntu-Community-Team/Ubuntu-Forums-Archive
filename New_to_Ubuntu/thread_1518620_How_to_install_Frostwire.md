---
title: "How to install Frostwire?"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by adamjkok on 2010-06-26
I want to install Frostwire. Please just tell me how instead of automatically assuming that I'm going to do something illegal. Frostwire is *perfectly legal*, dowloading copyrighted music is not.

---

### Post by DougieFresh4U on 2010-06-26
Here ya [go]("http://www.frostwire.com/") ):P
You will need Java as well

---

### Post by adamjkok on 2010-06-26
> **DougieFresh4U said:**
> Here ya [go]("http://www.frostwire.com/") ):P
You will need Java as well

Java...

I installed "Ubuntu Restricted Extras," does that count?

---

### Post by DougieFresh4U on 2010-06-26
> **adamjkok said:**
> Java...

I installed "Ubuntu Restricted Extras," does that count?

Have you downloaded Frostwire and tried to run it?
Can't answer about the restricted extras as I do not use that package

---

### Post by adamjkok on 2010-06-27
> **DougieFresh4U said:**
> Have you downloaded Frostwire and tried to run it?
Can't answer about the restricted extras as I do not use that package

I just tried to install the package and got an error (screenshot attached).

---

### Post by Dr_Willis on 2010-06-27
Sun java is now in the 'partners' repository. The default java is  not the one by sun, (yes there are 2 different java's you can be using)

Frostwire  is one of the apps i recall in that past that required the sun java. 

Canonical's partner repositories provide packages a location for software vendors to publish applications. 

The partner repo itself can be added by running this in terminal:  (one long line)

```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner" 

``` &#9474;

There is also this guide on frostwire 
[https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire)

---

### Post by adamjkok on 2010-06-27
> **Dr_Willis said:**
> Sun java is now in the 'partners' repository. The default java is  not the one by sun, (yes there are 2 different java's you can be using)

Frostwire  is one of the apps i recall in that past that required the sun java. 

Canonical's partner repositories provide packages a location for software vendors to publish applications. 

The partner repo itself can be added by running this in terminal:  (one long line)

```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner" 

``` &#9474;

There is also this guide on frostwire 
[https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire)

I ran the command you suggested, and it appeared to complete successfully. However, I'm still getting an error.

---

### Post by Dr_Willis on 2010-06-27
After you add the partner repository, you then need to install the sun java packages. 

From what i recall from our IRC channel.

For the Sun Java products and browser plugin, search for thesun-java6- packages and install them.


the command 

java -version   will show what java you have installed. On my new system using the Non-Sun java i get the following.

$** java -version**
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8) (6b18-1.8-0ubuntu1)
OpenJDK 64-Bit Server VM (build 14.0-b16, mixed mode)

I am using the 'Icedtea' version of Java it seems. I will see if i can get frostwire going.


**Success**.. using the Icedtea java mentioned above  (the default i think ubuntu-restricted-extras package installed)  I downloaded the deb from

[http://www.frostwire.com/download/?os=ubuntu](http://www.frostwire.com/download/?os=ubuntu)

then installed it with 'sudo dpkg -i frostwire-4.20.6.i586.deb'

It seems to be working fine. So Im now not sure about your original problem.

It COULD be that by using the GUI Installer tools to install the deb. its wantng the sun java. which  used to be required for the app to work. But this no longer seems to be the case.  downloading the deb and installing by the command line line i did above should work.

---

