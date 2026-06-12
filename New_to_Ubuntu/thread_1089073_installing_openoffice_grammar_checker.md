---
title: "installing openoffice grammar checker"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by nachos99 on 2009-03-06
i am trying to install a LanguageTool extension ([http://extensions.services.openoffice.org/project/languagetool](http://extensions.services.openoffice.org/project/languagetool)) into my openoffice 3.0.1.  

i am getting the error below through the openoffice extension manager.

[IMG]http://img19.imageshack.us/img19/9853/errorshot.jpg[/IMG]

when checking under tools -> options -> java in openoffice.org my current java runtime environment is the following: java runtime environment already installed Sun Microsystems Version 1.6.0_07.

checking through the terminal, i see:
~$ java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

i see it's noted on the languagetool site that java runtime environment 5.0 or later should be selected. 

1) i assume there is no workaround without updating the JRE?

2) what java version should i be upgrading to? 

3) should i be messing with my JRE, and would that be worth the effort (would it be complicated causing possible problems and other things messing up etc.)?

thanks in advance.


running hardy 8.04

---

### Post by erudite on 2009-03-06
uninstall java by command line or synaptic.

Then download the latest java from [LINK.]("http://javadl.sun.com/webapps/download/AutoDL?BundleId=27973")

Then do "chmod +x file.bin"
"./file.bin"

---

### Post by jmszr on 2009-03-06
nachos99,

           If erudite's advice didn't work out try going to System > Administration > Synaptic > Search > openoffice.org-java-common > Mark for Installation > Apply.  I'm not sure about 3.0.1, but it was needed for some extensions in 2.4.x

---

### Post by nachos99 on 2009-03-06
here's a noob question.

checking through the terminal, i see:
~$ java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

when i check java version at synaptic or add/remove apps, i see that java 6 runtime environment is installed. 

[IMG]http://img26.imageshack.us/img26/9987/javainstalled.jpg[/IMG]

what then is the java version 1.6.0_07 coming up in the terminal?

---

### Post by erudite on 2009-03-07
I don't really know but maybe you have it installed twice.

You should try uninstalling the older one as it may be using that by default.

---

