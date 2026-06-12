---
title: "Java plug in wont work"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by AlfyBoy on 2009-07-11
Since last update of firefox to 3.0.11, java stoped working...

when I do 

```
java -version
```

it gives

```
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Client VM (build 14.0-b16, mixed mode, sharing)
```

If I do on terminal:

```
sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin
```

It tells me everything is properly installed...

I even have tried out to make a link to the java plugin with...

```
cd /usr/lib/mozilla/plugins
```

```
sudo ln -sfn /usr/lib/jvm/java-6-sun-1.6.0.14/jre/plugin/i386/ns7/libjavaplugin_oji.so
```

No luck.

What can i do?

Thanks in advance.

---

### Post by ajgreeny on 2009-07-11
You are running a later version of java to me, but I have the same problem, which I was not aware of until now.  It worked a few weeks ago with no problem, so what is going on?

java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) Client VM (build 11.3-b02, mixed mode, sharing)

EDIT:
Being disappointed that java plugin was not working i have just reinstalled it and all is well again.  That may work for you as well.

---

### Post by AlfyBoy on 2009-07-11
> **ajgreeny said:**
> EDIT:
Being disappointed that java plugin was not working i have just reinstalled it and all is well again.  That may work for you as well.

Thanks, I have just reinstalled it, and no luck, then I even tried to reinstall the hole java jre, still no luck!. :confused:

---

### Post by Najand on 2009-07-11
Check if it exists in Firefox Add-ons and if it is enabled there or not.
Firefox > Tools > Add-ons > plugins > JAVA(TM) plug-in 1.6.0_14

---

### Post by AlfyBoy on 2009-07-13
> **Najand said:**
> Check if it exists in Firefox Add-ons and if it is enabled there or not.
Firefox > Tools > Add-ons > plugins > JAVA(TM) plug-in 1.6.0_14

Thanks... I've cheked and it is right there, the problem is that it doesen't work :(

---

