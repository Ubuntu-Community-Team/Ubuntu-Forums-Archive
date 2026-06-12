---
title: "Unable to install JAVA in Ubuntu 8.04 LTS 64bit"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by ZoRRoCanCer on 2009-01-19
I am Unable to install JAVA in Ubuntu 8.04 LTS 64bit, currently installed all updates. Also downloaded RPM and Self extracting file from JAVA.COM. Trying to follow instruction from Java.com , it didn't work. Please help me out.

---

### Post by abyssius on 2009-01-19
You will be able to install JAVA direct;y from Synaptic Package Manager or Add/Remove Programs once you update and expand your repository source list. Please follow the instructions provided in the link below. JAVA will be available for install in **System->Administration->Synaptic Package Manager** once you complete this.

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

P.S. If you haven't already, make sure that you access System->Administration->Software Sources  - Select the 3rd Party Software tab and place a check mark in all the boxes (except for the CD-ROM).

---

### Post by ZoRRoCanCer on 2009-01-20
Dear fellow, I am still unable start Java applet in browser (i.e)  Mozilla Firefox. I have installed some packages which have JRE in their names, but they have just add some policies in **System > Preferences**.
I have also try to verify Java at JAVA.COM.It says you have previous version of Java and just after a sec my PC gets nonrespondent & screen gets grabbled. I have to restart PC after that to use it again. :(
Also tried to play online games like _games.yahoo.com_, but it says install java first.

One thing about ***medibuntu***:
The packages notified by medibuntu was available to install in synaptic package manager except ibm-jre.. packages. Probably that is because, I have JRE installed by Add/remove programs.

What should I do, to have JAVA??

---

### Post by lovelyvik293 on 2009-01-20
try to use the command java in terminal.
And post the output of this command.

---

### Post by ZoRRoCanCer on 2009-01-20
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)
where options include:
    -d32	  use a 32-bit data model if available
    -d64	  use a 64-bit data model if available
    -server	  to select the "server" VM
                  The default VM is server.

    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose[:class|gc|jni]
                  enable verbose output
    -version      print product version and exit
    -version:<value>
                  require the specified version to run
    -showversion  print product version and continue
    -jre-restrict-search | -jre-no-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions with specified granularity
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions with specified granularity
    -esa | -enablesystemassertions
                  enable system assertions
    -dsa | -disablesystemassertions
                  disable system assertions
    -agentlib:<libname>[=<options>]
                  load native agent library <libname>, e.g. -agentlib:hprof
                  see also, -agentlib:jdwp=help and -agentlib:hprof=help
    -agentpath:<pathname>[=<options>]
                  load native agent library by full pathname
    -javaagent:<jarpath>[=<options>]
                  load Java programming language agent, see java.lang.instrument
    -splash:<imagepath>
                  show splash screen with specified image
See [http://java.sun.com/javase/reference](http://java.sun.com/javase/reference) for more details.


**[COLOR="Red"]That came out when I have wrote "java" and pressed enter[/COLOR]**

---

### Post by Michael.Godawski on 2009-01-20
hi,

have a look at :


[LIST]
[*][http://godawski.oxyhost.com/installingjava.html](http://godawski.oxyhost.com/installingjava.html)
[/LIST]

perhaps it helps.

---

### Post by ZoRRoCanCer on 2009-01-20
> **Michael.Godawski said:**
> hi,

have a look at :


[LIST]
[*][http://godawski.oxyhost.com/installingjava.html](http://godawski.oxyhost.com/installingjava.html)
[/LIST]

perhaps it helps.

My terminal sys:

zorro@zorro----:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin

Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

zorro@zorro-----:~$ 

After that non of the code seems with right results
At the end same previous version have been called by :java -version"

zorro@zorro----:~$ java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b23, mixed mode)
zorro@zorro----:~$

---

### Post by gandaran on 2009-01-20
ZoRRoCanCer
there isn't any sun java plugin for 64-bits firefox, what you can install for 64-bits is open java, just look in synaptic package manager for the icedtea plugin, mark for install and click the apply button or just install the ubuntu-restricted-extras, this package will install the java plugin for you.

---

### Post by 73ckn797 on 2009-01-20
I have gone round and round with Java in Ubuntu. On the 64bit side once the latest Java was released for 64bit, I removed all prior installs of Java and loaded to latest. I have had no issues since.

---

### Post by ZoRRoCanCer on 2009-01-20
> **73ckn797 said:**
> I have gone round and round with Java in Ubuntu. On the 64bit side once the latest Java was released for 64bit, I removed all prior installs of Java and loaded to latest. I have had no issues since.

How do I ?

---

### Post by ZoRRoCanCer on 2009-01-20
> **gandaran said:**
> ZoRRoCanCer
there isn't any sun java plugin for 64-bits firefox, what you can install for 64-bits is open java, just look in synaptic package manager for the icedtea plugin, mark for install and click the apply button or just install the ubuntu-restricted-extras, this package will install the java plugin for you.

There are 4 packages come with the search of ICEDTEA, two of them are already installed, remaining two are JDK, should I install that?

---

### Post by gandaran on 2009-01-20
> **ZoRRoCanCer said:**
> There are 4 packages come with the search of ICEDTEA, two of them are already installed, remaining two are JDK, should I install that?
no, this should be fine for you, does java work now in firefox?
well if open java doesn't work for you wait until someone knows how to get sun java working in a 64-bits firefox, as far has I know it's still not possible, maybe I'm wrong!

---

### Post by ZoRRoCanCer on 2009-01-20
Tell me. If only 64 bit is hurdle in using Java then how can I rollback to 32 bit?

Can't I install rpm or self extracting file for 64 bit available at 
[http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80)

---

### Post by 73ckn797 on 2009-01-20
> **ZoRRoCanCer said:**
> Tell me. If only 64 bit is hurdle in using Java then how can I rollback to 32 bit?

Can't I install rpm or self extracting file for 64 bit available at 
[http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80)

Follow this thread for installing Java. 
[http://ubuntuforums.org/showthread.php?t=1011899](http://ubuntuforums.org/showthread.php?t=1011899)

You can also use the "sun-java6-jre" from repositories and it should work. You will have to do the EULA agreement. The thread is how I successfully loaded Java in 64 Ubuntu.

---

### Post by ZoRRoCanCer on 2009-01-21
Finally this thread solved this puzzle of installing Java in 64bit Ubuntu:

[http://ubuntuforums.org/showthread.php?t=1013658](http://ubuntuforums.org/showthread.php?t=1013658)

Before going through this. You have to remove all java packages you have tried. If you are fresh then don't waste your time!

> **Antionio said:**
> Hello!

I've had HUGE problems with java plugins in the past and I've found forum threads very useful when searching installation help. So I decided to show you how I got the brand new 64bit java plugin working for 64bit Ubuntu (8.04) and the 64bit Firefox 3.0.4.

EDIT: Be sure to read the whole post and try the tips I've added below.

1)

Download Linux x64 JRE bin from the following address:
[https://jdk6.dev.java.net/6uNea.html](https://jdk6.dev.java.net/6uNea.html)

2)

Run the .bin file so that it extracts the jre files. Copy the files where you want to keep them. I put them next to my other JDK's and JRE's.

```

sudo chmod +x jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
sudo ./jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
sudo mv jre1.6.0_12 /some_path

```

3)

Create a symbolic link to Firefox plugin directory:

```

mkdir ~/.mozilla/plugins/
ln -s /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so ~/.mozilla/plugins/

```

4)

EDIT: These about:config settings might be unnecessary after all. Some people have gotten the plugin working without changing these settings.

Run Firefox and write about:config to the address bar. Write "java" to the filter so that you can find the settings more easily.

Change the following settings:

java.default_java_location_others = /path_to_jre/jre1.6.0_12
java.java_plugin_library_name = libnpjp2


5)

Voila, the plugin should be working now. If not, respond to this thread so we can troubleshoot for different ubuntu configurations. Also if you have some better way to get it working, please let us know.

EDIT:
Here are some tips people have posted:

1) If you're having problems getting java to work, uninstall any previous java version you might have! (for example icedtea and openjdk).

```

sudo apt-get remove icedtea6-plugin openjdk-6-jre

```

2) Try changing the default java jre with ```
sudo update-alternatives --config java
```

If you still don't get the plugin working after this, try to read through the responses of this thread for more tips. I might not update this tutorial so often.

;)

---

