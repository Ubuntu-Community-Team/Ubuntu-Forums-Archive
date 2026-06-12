---
title: "Create Desktop shortcut for termina ./launch file"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by unclerico on 2008-12-18
Hi, 

I have installed a program (jHeidi, a gui interface for MySQL) and I want to create an Applications menu item for it on my desktop.  I have been able to do that for other files that I start by choosing a file. 

This is what I am doing:  

Edit Menus
   New Menu Item -> Type -Application in Terminal
                    Name "jHeidi"
                    Command "usr/local/jheidi-bin/ ./jheidi"
                    Comment ""

The error I get is "There was an error creating the child process for this terminal."  

I think my question is really, how do I specify the 'command' portion so that I can start this application by cd'ing to the directory and then typing ./jheidi?

Thanks!

---

### Post by Fixman on 2008-12-18
> **unclerico said:**
> Hi, 

I have installed a program (jHeidi, a gui interface for MySQL) and I want to create an Applications menu item for it on my desktop.  I have been able to do that for other files that I start by choosing a file. 

This is what I am doing:  

Edit Menus
   New Menu Item -> Type -Application in Terminal
                    Name "jHeidi"
                    Command "usr/local/jheidi-bin/ ./jheidi"
                    Comment ""

The error I get is "There was an error creating the child process for this terminal."  

I think my question is really, how do I specify the 'command' portion so that I can start this application by cd'ing to the directory and then typing ./jheidi?

Thanks!


```
 Command "/usr/local/jheidi-bin/jheidi" 
```

---

### Post by unclerico on 2008-12-19
Thanks for that response, but that command instruction doesn't work for me.  After changing the command, when I choose the menu item, I see a terminal flash up, but the jheidi program doesn't start.  

There is no error message this time.  Any other ideas?  

Thanks.

(Esta usted de veras en Buenos Aires?  Como va todo?)

---

### Post by Kareeser on 2008-12-19
Open up a terminal session, copy and paste **Fixman**'s command into the terminal, and see if that runs.

If not, there will be an error message to guide you.

---

### Post by unclerico on 2008-12-19
Thanks Kareeser.  No I see the error message is: 

Exception in thread "main" java.lang.NoClassDefFoundError: com/rendion/ajl/AjlScript
Caused by: java.lang.ClassNotFoundException: com.rendion.ajl.AjlScript
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

How can I get this AjlScript?

---

