---
title: "How do I install the Java JDK?"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by anthony62490 on 2009-07-06
OK, I've installed
sun-java6-bin
sun-java6-jdk
sun-java6-jre
sun-java6-plugin

Now, since I'm not seeing any new programs, I am going to assume that the JDK is not completely installed. 

> java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu7)
OpenJDK Client VM (build 14.0-b08, mixed mode, sharing)


I think I need to run localepurge to proceed, but that is a pretty intimidating program. Any idea what I need to do next?

---

### Post by sdlynx on 2009-07-06
to program in Java you're going to need an IDE I believe. Eclipse would do it. ```
sudo aptitude install eclipse
```

---

### Post by kpkeerthi on 2009-07-06
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by anthony62490 on 2009-07-06
@Sdlynx
Oh. Thank you very much. I am back in familiar territory. Now I'm going to pass out for a few hours and explore this new toy tomorrow. Thank you.

@Kpkeerthi
Thanks. Was actually looking for a developers kit, but I'll keep this bookmarked just in case.

---

### Post by credobyte on 2009-07-06
> **sdlynx said:**
> to program in Java you're going to need an IDE I believe. Eclipse would do it. ```
sudo aptitude install eclipse
```

IDE is NOT necessary to program in Java ! It can be done in any text editor & compiled from command line, unless you need something more advanced ( plugins, macros, etc. ).

---

### Post by sdlynx on 2009-07-06
> **credobyte said:**
> IDE is NOT necessary to program in Java ! It can be done in any text editor & compiled from command line, unless you need something more advanced ( plugins, macros, etc. ).

good point
I just figured it would be easy with a GUI (its also wut I use).

---

### Post by sadaruwan12 on 2009-07-06
When you install java you want see any new program installed in to your system due to java is just a programing platform. If you want to use that platform to program you can use any text editor as your IDE but if you want an high end GUI then eclips is good or other wise you can google and see is there any other better options available.

---

### Post by credobyte on 2009-07-06
> **sadaruwan12 said:**
> When you install java you want see any new program installed in to your system due to java is just a programing platform. If you want to use that platform to program you can use any text editor as your IDE but if you want an high end GUI then eclips is good or other wise you can google and see is there any other better options available.

Correction - you'll see [COLOR=Blue]Java[/COLOR] under [COLOR=Blue]Applications / Programming[/COLOR] ;)

---

### Post by sdlynx on 2009-07-06
> **credobyte said:**
> Correction - you'll see [COLOR=Blue]Java[/COLOR] under [COLOR=Blue]Applications / Programming[/COLOR] ;)

I don't see that under Applications > Programming for me...

---

### Post by diafanos on 2009-07-06
> **anthony62490 said:**
> OK, I've installed
sun-java6-bin
sun-java6-jdk
sun-java6-jre
sun-java6-plugin

Now, since I'm not seeing any new programs, I am going to assume that the JDK is not completely installed. 



I think I need to run localepurge to proceed, but that is a pretty intimidating program. Any idea what I need to do next?


Now even though you have installed sun jdk, you are still using Open JDK as the default one.
If you would like to set sun jdk as the default then run:
> sudo update-alternatives --config java 

and select the one you prefer.

Also under System -> Preferences, there will (probably) appear two new entries:
1. Sun Java 6 Policy Tool
2. Sun Java 6 Plugin Control Panel

btw, java has a command-line-only version. There is not any "program" associated with it, that you can find under Application menu.
If you want to install Eclipse, don't use the one in repositories, cause it's too old. Go get the new version (galileo - 3.5) from the [[COLOR="RoyalBlue"]eclipse site[/COLOR]]("http://www.eclipse.org").

---

### Post by anthony62490 on 2009-07-06
@ Diafanos

Sweet. That helps alot. Thanks.

---------

As for the text editor, I think I would be much more comfortable using a GUI for day-to-day use. I'll learn to use the text editor method also, though. I'll need help catching bugs and the like.

Thank you guys so much. You've all been a lot of help.

---

