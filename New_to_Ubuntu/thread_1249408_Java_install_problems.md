---
title: "Java install problems"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by Gregz on 2009-08-25
I downloaded the latest java to see if it would fix my firefox freezing.

 Well I screwed it up. I think I installed it on my desktop. How can I move it where it goes?

Firefox would hang on java script and I would have to force quit.

---

### Post by Mighty_Joe on 2009-08-25
> **Gregz said:**
> I downloaded the latest java. . .Firefox would hang on java script 

[Javascript is not Java]("http://www.ericgiguere.com/articles/javascript-is-not-java.html").  Two completely different languages.

As for Java, the Sun JDK and JRE are in the Ubuntu repository.  No need to install the binary yourself.  Use Synaptic or apt-get to install sun-java6-jre.  [see here for more info]("https://help.ubuntu.com/community/Java")

---

### Post by Gregz on 2009-08-25
Why do I get this-

```
james@Catfish:~$ sudo update-java-alternatives -s java-6-sun
[sudo] password for james: 
No alternatives for appletviewer.
No alternatives for apt.
No alternatives for extcheck.
No alternatives for HtmlConverter.
No alternatives for idlj.
No alternatives for jar.
No alternatives for jarsigner.
No alternatives for javac.
No alternatives for javadoc.
No alternatives for javah.
No alternatives for javap.
No alternatives for java-rmi.cgi.
No alternatives for jconsole.
No alternatives for jdb.
No alternatives for jhat.
No alternatives for jinfo.
No alternatives for jmap.
No alternatives for jps.
No alternatives for jrunscript.
No alternatives for jsadebugd.
No alternatives for jstack.
No alternatives for jstat.
No alternatives for jstatd.
No alternatives for native2ascii.
No alternatives for rmic.
No alternatives for schemagen.
No alternatives for serialver.
No alternatives for wsgen.
No alternatives for wsimport.
No alternatives for xjc.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/java-rmi.cgi
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/xjc
Using '/usr/lib/jvm/java-6-sun/jre/bin/ControlPanel' to provide 'ControlPanel'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java_vm' to provide 'java_vm'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/javaws' to provide 'javaws'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/jcontrol' to provide 'jcontrol'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/jexec' to provide 'jexec'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/keytool' to provide 'keytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/orbd' to provide 'orbd'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/pack200' to provide 'pack200'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/policytool' to provide 'policytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmid' to provide 'rmid'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry' to provide 'rmiregistry'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/servertool' to provide 'servertool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/tnameserv' to provide 'tnameserv'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/unpack200' to provide 'unpack200'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so' to provide 'firefox-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so' to provide 'iceape-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so' to provide 'iceweasel-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so' to provide 'midbrowser-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so' to provide 'mozilla-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so' to provide 'xulrunner-1.9-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so' to provide 'xulrunner-javaplugin.so'.
james@Catfish:~$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.
```

---

### Post by Gregz on 2009-08-25
ok it's not the java then it must be firefox. On some BUT not all sites I go to firefox freezes screen turns gray and I have to force quit firefox.

If I undo plug in for firefox it's better but still locks up. So is this a java script problem or  firefox problem????

---

### Post by Mighty_Joe on 2009-08-25
> **Gregz said:**
> Why do I get this-

```
james@Catfish:~$ sudo update-java-alternatives -s java-6-sun
[sudo] password for james: 
No alternatives for appletviewer.
. . .

```

The JRE, which is what you have installed, does not have Java development utilities like appletviewer, jar, javac and so on.  I would speculate the dump merely states that there are no alternatives for those utilities(which aren't needed if you aren't writing Java code).

> **Gregz said:**
> 
james@Catfish:~$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.[/CODE]

That looks fine.  
I've seen several posts about Firefox hanging.  Search the forum or Launchpad and see if any match the symptoms you are seeing.

---

