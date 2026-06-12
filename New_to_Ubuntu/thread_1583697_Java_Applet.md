---
title: "Java Applet"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by Sgele™ on 2010-09-28
Hi,

Ubuntu is running, drivers working, extra restricted repositories installed.

I do have one slight problem. For some reason, my internet banking does not work. 

It uses a Java applet to start up. The actual page starts, though i don't see the java 'loader' image. Instead of that i see a grey square. This is in Google Chrome by the way, because in FireFox i keep getting the message "No Java 2 SDK, Standard Edition support for internet banking applet!!" (never got it to work under firefox in Windows either)

Now i am wondering what i am doing wrong. Java is installed. Though this page does not allow me to run the applet. In Windows *(sorry for mentioning that word again :() It does work under Chrome.

Any tips or tricks?

For the rest, i'm hooked to Ubuntu, it's blazing fast, and i just love it :)

---

### Post by jtarin on 2010-09-28
post results from the terminal command ```
java -version
```

---

### Post by Sgele™ on 2010-09-28
```
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8.1) (6b18-1.8.1-0ubuntu1)
OpenJDK Server VM (build 16.0-b13, mixed mode)

```

---

### Post by jtarin on 2010-09-28
Your running an "Open" version of Java. There's nothing wrong with that if that is what you want. It will work with a large number of sites however it has been my experience that most banking institutions program there sites to use Sun Java.
Mine:java -version
```
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
```

---

### Post by Sgele™ on 2010-09-28
> **jtarin said:**
> Your running an "Open" version of Java. There's nothing wrong with that if that is what you want. It will work with a large number of sites however it has been my experience that most banking institutions program there sites to use Sun Java.
Mine:java -version
```
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
```

Ok, so i have to get the Sun Java from the Sun website.
I assume then i have to uninstall this 'open' version of Java? :)

---

### Post by jtarin on 2010-09-28
You can find it in the repositories.....or download a .deb package at Sun.

---

### Post by Old_Man_Unix on 2010-09-28
> **Sgele&#8482 said:**
> Ok, so i have to get the Sun Java from the Sun website.
I assume then i have to uninstall this 'open' version of Java? :)

You can get a fairly recent version of Sun Java from the *partner*  repository.  Add that repository to your sources,  and install it as usual.    Doing it that way will enable updates via the Update Manager, whereas if you install it from the Java website  you will have to update it manually.

Yes it is a good idea to remove  the open-source Java  before you install Sun Java. Don't forget to check  that the plug-ins are removed as well.  Most applications that use Java - such as browsers - can be pointed to the last installed version in any case,  but I wouldn't rely on that.

You can only use one RTE and its associated plug-ins  at one time anyway, so unless you are a developer,  keeping multiple versions around serves no purpose.

Very few websites check their operation with anything other than Sun Java so you will often get these incompatibilities - it's just a fact of life.

---

### Post by Sgele™ on 2010-09-28
```
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Server VM (build 16.3-b01, mixed mode)
```

Finally got that done :) Took me a while, but i figured it out.
Now it's the trick to get this working with FireFox or Chrome? 

Firefox keeps fishing to install the IcedTea plugin.

---

### Post by Irony on 2010-09-28
Go to the end of this document;

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Irony on 2010-09-28
Also the manual way of installing is quite straighforward;

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by madmax75 on 2010-09-28
> **Sgele™ said:**
> ```
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Server VM (build 16.3-b01, mixed mode)
```Finally got that done :) Took me a while, but i figured it out.
Now it's the trick to get this working with FireFox or Chrome? 

Firefox keeps fishing to install the IcedTea plugin.

Make sure you installed all of these:

sun-java6-jre
sun-java6-plugin 
sun-java6-fonts

Especially note the **sun-java6-plugin** for the web browser. I myself forgot that one and that's why I didn't get Java on the browser.

---

### Post by Sgele™ on 2010-09-28
> **madmax75 said:**
> Make sure you installed all of these:

sun-java6-jre
sun-java6-plugin 
sun-java6-fonts

Especially note the **sun-java6-plugin** for the web browser. I myself forgot that one and that's why I didn't get Java on the browser.

And you my man...are my hero!
It's working!

I indeed looked over the java6-plugin. Installed that one, removed icedtea..and now i can bank the hell out of anything..if only i had some money :P

Thank you so much :)

---

### Post by madmax75 on 2010-09-28
> **Sgele™ said:**
> And you my man...are my hero!
It's working!

I indeed looked over the java6-plugin. Installed that one, removed icedtea..and now i can bank the hell out of anything..if only i had some money :P

Thank you so much :)

Heh, I have indeed battled with Java myself (see my signature). I even once had to install it manually from the Java website.

You cannot imagine *the horror*... :D

---

### Post by jtarin on 2010-09-28
You can become quite the expert in no time.

---

