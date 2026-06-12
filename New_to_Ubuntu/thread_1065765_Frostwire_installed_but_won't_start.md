---
title: "Frostwire installed but won't start"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by trekguy on 2009-02-10
I installed Frostwire, and there is an icon in Apps/Internet.  When I click on it, it does nothing.  When I run it in Terminal, I get the message shown below.  I have the new 64 bit Java 1.6.0_12, first it doesn't find Java, then Frostwire seems to find it, and it's "suitable"... but again has a problem with it.

???

Starting FrostWire...
Java exec not found in PATH, starting auto-search...
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
Java exec found in  /usr/java/jre1.6.0_12/bin/
Suitable java version found  [/usr/java/jre1.6.0_12/bin/java = 1.6.0_12]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO:
Unable to access jarfile FrostWire.jar

/usr/java/jre1.6.0_12/bin/
******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
/usr/lib/frostwire/runFrostwire.sh: line 158: java: command not found

---

### Post by gjoellee on 2009-02-10
Try this:
```
sudo apt-get install ubuntu-restricted-extras
```

then launch Frostwire from the terminal:
```
frostwire
```

if it does not work, post the output

---

### Post by quietbear on 2009-02-10
I had this same problem, and ran that code, it got halfway through the install and froze.  now it says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

what do I do?

---

### Post by cerealtx on 2009-02-10
frostwire, is a version of limewire, but limewire now has a linux version, u might suggest just dling/installing limewire, seeing as it will probably be alot more supported than frostwire

---

### Post by trekguy on 2009-02-10
> **gjoellee said:**
> Try this:
```
sudo apt-get install ubuntu-restricted-extras
```

then launch Frostwire from the terminal:
```
frostwire
```

if it does not work, post the output

dean@dean-desktop:~$ frostwire
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
HOSTNAME IS dean-desktop
Starting FrostWire...
Java exec not found in PATH, starting auto-search...
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
Java exec found in  /usr/java/jre1.6.0_12/bin/
Suitable java version found  [/usr/java/jre1.6.0_12/bin/java = 1.6.0_12]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO:
Unable to access jarfile FrostWire.jar

/usr/java/jre1.6.0_12/bin/
******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
/usr/lib/frostwire/runFrostwire.sh: line 158: java: command not found


No new restricted extras available... had that already.

Got to be the Java ... it finds the current version, but the path isn't right, or something????

---

### Post by howefield on 2009-02-10
> **quietbear said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

what do I do?

You open a terminal and type

```
sudo dpkg --configure -a
```

Then enter your password when it asks for it and press enter.

Then do sudo apt-get update

---

### Post by jerome1232 on 2009-02-10
> **trekguy said:**
> dean@dean-desktop:~$ frostwire
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
HOSTNAME IS dean-desktop
Starting FrostWire...
Java exec not found in PATH, starting auto-search...
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
Java exec found in  /usr/java/jre1.6.0_12/bin/
Suitable java version found  [/usr/java/jre1.6.0_12/bin/java = 1.6.0_12]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO:
Unable to access jarfile FrostWire.jar

/usr/java/jre1.6.0_12/bin/
******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
/usr/lib/frostwire/runFrostwire.sh: line 158: java: command not found


No new restricted extras available... had that already.

Got to be the Java ... it finds the current version, but the path isn't right, or something????

Do you have java installed? I believe all you need is the jre.

[apt://sun-java6-jre]("apt://sun-java6-jre")
```
sudo apt-get instal sun-java6-jre
```

---

### Post by trekguy on 2009-02-10
> Starting FrostWire...
Java exec not found in PATH, starting auto-search...
OOPS, unable to locate java exec in /usr/lib/ hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
[B]Java exec found in /usr/java/jre1.6.0_12/bin/
Suitable java version found [/usr/java/jre1.6.0_12/bin/java = 1.6.0_12][/B]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO:
Unable to access jarfile FrostWire.jar

/usr/java/jre1.6.0_12/bin/

I just installed the new 64 bit Java 1.6.0_12.  It seems to know it's there, but doesn't want use it.   ?????

---

### Post by jerome1232 on 2009-02-10
Try executing the java file directly

```
java -jar /path/to/froswire.jar
```

---

### Post by trekguy on 2009-02-10
> **jerome1232 said:**
> Try executing the java file directly

```
java -jar /path/to/frostwire.jar
```

Did that... then...

The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found


It's asking for Java... but I do have it... it's just not finding it for some reason.  :confused:

---

### Post by jerome1232 on 2009-02-10
huh well maybe...

```
/usr/java/jre1.6.0_12/bin/java -jar /path/to/frostwire.jar
```

**If** that works then you should be able to create a symbolic link to your java jre.

```
sudo ln -s /usr/java/jre1.6.0_12/bin/java /usr/local/bin/java
```

After creating the symbolic, running frostwires startup script should work like normal.

---

### Post by trekguy on 2009-02-10
> **jerome1232 said:**
> huh well maybe...

```
/usr/java/jre1.6.0_12/bin/java -jar /path/to/frostwire.jar
```

**If** that works then you should be able to create a symbolic link to your java jre.

```
sudo ln -s /usr/java/jre1.6.0_12/bin/java /usr/local/bin/java
```

After creating the symbolic, running frostwires startup script should work like normal.

Result...

dean@dean-desktop:~$ /usr/java/jre1.6.0_12/bin/java -jar /path/to/frostwire.jar
Unable to access jarfile /path/to/frostwire.jar

---

### Post by jerome1232 on 2009-02-10
When I say /path/to/frostwire.jar I don't mean it literally, you need to put the real path to frostwires directory.

So if you have frostwire sitting your home directory that should be

```
/usr/java/jre1.6.0_12/bin/java -jar ~/frostwire/frostwire.jar
```

I'm not sure where frostwire is actually installed so I don't know what you need to put for that last part.

To find it you could post the output of this, it should tell me where froswire.jar is actually at.
```
sudo updatedb
locate FrostWire.jar
```

---

### Post by trekguy on 2009-02-10
> **jerome1232 said:**
> When I say /path/to/frostwire.jar I don't mean it literally, you need to put the real path to frostwires directory.

So if you have frostwire sitting your home directory that should be

```
/usr/java/jre1.6.0_12/bin/java -jar ~/frostwire/frostwire.jar
```

I'm not sure where frostwire is actually installed so I don't know what you need to put for that last part.

To find it you could post the output of this, it should tell me where froswire.jar is actually at.
```
sudo updatedb
locate FrostWire.jar
```

:redface:

Thank you for your patience... as you can tell... I'm stumblin' through this.  Directions need to be real simple, and real plain. :redface:

I get no output from "locate Frostwire.jar"  at all.  :confused:

---

### Post by jerome1232 on 2009-02-10
Did you copy paste my code or did you type in yourself?

The reason I ask is Frost**w**ire.jar is different than Frost**W**ire.jar  (capital W).

Based on one of your previous errors the file is FrostWire.jar not Frostwire.jar

So does it return nothing for FrostWire.jar?

Sometimes I'm not great at explaining things so sorry if my explanations are lacking :)

---

### Post by trekguy on 2009-02-10
> **jerome1232 said:**
> Did you copy paste my code or did you type in yourself?

The reason I ask is Frost**w**ire.jar is different than Frost**W**ire.jar  (capital W).

Based on one of your previous errors the file is FrostWire.jar not Frostwire.jar

So does it return nothing for FrostWire.jar?

Sometimes I'm not great at explaining things so sorry if my explanations are lacking :)

Yep, I did copy/paste... no output... just the ~$

---

### Post by trekguy on 2009-02-11
Can anyone explain what this line means??

[B]The version of Java in your PATH is:
/usr/lib/frostwire/runFrostwire.sh: line 158: java: command not found[/B]

---

### Post by Old Old Duffers on 2009-02-11
sudo update-alternatives --config java

Pick the version of java you want.
Frostwire WILL run then.  Had the same
problem

---

### Post by trekguy on 2009-02-11
> **Old Old Duffers said:**
> sudo update-alternatives --config java

Pick the version of java you want.
Frostwire WILL run then.  Had the same
problem

Result...

[B]There is only 1 program which provides java
(/usr/bin/gij-4.2). Nothing to configure.
[/B]

Still no joy.  :(


So, what's this gij -4.2 in /usr/bin??  :confused:

There's also a Java folder in /usr.  ???

---

### Post by trekguy on 2009-02-11
Found this from an older thread at the Frostwire forums... it appears to be an answer, but I'm not smart enough to know what I'm supposed to do with it... LOL!  Help 

*You have to go in and do what the developers (errrr FW scriveners?) didn't do .. change the location of where Frostwire (and Limewire too) looks for that wonder world of java. Just use the "#" to block off the offending parts of the FW script and then type in your location for jre (which is where jre ALWAYS installs in ubuntu (like Duh!) *

---

### Post by ben2talk on 2009-02-21
Bumping 
Installed (using installer Frostwire-4.17.1.i586.deb)

ben@ubuntu-desktop:~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
*+        3    /usr/lib/jvm/java-6-openjdk/jre/bin/java

Press enter to keep the default[*], or type selection number: 
ben@ubuntu-desktop:~$ frostwire
sh: unpack200: not found
HOSTNAME IS ubuntu-desktop
Starting FrostWire...
Java exec not found in PATH, starting auto-search...
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ben@ubuntu-desktop:~$

frostwire run script is at /usr/bin/frostwire
#!/bin/bash
export HOSTNAME=localhost
/usr/lib/frostwire/runFrostwire.sh

Next step - synaptic, remove Frostwire.

In contrast, after installing LimeWireLinux 4.18 Pro.deb . . .

ben@ubuntu-desktop:~$ limewire
Starting LimeWire...
Java exec not found in PATH, starting auto-search...
Java exec found in  /usr/lib/jvm/java-6-sun-1.6.0.10/bin/
Suitable java version found  [/usr/lib/jvm/java-6-sun-1.6.0.10/bin/java = 1.6.0_10]
Configuring environment...
Loading LimeWire:
ben@ubuntu-desktop:~$ 

I used this same installer (before reinstalling ubuntu 8.10) and it had no issues.
What's going on people? please help.

Trying this next:

sudo update-java-alternatives -s java-6-sun

frostwire>frostwire.txt

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_10]
Configuring environment...
Loading FrostWire:

BINGO!!!!

---

### Post by jhetrick62 on 2009-04-09
I found this fix on the Fedora Forum.  There seems to be some issues with the Frostwire when using the install package.  I had no Frostwire.jar file either after unpacking.

Better installation here providing that when you run the command "update-alternatives --config java", you get that you have java-6-sun properly installed and listed.  If you do then follow this.

```
1.  Download the frostwire-4.17.1.noarch.tar.gz file from www.frostwire.com
2.  Move the file to /opt
3.  Un-pack the file
4.  My suggestion is to make a new directory of /opt/frostwire
    -then move all un-packed contents from the /opt/frostwire-4.17.1.noarch directory 
      that was created to the new /opt/frostwire directory (this is so that once you get your 
      menu items set up, future upgrades can also be copied here and you won't have to keep 
      re-creating a menu item - your choice)
5.  It should now run by executing the command /opt/frostwire/runFrostwire.sh in a terminal
6.  Obtain a frostwire.png image file (google) to use as an icon and place it in your system 
    after re-sizing to 48 x 48 into /usr/share/icons/hicolor/48x48/apps
7.  Next there is a file for your gnome menus in the /opt/frostwire directory that you have to 
     modify to suit your needs called frostwire.desktop
8.  Modify this file to match your system now.  
    Change:  Exec=/usr/bin/frostwire to Exec=/opt/frostwire/runFrostwire.sh
    Change:  Icon=frostwire.png to Icon=/usr/share/icons/hicolor/48x48/apps/frostwire.png
```

You should be all set and a menu item will appear on each users gnome menu and you will have a working Frostwire.

---

