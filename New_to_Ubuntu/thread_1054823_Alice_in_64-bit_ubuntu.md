---
title: "Alice in 64-bit ubuntu"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Ong on 2009-01-30
I am currently trying to use [Alice]("http://www.alice.org") on my 64-bit ubuntu 8.10 Desktop. I downloaded it from the site. I run the run-alice file from the folder in the terminal. It came up with lots of messages but stopped.This is the results generated.```
attempting to register mp3 capability... 
Registered succesfully
*sys-package-mgr*: processing new jar, '/home/ong/Desktop/Alice/Required/gnu/getopt-1.0.7.jar'
*sys-package-mgr*: processing new jar, '/home/ong/Desktop/Alice/Required/jython-2.1/jython.jar'
*sys-package-mgr*: processing new jar, '/home/ong/Desktop/Alice/Required/lib/alice.jar'
*sys-package-mgr*: processing new jar, '/home/ong/Desktop/Alice/Required/jogl/lib/jogl.jar'
*sys-package-mgr*: processing new jar, '/home/ong/Desktop/Alice/Required/xerces-2_6_2/resolver.jar'
*sys-package-mgr*: processing new jar, '/home/ong/Desktop/Alice/Required/vecmath/lib/ext/vecmath.jar'
*sys-package-mgr*: processing new jar, '/home/ong/Desktop/Alice/Required/xerces-2_6_2/xercesImpl.jar'
*sys-package-mgr*: processing new jar, '/home/ong/Desktop/Alice/Required/xerces-2_6_2/xml-apis.jar'
*sys-package-mgr*: processing new jar, '/home/ong/Desktop/Alice/Required/xerces-2_6_2/xmlParserAPIs.jar'
*sys-package-mgr*: processing new jar, '/home/ong/Desktop/Alice/Required/JMF-2.1.1e/lib/customizer.jar'
*sys-package-mgr*: processing new jar, '/home/ong/Desktop/Alice/Required/JMF-2.1.1e/lib/jmf.jar'
*sys-package-mgr*: processing new jar, '/home/ong/Desktop/Alice/Required/JMF-2.1.1e/lib/mediaplayer.jar'
*sys-package-mgr*: processing new jar, '/home/ong/Desktop/Alice/Required/JMF-2.1.1e/lib/multiplayer.jar'
*sys-package-mgr*: processing new jar, '/home/ong/Desktop/Alice/Required/mp3/lib/ext/mp3plugin.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/charsets.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/rhino.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunpkcs11.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/ext/localedata.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/ext/dnsns.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/ext/gnome-java-bridge.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunjce_provider.jar'
java.lang.UnsatisfiedLinkError: /home/ong/Desktop/Alice/Required/jogl/lib/linux-i586/libjogl_drihack.so: /home/ong/Desktop/Alice/Required/jogl/lib/linux-i586/libjogl_drihack.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1692)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at com.sun.opengl.impl.NativeLibLoader$DefaultAction.loadLibrary(NativeLibLoader.java:78)
	at com.sun.opengl.impl.NativeLibLoader.loadLibrary(NativeLibLoader.java:101)
	at com.sun.opengl.impl.NativeLibLoader.access$100(NativeLibLoader.java:47)
	at com.sun.opengl.impl.NativeLibLoader$3.run(NativeLibLoader.java:141)
	at java.security.AccessController.doPrivileged(Native Method)
	at com.sun.opengl.impl.NativeLibLoader.loadDRIHack(NativeLibLoader.java:139)
	at com.sun.opengl.impl.x11.DRIHack.begin(DRIHack.java:105)
	at com.sun.opengl.impl.x11.X11GLDrawableFactory.<clinit>(X11GLDrawableFactory.java:66)
	at java.lang.Class.forName0(Native Method)
	at java.lang.Class.forName(Class.java:186)
	at javax.media.opengl.GLDrawableFactory.getFactory(GLDrawableFactory.java:111)
	at javax.media.opengl.GLCanvas.<init>(GLCanvas.java:113)
	at javax.media.opengl.GLCanvas.<init>(GLCanvas.java:82)
	at javax.media.opengl.GLCanvas.<init>(GLCanvas.java:75)
	at edu.cmu.cs.stage3.alice.scenegraph.renderer.joglrenderer.OnscreenRenderTarget.getAWTComponent(OnscreenRenderTarget.java:57)
	at edu.cmu.cs.stage3.alice.authoringtool.util.RenderTargetPickManipulator.setRenderTarget(RenderTargetPickManipulator.java:74)
	at edu.cmu.cs.stage3.alice.authoringtool.util.RenderTargetPickManipulator.<init>(RenderTargetPickManipulator.java:45)
	at edu.cmu.cs.stage3.alice.authoringtool.util.RenderTargetMultiManipulator.<init>(RenderTargetMultiManipulator.java:33)
	at edu.cmu.cs.stage3.alice.authoringtool.editors.sceneeditor.CameraViewPanel.renderInit(CameraViewPanel.java:867)
	at edu.cmu.cs.stage3.alice.authoringtool.editors.sceneeditor.SceneEditor.setAuthoringTool(SceneEditor.java:215)
	at edu.cmu.cs.stage3.alice.authoringtool.JAliceFrame.guiInit(JAliceFrame.java:157)
	at edu.cmu.cs.stage3.alice.authoringtool.JAliceFrame.<init>(JAliceFrame.java:71)
	at edu.cmu.cs.stage3.alice.authoringtool.AuthoringTool.mainInit(AuthoringTool.java:456)
	at edu.cmu.cs.stage3.alice.authoringtool.AuthoringTool.<init>(AuthoringTool.java:408)
	at edu.cmu.cs.stage3.alice.authoringtool.JAlice.main(JAlice.java:131)


```I hope you could help me or I will have to use windows. Thanks in advance:popcorn:

---

### Post by T3kG33k on 2009-01-30
Are you talking about American McGee's Alice?

---

### Post by Ong on 2009-01-30
> **T3kG33k said:**
> Are you talking about American McGee's Alice?

No. It is a This one [www.alice.org]("http://www.alice.org")

---

### Post by Arylon on 2009-01-31
What's happening is you have the 64-bit Ubuntu, but Alice is supplying a 32-bit only library. That's what the line below is trying to tell you.
```
java.lang.UnsatisfiedLinkError: /home/ong/Desktop/Alice/Required/jogl/lib/linux-i586/libjogl_drihack.so: /home/ong/Desktop/Alice/Required/jogl/lib/linux-i586/libjogl_drihack.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
```
You can get the 64-bit version of the jogl library at [https://jogl.dev.java.net/](https://jogl.dev.java.net/)

---

### Post by Ong on 2009-01-31
> **Arylon said:**
> What's happening is you have the 64-bit Ubuntu, but Alice is supplying a 32-bit only library. That's what the line below is trying to tell you.
```
java.lang.UnsatisfiedLinkError: /home/ong/Desktop/Alice/Required/jogl/lib/linux-i586/libjogl_drihack.so: /home/ong/Desktop/Alice/Required/jogl/lib/linux-i586/libjogl_drihack.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
```
You can get the 64-bit version of the jogl library at [https://jogl.dev.java.net/](https://jogl.dev.java.net/)

I will do that now. Thanks

---

### Post by npnutn on 2009-03-03
I just tried using the 64-bit jogl libraries on a 64-bit system with no luck.  I did get Alice running on my 32-bit system though.

---

### Post by myolbug on 2009-04-09
I too am trying to run this on 64 bit Ubuntu.  As I am still trying to learn Ubuntu, if anyone has a walk through on this, I would really appreciate it.

---

### Post by graphius on 2009-11-17
I would like to play with Alice as well, so I can keep up with my kids...

---

