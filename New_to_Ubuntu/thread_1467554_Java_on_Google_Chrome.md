---
title: "Java on Google Chrome"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Vistz on 2010-04-30
I just upgraded to lucid and now my java plugin won't work on Google Chrome. However, it works fine in Firefox.

---

### Post by tom.swartz07 on 2010-04-30
> **Vistz said:**
> I just upgraded to lucid and now my java plugin won't work on Google Chrome. However, it works fine in Firefox.

What version of the Java plugin are you using?


Try following the java guide in my sig. Its a bit of copy and paste action, but you will be assured to have the most up to date version!

---

### Post by Vistz on 2010-04-30
This was copied directly from the terminal


```
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8) (6b18-1.8-0ubuntu1)
OpenJDK Server VM (build 14.0-b16, mixed mode)

```

---

### Post by suryaccnamcse on 2010-04-30
Just try to reinstall the latest java .deb package or you can uninstall  java and again try to reinstall the java through terminal, it will work. I am using 10.04 with the chrome browser and the java works perfectly...

---

### Post by QIII on 2010-04-30
Hang on here, folks.

Uninstall OpenJDK first.

Although OpenJDK should be fine for most people, Chrome may not like it

The latest Sun Java (Update 20) is available in the partner repository for Lucid.  No need any longer to follow instructions from the web.  Just activate the install it through Synaptic.

---

### Post by Vistz on 2010-04-30
> **QIII said:**
> Hang on here, folks.

Uninstall OpenJDK first.

Although OpenJDK should be fine for most people, Chrome may not like it

The latest Sun Java (Update 20) is available in the partner repository for Lucid.  No need any longer to follow instructions from the web.  Just activate the install it through Synaptic.

I uninstalled OpenJDK. Then I ran this in the terminal:

```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```

I think that I may have also accidentally uninstalled a few necessary Java packages in the process. And now Java doesn't work in either Firefox either

---

### Post by QIII on 2010-04-30
You have added the repository, but have not yet added Java itself.

Go to Synaptic and search for "sun-java6" (no quotes)

Install sun-java6-fonts, sun-java6-bin, sun-java6-jre and sun-java6-plugin.  If you are interested in programming in Java, also install sun-java6-jdk.

---

### Post by Vistz on 2010-04-30
That did it. Thank you

---

### Post by iburroughs on 2010-08-26
Finally works for me also. I followed this thread several times and it wouldn't work. Then I restarted Google Chrome and it works perfectly. OK I'm a big dummy but thanks once again for the help.

---

