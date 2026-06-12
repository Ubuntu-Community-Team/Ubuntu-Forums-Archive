---
title: "Java based chatroom not working in ubuntu 10.10"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by theginge99 on 2010-11-03
I have been using ubuntu since 10.4 and found that most things work without much fiddling, but try as I may I just cant get my favourite chatroom to work. It is a java based room and when I try to get on it all I get is a blank box on the web page, not even a 'sorry java isnt working' type message.
 
Ive tried different web browsers and reistalling java all to no avail.
 
Does anyone know if this is a recognised problem and what else I can try to resolve it.
 
Many thanks

---

### Post by cavh on 2010-11-03
Please post the output of ```
java -version
``` typed into a terminal. Does this match what your chat room requires in order to work?

---

### Post by janpol on 2010-11-03
Maybe it's a problem related with openjdk, have you tried installing sun's java runtime?

Go to the Software Center and enable the partners repository, wait till it updates, and install it from there. Or, from a console:

```
sudo add-apt-repository &#8220;deb http://archive.canonical.com/ lucid partner&#8221;
```

```
sudo apt-get update
```

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

After that, check if it is installed properly running:

```
java -version
```

---

### Post by beew on 2010-11-03
> **janpol said:**
> Maybe it's a problem related with openjdk, have you tried installing sun's java runtime?

Go to the Software Center and enable the partners repository, wait till it updates, and install it from there. Or, from a console:

```
sudo add-apt-repository &#8220;deb http://archive.canonical.com/ lucid partner&#8221;
``````
sudo apt-get update
``````
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```After that, check if it is installed properly running:

```
java -version
```

Unless OP uninstalls Open Java or change Ubuntu's java default, openjdk will still be the default even if s/he installs the sun version.

To change the default s/he can either uninstall Openjdk or run in the terminal (after installing sun-java)

```
sudo update-java-alternatives -s java-6-sun
```P.S. I think PO needs to install sun-java6-jdk , sun-java6-bin as well in addition to the packages you listed.

---

### Post by janpol on 2010-11-03
jdk is for developing...don't know about bin.

---

### Post by beew on 2010-11-03
yes jdk is for developing but if you run the update-java-alternatives command without it you will get an error. It probably doesn't matter as long as it changes the default java version(which it probably does) but error message makes me nervous. :)

---

