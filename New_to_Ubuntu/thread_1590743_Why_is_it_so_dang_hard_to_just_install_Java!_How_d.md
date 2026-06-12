---
title: "Why is it so dang hard to just install Java?! How do I do it?"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by Iniquit-e on 2010-10-08
I tried this line of code I read on a couple different sites:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

And I get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-fonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jre' has no installation candidate
E: Package 'sun-java6-plugin' has no installation candidate
E: Package 'sun-java6-fonts' has no installation candidate
```

Seriously, this has been the number 1 reason I've had thoughts of going back to windows. If the software you need isn't in the Software Center, it's a super complex process to get it and even then it isn't guaranteed to work. Why cant it be as easy as windows? All you have to do there is double click and it basically installs itself. I REALLY want to love Ubuntu, but it's the little things like this that really push me the other way.

---

### Post by beew on 2010-10-08
The sun-java packages are not in the repository by default,--it is not open source,-- Ubuntu uses open-jdk as its default java. To install the Sun (Oracle) version you have to activate some additional repositories, I think it is in Canonical partners but I am not sure. You can activate it simply opening Synaptic, go to settings > repositories > other softwares and check the box. 

 I installed sun-java via a PPA  [https://launchpad.net/~ferramroberto/+archive/java]("https://launchpad.net/%7Eferramroberto/+archive/java")

I like the way some new people always threatening to "go back to windows" when they can't do certain things just because they don't know how. I say good riddance.

---

### Post by Vaphell on 2010-10-08
if a software is not in the software center it means that the creator/owner asks you to jump through the hoops and ubuntu people can't do anything about it. Besides i see sun-java6-* packages just fine
what does **apt-cache search java6** run in terminal say?
my box says:
default-jdk - Standard Java or Java compatible Development Kit
default-jre - Standard Java or Java compatible Runtime
default-jre-headless - Standard Java or Java compatible Runtime (headless)
openjdk-6-jdk - OpenJDK Development Kit (JDK)
openjdk-6-jre - OpenJDK Java runtime, using Hotspot JIT
openjdk-6-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
sun-java6-source - Sun Java(TM) Development Kit (JDK) 6 source files
sun-java6-jre - Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
sun-java6-javadb - Java(TM) DB, Sun Microsystems' distribution of Apache Derby
sun-java6-fonts - Lucida TrueType fonts (from the Sun JRE)
sun-java6-plugin - The Java(TM) Plug-in, Java SE 6
sun-java6-jdk - Sun Java(TM) Development Kit (JDK) 6
sun-java6-demo - Sun Java(TM) Development Kit (JDK) 6 demos and examples
sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)
ia32-sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (32-bit)

edit: 
agreed with the poster above, in my soft center java is in 'partners of canonical'

---

### Post by Iniquit-e on 2010-10-08
Um, ok so now I cant click on OK or press Enter to continue this agreement:

[[IMG]http://img183.imageshack.us/img183/959/screenshotcqa.th.png[/IMG]](http://img183.imageshack.us/i/screenshotcqa.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

Ugh.

---

### Post by desnaike on 2010-10-08
Press the tab button and the ok will highlight and then press enter.

---

### Post by theozzlives on 2010-10-08
I just type

```
sudo apt-get install ubuntu-restricted-extras
```

Installs JAVA, Flash and other friends.

---

### Post by pricetech on 2010-10-08
You don't say which Ubuntu you're running, but in Ubuntu / Edubuntu;

System - Administration - Software Sources

I check everything but Source Code, but the one you want ends with the word "multiverse".

System - Administration - Synaptic Package Manager

Click the Reload button to refresh the listing.

Search for and check sun-java6-plugin which will give you all the Java you need.

Piece of cake actually.

---

### Post by iponeverything on 2010-10-08
> Seriously, this has been the number 1 reason I've had thoughts of going back to windows. 

no harm in going back to windows, it's your choice. Choice is what it is all about.

---

### Post by beew on 2010-10-08
> **theozzlives said:**
> I just type

```
sudo apt-get install ubuntu-restricted-extras
```Installs JAVA, Flash and other friends.

Well, no. You can't install the Sun/Oracle version of Java that way, it will install Open-Jdk though.

---

