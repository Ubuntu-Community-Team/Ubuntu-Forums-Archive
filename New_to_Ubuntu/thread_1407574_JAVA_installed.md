---
title: "JAVA installed?"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by bob brazie on 2010-02-15
Ubuntu 9.10.

Will JAVA work in Ubuntu 9.10?

How do I check to see if JAVA is installed?

If it's not how do I install it?

Thanks in advance, Bob.

---

### Post by mk1w86 on 2010-02-15
Have a look here:

[http://www.ubuntugeek.com/install-java-runtime-environment-jre-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/install-java-runtime-environment-jre-in-ubuntu-9-10-karmic.html)

or you can run

```
sudo aptitude install ubuntu-restricted-extras
```

which will install many non free packages such as codecs, flash and java. ;)

---

### Post by SemiBuz on 2010-02-15
```
sudo apt-get install sun-java6-jre sun-java6-plugin

```

---

### Post by Xarver on 2010-02-15
I suggest installing openjdk as it's open source and works pretty much exactly the same.

---

### Post by slakkie on 2010-02-15
> **Xarver said:**
> I suggest installing openjdk as it's open source and works pretty much exactly the same.

OpenJDK is not suppored by some applications eg Android. I'd suggest to use Sun's Java.

---

### Post by bob brazie on 2010-02-15
Thanks I ran it in a terminal but when I came to the agreement I couldn't find a way to click on the OK. Either with the mouse or by using the keyboard enter command.

---

### Post by bob brazie on 2010-02-15
I found several Java installs in the applications/software center but I don't know which one is the one I am looking even after reading their explanations. <g>

Any help here too? 

Thanks, Bob.

---

### Post by bob brazie on 2010-02-15
This is what it looks like.

---

### Post by Redmage913 on 2010-02-15
how about hitting the tab key to see if the OK can be highlighted?  also, hitting the o key might work too, something I remember from the old win3.1 days.

---

### Post by adam814 on 2010-02-15
+1

Pretty sure it's the tab key.

---

### Post by bob brazie on 2010-02-15
What a memory! That did the trick!

I thought that would add the Plugins for Firefox but it didn't.

Any ideas on how to do that?

---

### Post by adam814 on 2010-02-15
Did you install Sun Java?  I'm not sure if OpenJDK has a firefox plugin, although in all fairness I haven't really looked.

If you installed Sun Java you just need to make a symlink to get your plugin working.
```
find /usr/lib/jvm -name libnpjp2.so
```
Hopefully that finds at least one file.  Note the path to it, you'll need it.
```
sudo ln -s <path-you-just-found> /usr/lib/mozilla/plugins/libnpjp2.so
```

That should do the trick

---

### Post by bob brazie on 2010-02-16
Thanks to all!!

Everything is working as billed.

---

