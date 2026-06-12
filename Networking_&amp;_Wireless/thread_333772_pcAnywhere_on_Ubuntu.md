---
title: "pcAnywhere on Ubuntu"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by vrod74 on 2007-01-07
Has anyone ever successfully installed Linux/Mac pcAnywhere version on Ubuntu Platform? I tried installing on Edgy this morning and it doesn't run at all. I do have the latest Java runtime  and I followed all the steps given by symantec, but no go for me. 

My job still uses this for our windows machines, so i have to live with it. Grrrrr! :twisted:

---

### Post by rickatnight11 on 2007-01-09
Well I got it to install just fine with their instructions (pcAnywhere 12.0) by installing Java, and then running the Java command from the Cross Platform folder, and although everything installed fine, when I try to run it like it instructs I get the following error:
```
rickatnight11@Fuzztop:/usr/bin$ ./pcAnywhere
exec: 7: /bin/bash2: not found
```

---

### Post by billmeek on 2007-03-22
rickatnight11,

I had the same issue using pcAnywhere 12.1 beta.  Edit the file /usr/bin/pcAnywhere and change the first line from:

```
#!/bin/sh
```

to: 

```
#!/bin/bash
```

You can then start pcAnywhere correctly.  I've used the remote, including file transfer, but as of yet have not tested the host.

---

### Post by tombott on 2007-06-12
I am trying to install this at the moment but keep getting the following error:

JVM not found

I have Java 6 installed, so not sure what to try next!

Copy of install log:
```

(12-Jun-2007 14:09:03), Install, com.installshield.product.service.product.PureJavaProductServiceImpl$Installer, err, ProductException: (error code = 601; message="JVM not found")
STACK_TRACE: 8
ProductException: (error code = 601; message="JVM not found")
	at com.installshield.product.actions.JVMResolution.install(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallProduct.checkUninstallerJVMResolution(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallProduct.install(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$Installer.execute(Unknown Source)
	at com.installshield.wizard.service.AsynchronousOperation.run(Unknown Source)
	at java.lang.Thread.run(Thread.java:619)

(12-Jun-2007 14:10:40), Install, com.installshield.product.service.product.PureJavaProductServiceImpl$Installer, err, ProductException: (error code = 601; message="JVM not found")
STACK_TRACE: 8
ProductException: (error code = 601; message="JVM not found")
	at com.installshield.product.actions.JVMResolution.install(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallProduct.checkUninstallerJVMResolution(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallProduct.install(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$Installer.execute(Unknown Source)
	at com.installshield.wizard.service.AsynchronousOperation.run(Unknown Source)
	at java.lang.Thread.run(Thread.java:619)

(12-Jun-2007 14:20:15), Install, com.installshield.product.service.product.PureJavaProductServiceImpl$Installer, err, ProductException: (error code = 601; message="JVM not found")
STACK_TRACE: 8
ProductException: (error code = 601; message="JVM not found")
	at com.installshield.product.actions.JVMResolution.install(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallProduct.checkUninstallerJVMResolution(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallProduct.install(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$Installer.execute(Unknown Source)
	at com.installshield.wizard.service.AsynchronousOperation.run(Unknown Source)
	at java.lang.Thread.run(Thread.java:619)
```

---

### Post by tombott on 2007-06-12
Ok I got it to install now.

Did the following:

```
sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 
```

Chose 3 then:

```
sudo java -jar SetupLinuxMac.jar
```

The setup then completed without any errors

---

### Post by Josiah.Allen on 2007-06-14
I was having these problems and tombott's solution worked.  However, I can't get the pcAnywhere host to work.  I can connect to other hosts though.  

Anyone else have issues getting the hosting to work?

---

### Post by plsanz on 2007-07-17
The host option fails because it doesn't find libXm.so.3

I install libmotif3 via Synaptic and then pcAnywhere works.

---

### Post by vrod74 on 2007-11-22
@tombott

Your suggestion to put JVM on my path worked.

@billmeek

I had the same problem when executing from /user/bin/pcAnywhere , and your suggestion  worked. 


I really don't need to run pcAnywhere as host on Ubuntu, I just need to connect to other pcAnywhere computers. So I'm really happy with this.  Thanks a lot guys.

vrod74

---

### Post by vdvleon on 2008-01-05
I have another question. I want to auth with PAM. I run naturally Ubuntu. Have someone a answer?

BTW, thnx for the help above:P

---

### Post by popiculo on 2008-02-07
I have both java 5 & 6 installed and when i run: 
```
sudo update-alternatives --config java
```

i only get these two:
```
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

```

if i type in:
```
sudo update-java-alternatives --list
```

i get
```

java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-6-sun 63 /usr/lib/jvm/java-6-sun

```

finally trying to set java to 1.5.0 gets me this 
```
sudo update-java-alternatives --set java-1.5.0-sun
Using `/usr/lib/jvm/java-1.5.0-sun/bin/appletviewer' to provide `appletviewer'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/apt' to provide `apt'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/extcheck' to provide `extcheck'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/HtmlConverter' to provide `HtmlConverter'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/idlj' to provide `idlj'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jarsigner' to provide `jarsigner'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jar' to provide `jar'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javac' to provide `javac'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javadoc' to provide `javadoc'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javah' to provide `javah'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javap' to provide `javap'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/java-rmi.cgi' to provide `java-rmi.cgi'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jconsole' to provide `jconsole'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jdb' to provide `jdb'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jinfo' to provide `jinfo'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jmap' to provide `jmap'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jps' to provide `jps'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jsadebugd' to provide `jsadebugd'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jstack' to provide `jstack'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jstatd' to provide `jstatd'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jstat' to provide `jstat'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/native2ascii' to provide `native2ascii'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/rmic' to provide `rmic'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/serialver' to provide `serialver'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/ControlPanel' to provide `ControlPanel'.
update-alternatives: Cannot find alternative `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java'.

Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java_vm' to provide `java_vm'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/javaws' to provide `javaws'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/keytool' to provide `keytool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/orbd' to provide `orbd'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/pack200' to provide `pack200'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/policytool' to provide `policytool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/rmid' to provide `rmid'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/rmiregistry' to provide `rmiregistry'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/servertool' to provide `servertool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/tnameserv' to provide `tnameserv'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/unpack200' to provide `unpack200'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `firefox-javaplugin.so'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `iceape-javaplugin.so'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `iceweasel-javaplugin.so'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `midbrowser-javaplugin.so'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `mozilla-javaplugin.so'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `xulrunner-javaplugin.so'.

```

im at a lost. anyone have any idea?

---

### Post by cejack on 2008-06-16
When I run the following command:

sudo java -jar SetupLinuxMac.jar

I get the following error messages:

WARNING: could not delete temporary file /tmp/ismp002/5723167
WARNING: could not delete temporary file /tmp/ismp002/7113152


Any ideas on what's going on here?  How do I solve this problem?

---

