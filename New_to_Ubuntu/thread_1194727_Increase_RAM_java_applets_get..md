---
title: "Increase RAM java applets get."
date: 2009-06-23
forum: New to Ubuntu
---

### Post by CJ Master on 2009-06-23
(Note: I'm currently using Arch Linux, I however believe that the instructions should be the same for Ubuntu.)

I'm currently using the propriety version of Java because the F/OSS version doesn't work with the games I play. How do I increase the amount of RAM that java web applets get? I want to let them get around 400 megabytes of ram.

---

### Post by QIII on 2009-06-23
The default amount of memory allotted to the JVM is pretty small.  I think it is 2MB.

Depending on how much memory your application needs to run, it sounds like you may want to increase the size of the memory allocation pool.

Here is the Java documentation:  [http://java.sun.com/j2se/1.5.0/docs/tooldocs/solaris/java.html](http://java.sun.com/j2se/1.5.0/docs/tooldocs/solaris/java.html)

In the terminal, you want to type "java" (no quotes) followed by a space and then "-Xmx" with some amount of memory space. Please do a search for Xmx and read CAREFULLY.

---

### Post by CJ Master on 2009-06-23
> **QIII said:**
> The default amount of memory allotted to the JVM is pretty small.  I think it is 2MB.

Depending on how much memory your application needs to run, it sounds like you may want to increase the size of the memory allocation pool.

Here is the Java documentation:  [http://java.sun.com/j2se/1.5.0/docs/tooldocs/solaris/java.html](http://java.sun.com/j2se/1.5.0/docs/tooldocs/solaris/java.html)

In the terminal, you want to type "java" (no quotes) followed by a space and then "-Xmx" with some amount of memory space. Please do a search for Xmx and read CAREFULLY.

Actually it's 64mb of ram. Thanks for the link, though it's for apps, not applets. Or if it's both, I can't see how to run web applets. It's for games on [www.funorb.com](www.funorb.com) btw.

---

### Post by QIII on 2009-06-23
Sorry.  I guess RTFQ applies...

Yeah.  2Mb is the default minimum.  Too much in old brain to remember.

How are you accessing the games?  Through a browser?  Which one?  Do the games work at all?  Which JRE do you have installed?

---

### Post by CJ Master on 2009-06-23
Heh - it's ok. I make forgetting look like an art.

Browser, firefox, yes, the latest one from sun.

---

### Post by QIII on 2009-06-23
Disregard last...
I see the yes now.

What behavior are you seeing?

---

### Post by CJ Master on 2009-06-23
> **QIII said:**
> Disregard last...
I see the yes now.

What behavior are you seeing?

I don't get the question, but if your asking why I want to allocate more ram it's so my games doesn't have to constantly uncompress images.

---

### Post by QIII on 2009-06-23
I guess the implication is that your performance is slow?

(Since you pointed out that you are talking about applets, I'm really curious.  In some older JREs, the problem was that applets used too much memory.)

Have you tried to see what happens with a browser like Konquerer or Epiphany?

---

### Post by Nostalos on 2009-06-23
Under the System | Preferences (assuming GNOME) open the "Sun Java 6 Plugin Control Panel"

Click the Java Panel and the view button under "Java Applet Runtime Settings"

In the "Java Runtime" box just add -Xmx400m or 300m or whatever you need.

---

### Post by CJ Master on 2009-06-23
Interesting. I didn't see any options for java.

---

### Post by Nostalos on 2009-06-23
I "think" its under /usr/jvm/sun-jre-6/bin/ControlPanel.    Don't have my system available to me at the moment.

---

### Post by QIII on 2009-06-23
Go to System | Preferences | Sun Java 6 Plugin Control Panel.

Click on the Java tab, then View in Java Applet Runtime Settings.

You can see where I made changes.

You learn something new every day!  That's what makes this fun.

---

### Post by CJ Master on 2009-06-25
Well there's the problem, there's no "Sun Java 6 Plugin Control Panel" for me. In fact, none of the menu items mentioned Java at all.

---

### Post by QIII on 2009-06-26
Hmmmm...

I'll have to look around.  I have it.  But I also have Netbeans and the JDK installed on all my machines because I develop in Java.

That may be why I have it.

---

