---
title: "Java"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by calk on 2009-09-28
Hi, I recently installed ubuntu and I am having problems with getting java, I went to the java site to download but it only had .bin files and my ubuntu didnt have a path set for .bin files. so i dont know what to tell it to use to read the .bin files.

---

### Post by nhasian on 2009-09-28
in a terminal type:

```
sudo apt-get install ubuntu-restricted-extras
```

during installation it should ask you to accept the java license and continue installing.

---

### Post by dvn3ch on 2009-09-28
> **calk said:**
> Hi, I recently installed ubuntu and I am having problems with getting java, I went to the java site to download but it only had .bin files and my ubuntu didnt have a path set for .bin files. so i dont know what to tell it to use to read the .bin files.

You must first install an IDE like NetBeans or jGrasp to learn / develop in Java.

I highly suggest to slow down and pick up a book at BAM and read how to get started in Java.  If you go into this half-cocked you will not get the real experience of Java and will probably be disappointed after awhile.

---

### Post by 3rdalbum on 2009-09-28
> **calk said:**
> Hi, I recently installed ubuntu and I am having problems with getting java, I went to the java site to download but it only had .bin files and my ubuntu didnt have a path set for .bin files. so i dont know what to tell it to use to read the .bin files.

Use the Ubuntu repositories to download software wherever possible, rather than go scooting around the web. You can access the Ubuntu repositories through the Synaptic Package Manager program, where even Java is just a couple of clicks away.

To answer your question, files with ".bin", ".run" or sometimes ".sh" are binary installers, similar to what you might have used on Windows. The Linux security system demands that you give those files execute permission in Nautilus or in the terminal before they can be run. As they are installers, you need to run them with root privileges so they have the ability to access the system-wide locations. And they usually only run in the terminal, so you must run them in the terminal.

You can do all this by opening the terminal and typing "sudo -i" and pressing Enter (type your password if it asks you to and press Enter). Then type "chmod a+x " (with a trailing space), drag the file to the terminal, and press Enter. Then drag the file to the terminal once more and press Enter.

Stick to the repositories wherever possible. It's safer and easier, and does not require you to open a terminal.

---

### Post by Mighty_Joe on 2009-09-28
> **dvn3ch said:**
> You must first install an IDE like NetBeans or jGrasp to learn / develop in Java.


I think OP's trying to *use *Java, not program with it. And if he were trying to program with it, I think it would be easier to learn using a [programmer's text editor]("http://www.jedit.org/") as opposed to an IDE.  Using an editor lets the budding programmer focus on learning the language instead of trying to figure out an IDE's particularities.

---

### Post by credobyte on 2009-09-28
```
sudo apt-get install sun-java6-jre sun-java6-plugin

```

---

