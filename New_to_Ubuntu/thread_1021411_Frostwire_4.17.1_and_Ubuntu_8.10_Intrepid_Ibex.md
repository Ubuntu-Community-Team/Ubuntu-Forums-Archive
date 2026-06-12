---
title: "Frostwire 4.17.1 and Ubuntu 8.10 Intrepid Ibex"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by wynneth on 2008-12-25
Ok, so I'm running Ubuntu 8.10 Intrepid Ibex latest updates. I downloaded Frostwire (tarball), which was hard to find because for some reason the .deb and .rpm package links on the official site and in many forums are all 404d. I seem to have managed to get alot of the problems sorted out courtesy of another thread - had to run fromdos to change the runFrost.sh from dos style to unix style. Had to change sh to bash on line 3. (I'm just throwing the shortened version out because either you know what fixes I mean or it doesn't matter anyway.) Now I'm getting the following:

```
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_10]
Configuring environment...
Loading FrostWire:
log4j:WARN No appenders could be found for logger (com.limegroup.gnutella.gui.Initializer).
log4j:WARN Please initialize the log4j system properly.
Error: Couldn't find per display information

******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Server VM (build 11.0-b15, mixed mode)

```

The community page for frostwire says in the case of an error such as this to "*Simply type in sudo update-alternatives --config java then select the alternative that includes "sun" in the name.*" however, I have java_6_sun currently installed. Is there possibly something else I need to edit to resolve this issue?

---

### Post by jamesstansell on 2008-12-25
This looks like the actual problem.

> Error: Couldn't find per display information


Sounds like it's trying to do something graphical, but failing to initialize.  Are you running in a graphical environment?

Does /usr/bin/jcontrol give you any errors starting up?  (I just picked it as a relatively small app that I knew you would have installed.)

---

### Post by mick222 on 2008-12-25
frostwires in the repositories install from there if you can

---

### Post by wynneth on 2008-12-25
@jamesstansell: Yes I'm running in a graphical environment. I actually just installed Ubuntu recently, so I'm running everything stock - which is to say Gnome/GTK2.0. jcontrol opened with no errors whatsoever no problem. I didn't think to mention when I run frostwire it brings up the splash and does some startup routines, the last thing I can actually read before it dissapears (which may not be the last thing it does but is the last one I can read) is something about Loading Beanshell.:confused:

@mick222: I have absolutely $null experience with repositories as of yet, I originally tried to do sudo apt-get install frostwire, and then searched the synaptic for it as well and did not find it, otherwise I would not have installed from a tarball.:(

---

### Post by wynneth on 2008-12-27
Well now that the link isn't dead I went and downloaded the deb package from the frostwire site (it was dead before). Now I get all of this:

```

Error: Could not open jar file: jmdns.jar
Error: Could not open jar file: icu4j.jar
Error: Could not open jar file: ProgressTabs.jar
Error: Could not open jar file: httpclient-4.0-alpha3.jar
Error: Could not open jar file: commons-codec-1.3.jar
Error: Could not open jar file: log4j.jar
Error: Could not open jar file: gettext-commons.jar
Error: Could not open jar file: onion-common.jar
Error: Could not open jar file: guice-1.0.jar
Error: Could not open jar file: httpcore-nio-4.0-beta2.jar
Error: Could not open jar file: jaudiotagger.jar
Error: Could not open jar file: mp3spi.jar
Error: Could not open jar file: aopalliance.jar
Error: Could not open jar file: jorbis.jar
Error: Could not open jar file: jl.jar
Error: Could not open jar file: jdic.jar
Error: Could not open jar file: clink.jar
Error: Could not open jar file: httpcore-niossl-4.0-alpha7.jar
Error: Could not open jar file: daap.jar
Error: Could not open jar file: FrostWire.jar
Error: Could not open jar file: commons-logging.jar
Error: Could not open jar file: lw-all.jar
Error: Could not open jar file: jflac.jar
Error: Could not open jar file: forms.jar
Error: Could not open jar file: jogg.jar
Error: Could not open jar file: messages.jar
Error: Could not open jar file: tritonus.jar
Error: Could not open jar file: themes.jar
Error: Could not open jar file: junit.jar
Error: Could not open jar file: httpcore-4.0-beta2.jar
Error: Could not open jar file: jdic_stub.jar
Error: Could not open jar file: foxtrot.jar
Error: Could not open jar file: vorbisspi.jar
Error: Could not open jar file: looks.jar
Error: Could not open jar file: jython.jar
Error: Could not open jar file: jcraft.jar
Error: Could not open jar file: onion-fec.jar
Traceback (most recent call last):
  File "/usr/lib/frostwire/unpack200.py", line 58, in <module>
    makeHashes()
  File "/usr/lib/frostwire/unpack200.py", line 17, in makeHashes
    output = file('hashes','w')
IOError: [Errno 13] Permission denied: 'hashes'
HOSTNAME IS wilykat
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_10]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO:
Unable to access jarfile FrostWire.jar


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Server VM (build 11.0-b15, mixed mode)

```

So now what do I need to do to fix it?? I'm thinking the path needs to be set (CLASSPATH SET TO:) but I don't know where.

---

### Post by wynneth on 2008-12-27
NEVERMIND - needed to run it SUDO the first time to get it going.

---

### Post by jhansonxi on 2009-04-20
This issue occurs with Ubuntu 8.04 (Hardy Heron) as well.  The Python application unpack200.py wants to create a hashes file and can't as the file and directory are owned by root and can't be written to by a normal user.  FrostWire will not run until the file is created.  The solution is to run it manually from a terminal:

sudo python /usr/lib/frostwire/unpack200.py

This creates the hashes file and FrostWire will then work.  Either there is a bug in unpack200.py or the installation scripts in the deb package that don't run it during installation.

---

