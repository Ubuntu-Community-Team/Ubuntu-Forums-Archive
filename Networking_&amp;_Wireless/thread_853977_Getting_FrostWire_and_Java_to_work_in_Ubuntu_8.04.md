---
title: "Getting FrostWire and Java to work in Ubuntu 8.04"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by gluonman on 2008-07-09
Greetings.
   Since upgrading to 8.04, I've discovered not everything is running with perfect smoothness. I've managed to create fixes and workarounds for almost all of my problems, but the following is a list of the issues surrounding my seemingly last truly annoying problem.

   1) I can't seem to get Java working... period. In my preferences in FireFox 3.0, I've enabled Java. I have also downloaded sun-java6-jre and other java plugins from so many sources recommended by various posts, etc. I've uninstalled and reinstalled the standard Ubuntu installation of SunJava. None of this has worked.

   2)
      a) The consequences of not having Java working include not being able to run FrostWire, for which the terminal feedback is:

```
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading FrostWire:
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
	at com.limegroup.gnutella.gui.Main.main(Main.java:39)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)
```

      b) And the other consequence to not having java working correctly is that I am unable to access many applications and games online. For example, I cannot play pool at games.yahoo.com. If I reach a website where I try to play a java-based game and the plugin menu drops down asking me to install the missing plugins, I click on it and it can never find any suitable plugin.

   I realize I'm not alone in facing Java-related problems in 8.04. There are complaints all over the place. But has anyone run into these problems who have fixed them for themselves? If so, I want those people to reply to this post telling me how they did it and how I can do it too. I want to have full access to java-based applications and games, etc.
   I look forward to responses and any help will be appreciated.

---

### Post by gluonman on 2008-07-09
Alright. I managed to figure out how to get FrostWire to work. I found some Java alternatives that helped get that going. However, the second problem concerning online applications and games still remains.

---

### Post by gluonman on 2008-07-09
All problems fixed. :)

---

### Post by tamarku on 2008-07-09
Gluon, 

So how did you get Frostwire to work.  I started doing some searches last evening and tried a couple of things but nothing seemed to work so I was going to pick it up again tonight.  Your post was the first one I came across. 

Regards, 
tamarku

---

### Post by Palumbo on 2008-08-17
I was having issues getting The Learning Sandbox to work with the [O'Reilly School of Technology]("http://oreillyschool.com/") where I'm studying to become a Unix/Linux System Administrator. This program offers an interactive java environment to simulate running Linux/Unix on a server. I'm sure this is a similar issue for anybody not able to run javascript in their web browser (i.e. games.yahoo.com). 

I finally got the issue resolved by launching the Synaptic Package Manager and searching for "Java Runtime Environment". From the resulting search query I was able to download "sun-java6-plugin", which in turn downloaded any dependent files. 

I'm very new to Linux and therefore Ubuntu, so I think this particular download falls outside of the free software realm. On the other hand, it resolved my issue perfectly. 

-Palumbo

p.s. Going forward, if you found a resolution to your issue, please don't post "Alright, all fixed now!" Please take the time to describe what and how you were able to resolve or work around the issue you first described. That's the only real way for these forums to be of any use to anybody.

---

### Post by wiseguy on 2008-08-20
You need Java version 5 to play online java games.

Version 6 won't work with java games but works with frostwire.

Work around for this is to keep switching accordingly.

---

