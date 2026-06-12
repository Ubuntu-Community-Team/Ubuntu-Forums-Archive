---
title: "Having trouble installing DumpHD"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by Omegaxis on 2010-03-02
I've extracted the DumpHD-0.61 onto my desktop and am trying to compile.
Unfortunately nothing seems to work, I've tried:

```
omega@Omegaxis:~/Desktop/dumphd-0.61$ ./configure
bash: ./configure: No such file or directory

```

```
omega@Omegaxis:~/Desktop/dumphd-0.61$ sudo sh DumpHD.jar
DumpHD.jar: 1: Syntax error: "(" unexpected

```

```
omega@Omegaxis:~/Desktop/dumphd-0.61$ java -jar DumpHD.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.10)
   at java.awt.EventQueue.isDispatchThread(libgcj.so.10)
   at java.awt.EventQueue.invokeAndWait(libgcj.so.10)
   at javax.swing.SwingUtilities.invokeAndWait(libgcj.so.10)
   at dumphd.gui.Manager.<init>(Manager.java:161)
   at dumphd.core.DumpHD.main(DumpHD.java:1032)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.10)
   at java.lang.Runtime.loadLibrary(libgcj.so.10)
   at java.lang.System.loadLibrary(libgcj.so.10)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.10)
   at java.lang.Class.initializeClass(libgcj.so.10)
   at java.lang.Class.forName(libgcj.so.10)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.10)
   ...5 more

```

I'm running 9.10 amd64

---

### Post by Rhubarb on 2010-03-02
Hi there,

DumpHD does not need to be compiled, it is a java application that just needs to be executed (your last attempt using *java -jar DumpHD.jar* should have worked.

I'm not sure why it didn't work for you, I've managed to get DumpHD up and running, but am unable to get it to do any work, as I need to do some more reading about a few other applications that complement DumpHD.

Have a look at the following guide that may help point you in the right direction:
[Playing Blu-Ray and HD DVD Video]("https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD")

I have bought a BluRay disc here and am wishing to be able to watch the content in Ubuntu, and am also having a few difficulties.

I'll let you know if I later come across anything that may help us out.
In the mean time I do hope someone can shed some more light on getting DumpHD to help us play our BluRay discs.

---

