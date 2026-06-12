---
title: "firefox java plugin update, how?"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by infestor on 2009-11-20
i have installed **Version 6 Update 17, **but how can i show it to firefox's java plugin? also i dont know in which directory the plugin is.

---

### Post by infestor on 2009-11-20
i am talking about the symbolic links

---

### Post by QIII on 2009-11-20
I recommend this guy's method of installation and use of the plugin.

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by infestor on 2009-11-20
i have found files that contain *libjavaplugin*:

[IMG]http://img.photobucket.com/albums/v185/darkrift/Screenshot-4FilesFound-SearchforFil.png[/IMG]

where do i go from here?
how can i update jvm? also no *libjavaplugin_oji.so* link under firefox or mozilla folder :(

---

### Post by QIII on 2009-11-21
I would put a bookmark on the link I gave you.  To update to future updates of Java, you will have to follow the instructions again (replacing file names, of course).  He has already updated them a couple of times since he first posted the instructions.  Canonical does not plan to keep up with Sun anymore.  Instead, they are focusing on OpenJDK.  (In my honest opinion, I think they are making a big mistake!)

Follow his instructions from the top and to the letter.  You can cut and paste his instructions.  That's what I have been doing and it works perfectly.

I'm not blowing you off, I'm just saying that we shouldn't reinvent the wheel.  The blogger has all the details in a nice, easy-to-follow tutorial.

The JVM is installed automatically.

```
java -version
```should show (depending on whether you have 32 or 64 bit):

```
java version "1.6.0_17"
Java(TM) SE Runtime Environment (build 1.6.0_17-b04)
Java HotSpot(TM) 64-Bit Server VM (build 14.3-b01, mixed mode)
```

---

