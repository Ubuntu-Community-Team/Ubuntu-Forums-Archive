---
title: "Ubuntu 8.04 no java and no Audigy 2 LS Sound"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by raddad on 2009-03-09
I made the move from windows to Ubuntu 6.06 and can not get java setup on firefox or any sound.  I did the upgrades to Ubuntu 8.04 which fixed the foxfire flash problem but still no java.

I have tried many different fixes for the java and the sound I have read here in the forums and I am having no luck at all.

Help??

---

### Post by Cresho on 2009-03-09
what fixes.  i run java anf flash 10 with fullscreen just fine.

---

### Post by scphan on 2009-03-09
java as in the plugin for firefox? i think i can find some links for java in general for the system setup if you're looking to install jdk1.6.0_12 from Sun and not the one provided by ubuntu through the repositories ( i program with java so i'd rather use original jvm ) if you just need java for normal use, here's a general installation instruction page: [https://help.ubuntu.com/community/JavaInstallation]("https://help.ubuntu.com/community/JavaInstallation") or go to Add/Remove Applications in your menu on the desktop bar and do a search for 'java' there's also someplace on this forum for installing the latest flash successfully via the adobe website which i've used

---

### Post by Cresho on 2009-03-09
here let me help you

fix software sources "Download from" usa to main server.  update the resources.  It is in Administration->Software Sources.  add 3rd party stuff for source files.  refresh with button on top.  in add and remove programs, under show, select "all available applications"

open up terminal and do a 

sudo apt-get update

then

sudo apg-get upgrade

then do a search for gstreamer in add and remove and install these to enable most codecs and also java

ubuntu restricted extras
gstreamer extra plugins
gstreamer ffmpeg video plugin
gstreamer plugins for mms, wavpack, quicktime
gstreamer plugins for aac, xvid, mpeg2, faad
gstreamer dirac video plugin
gstreamer fluendo mpeg2 demuxing plugin

remember that some are restricted by law in some countries.

then you open up synaptic and do this

search for flash and look for version 10 and install that one its called adobe-flashplugin        version 10

---

### Post by scphan on 2009-03-09
here's another link, this is for sun java, [http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/]("http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/") it's more straightforward and [http://www.trausch.us/2009/02/15/installing-sun-jre-6u12-on-ubuntu-intrepid-810/]("http://www.trausch.us/2009/02/15/installing-sun-jre-6u12-on-ubuntu-intrepid-810/") this one looked promising to me but it was too late by the time i found it and already configured my ubuntu to run jdk1.6.0_12 by default sufficiently, for the firefox java plugin you have to make a symbolic link to the java's libjavaplugin_oji.so as described in the first link above, good luck, i'm going to bed now

---

### Post by raddad on 2009-03-11
The problem seems to be system sound.  Nothing I do produces sound.  I have installed flash, java (both sun micro and open  source) and still have not even a system sound.  Seems if we solve the system sound problem the rest may solve itself.

Anyone have any ideas on the audigy sound thing?

---

### Post by raddad on 2009-03-11
...java (in neither form) works either.

---

### Post by scphan on 2009-03-12
what happens when you type java -version? just wondering if it'll respond, also if it does respond with a java version you do recognize, try compiling and executing a small program..

open a text editor:

public class Hello
{
public static void main( String args[] )
{
System.out.println( "Hello, java has successfully compiled and execute this program" );
}
}

.. then save it as Hello.java on the desktop
then open a terminal, 'cd Desktop'
then type 'javac Hello.java'
then type 'java Hello'
it should execute correctly if java was installed correctly

---

### Post by raddad on 2009-03-12
:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)


and then...

raddad@Lenny:~/Desktop$ javac Hello.java
The program 'javac' can be found in the following packages:
 * gcj-4.1
 * jikes-sun
 * jikes-sablevm
 * gcj-4.2
 * kaffe
 * sun-java6-jdk
 * jikes-classpath
 * openjdk-6-jdk
 * ecj
 * j2sdk1.4
 * jikes-gij
 * jikes-kaffe
 * sun-java5-jdk
 * java-gcj-compat-dev
Ask your administrator to install one of them
bash: javac: command not found
raddad@Lenny:~/Desktop$ java Hello
Exception in thread "main" java.lang.NoClassDefFoundError: Hello
Caused by: java.lang.ClassNotFoundException: Hello
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: Hello. Program will exit.
raddad@Lenny:~/Desktop$ 

I do appreciate all the help.  My son is visiting me this comming week and I'd sure like to show him a great alternative to MS products, fully functioning.  Such an easy install I can't believe the sound and java is being such a dog.

---

### Post by scphan on 2009-03-13
lol, looks like java's not wired appropriately

try "sudo update-java-alternatives -l"
then select one and set it by
"sudo update-java-alternatives --config"

see if that works then try the program again

otherwise i would do a clean install of java with these instructions after going to synaptic package manager under System>Administration and get rid of the currently installed java (search for jdk, java):

[http://www.trausch.us/2009/02/15/installing-sun-jre-6u12-on-ubuntu-intrepid-810/]("http://www.trausch.us/2009/02/15/installing-sun-jre-6u12-on-ubuntu-intrepid-810/")

---

### Post by raddad on 2009-03-13
I did those and oddly enough when I went to check if java was working, firefox gave me an option to load the plugin, never did that previously; it offered icetea, and java now works.

Now if we can get system sound up I'll be a very happy camper!!

Thanks again!!

---

### Post by raddad on 2009-03-13
I spoke too soon.  The plugin loaded up, it asked where the cache file should be located, but java web pages still do not work.  I am so sad.

---

