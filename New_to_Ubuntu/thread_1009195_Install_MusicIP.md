---
title: "Install MusicIP"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by jratliff on 2008-12-12
I am trying to install MusicIP. I downloaded the tgz file from the website and unpacked it to the desktop. There is now a folder named MusicIP on the desktop with a folder named MusicMagicMixer inside. Inside of that are the files and folders I recognize from the Windows version.

How do I get the application to run? There is no package to install, so Package Manager is no use.

I am guessing the files need to be transferred to another directory. How do I figure out which one? I have tried to read the Ubunutu documentation, but it gets out of reach pretty quickly. 

Thanks for any help.

P.S. I install Linux every couple of years and then uninstall it when I hit an impenetrable wall. In the past that has been a driver, or a network configuration, or a piece of software I need that has no Linux equivalent. I'd like to stay with it this time, but if I can't figure out how to install a simple piece of software...

Please help.

Thanks.

---

### Post by OldGrey on 2008-12-12
Have tried the MusicIP help pages? [http://www.musicip.com/mixer/linuxstart.jsp](http://www.musicip.com/mixer/linuxstart.jsp)

---

### Post by renzokuken on 2008-12-12
have you looked here [http://www.musicip.com/mixer/linuxstart.jsp](http://www.musicip.com/mixer/linuxstart.jsp) ?

looks like all you have to do is enter the folder you etarcted and run the MusicMagicMixer command.

---

### Post by jratliff on 2008-12-12
Thanks. I have read that and tried to both double-click the MusicMagicMixer file with no result and also to run it from the terminal.

The documentation states that "The MusicIP Mixer runs as a Java-based gui on linux."

Is Java part of the standard Ubuntu installation? How can I tell? Do I need to use "java" as part of the command line?

Thanks.

---

### Post by renzokuken on 2008-12-12
i dont think it is, but it is in the repos. fire up synaptic (System -> Admin -> Synaptic Package Manager) and search for "java". i think you need java 1.4 so should be pretty obvious which package you need to install.

install that then try again

edit: i thinks it sun-java-jre or something is the java package you want

---

### Post by jratliff on 2008-12-12
Thanks. I got Java installed, but still no luck getting MusicIP to run. 

I right-clicked and Open with-> Sun Java 6 Web Start and get an error.

From the terminal I get a different error.

Hmm....

---

### Post by CDrewing on 2009-10-04
I got the same problem here,

for MusicIP I extra changed from IcedTea5 to Sun's Java. It is running and the defaut interpreter for Java classes. I also changed the JAVA_HOME variable to my Sun's binary.

But it is not working. "./MusicMagicMixer" on the terminal will bring up nothing; after a second I got the command prompt again - without any debug messages.

---

### Post by andrewlorien on 2011-04-17
I got it to work.

install the 32-bit java libraries:
ia32-sun-java6-bin

then create a bash file like this 
i call it MusicMagicStart, and i saved it in the same folder as MusicMagic,  /opt/MusicMagicMixer

```

#!/bin/bash

export JAVA_HOME="/usr/lib/jvm/ia32-java-6-sun"
/opt/MusicMagicMixer/MusicMagicMixer -anyimage &
```

make that file executable
chmod +x /opt/MusicMagicMixer/MusicMagicStart

then add a menu item which calls MusicMagicStart, give it a funky musical icon, and go!

---

### Post by wowotiel on 2012-01-24
@andrewlorien:
I am trying also to make the MuscicIP GUI working on Ubuntu, maybe you can help me.

I have no ia32-sun-java6-bin on my Ubuntu system because I use an a shell script to automate the retrieval and installation of the Oracle (Sun) Java Runtime Environment:
[http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)
I am using the repository because of the additional advantages: a possibly installed out-of-date sun-java6  installation will be removed completely and if you keep the software  source in your list, you will automatically receive updates of the  script.
The version of java is now: jre 1.6.0.30

I have tried the following, but it does not work. :(
```
#!/bin/bash

export JAVA_HOME="/opt/java/32/jre1.6.0_30"
/home/medion1/MusicIP/MusicMagicMixer -anyimage &
```and also
```
#!/bin/bash

export JAVA_HOME="/usr/bin/mime/packages/update-sun-jre"
/home/medion1/MusicIP/MusicMagicMixer -anyimage &
```Could someone point my in the right direction ?

---

### Post by uRock on 2012-01-24
Necromanced too many times since 2008.

Thread Closed

---

