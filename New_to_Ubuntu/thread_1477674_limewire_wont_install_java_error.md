---
title: "limewire wont install java error"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by ashora on 2010-05-09
im trying to install lime wire on my comp but i get this error on the package installer... "Error: Dependency is not satisfiable: sun-java6-jre|icedtea-java7-jre|sun-java6-jdk|icedtea-java7-jdk"....im new to this any advise? i

---

### Post by Mze on 2010-05-09
If you are running 10.04, here's a [how to]("http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html")

---

### Post by redbook4574 on 2010-05-09
> **ashora said:**
> im trying to install lime wire on my comp but i get this error on the package installer... "Error: Dependency is not satisfiable: sun-java6-jre|icedtea-java7-jre|sun-java6-jdk|icedtea-java7-jdk"....im new to this any advise? i

Also Try Frostwire.

---

### Post by barkej on 2010-05-09
+1 for frostwire.

---

### Post by ashora on 2010-05-09
i tryed frost wire and got an error as well..i tryed what you gave me ..the first command didnt work..the second one worked fine but when i entered the tired on i got this 

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

---

### Post by ashora on 2010-05-09
i installed ubuntu 9.10 instead everything is working fine :) no more windows vista for me yay!

---

### Post by Powerman2442 on 2010-05-10
> **Mze said:**
> If you are running 10.04, here's a [how to]("http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html")

I hope I'm not out of place by posting more on this thread but I am having the same issue while trying to install Frostwire on 10.04. Like I said I am using 10.04 (clean install) and trying to install Frostwire 4.20.6 via the package installer. I get the error "Error: Dependency is not satisfiable: sun-java6-jre". I followed that guide located [here]("http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html").

I'm running into problems on the first command. Here is a copy & paste from terminal. 

derek@derek-desktop:~$ sudo add-apt-repository “deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner”
Error: need a repository as argument

For the heck of it I did "sudo apt-get update" and then tried to install the java packages and this is what I got.

derek@derek-desktop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

Any ideas?

Thanks

---

### Post by ashora on 2010-05-11
thats what i kept getting as well!!  go to applications then the software center see if.. sun  java 6 runtime ..is there..thats how i installed it on 9.10..i thought i did that on 10.04 but i might have did openjdk java insted oops

---

### Post by marshmallow1304 on 2010-05-11
I don't know why that command isn't working, but this will work instead.  Go to System->Administration->Software Sources.  On the "Other Software" tab, check the box next to > [http://archive.canonical.com/](http://archive.canonical.com/) ubuntu lucid parter

Then continue with
```
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by adam22 on 2010-05-11
I got the same error. I installed the Ubuntu Restricted Extras package as always which used to install JRE as well, but did not see any prompt this time around. With the error, it's likely that package either does not contain JRE, or there's some bug that is not installing it correctly...

---

### Post by ashora on 2010-05-11
maybe this might help? [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by QIII on 2010-05-11
While ashora's suggested method will work, the packages are in the partner repo and you CAN install it.

The problem is that your command includes non-ascii quotation marks.

Try


```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```

---

### Post by Kafubie on 2010-05-11
What's wrong with torrents?

---

