---
title: "looking for remote text editor."
date: 2009-03-27
forum: New to Ubuntu
---

### Post by ja660k on 2009-03-27
hey guys,
does anyone know of a text editor that i can run then connect to a server and work on code remotly?

i know of ssh and vim etc. but i need to copy and paste.
also i know i can forward X in ssh but the server doesnt have very powerful text editors 

so im looking for a editor that can do this.
if people are still confused. im looking for the ubuntu equivalent of coda for mac.

thanks :)

---

### Post by The Cog on 2009-03-27
I always use nautilus to make the connection, opening a url something like:
ssh://username@1.2.3.4
and then use my fave editor (geany or gedit) directly on the remote file. It behaves the same as a local file would.

---

### Post by doas777 on 2009-03-27
i usually use nano (it has copy/paste) for cli editing.
in windows I use winscp, and right-click -> Edit. it's basically notepad.

---

### Post by ja660k on 2009-03-27
oh that is cool!

is there a way i can keep alive my remote folders? on logout?

thanks alot i didnt know that 
what happen to the thanking button?

---

### Post by doas777 on 2009-03-27
> **The Cog said:**
> I always use nautilus to make the connection, opening a url something like:
ssh://username@1.2.3.4
and then use my fave editor (geany or gedit) directly on the remote file. It behaves the same as a local file would.

dude, that is righteously kewl! I've never seen that before. Thanks!

---

### Post by sam1948 on 2009-03-27
i'm not sure it'll work but..
try working with _Emacs_ 
it's a very complete editor for non x environment
all the key bindings are different then in  xserver but it still learnable

---

### Post by Dr Small on 2009-03-27
I always open a ssh connection to the server, and use vim to edit my files (who needs copy and paste anyway?). But of course you can use copy and paste...

But, if you want to open files locally on the remote machine, use SSHFS, mount the directory to your local filesystem, and edit away. :)

---

### Post by ja660k on 2009-03-27
This is off topic but im having trouble with java on this machine...

thats why im doing everything remotely 

the error im getting is
```

ja660k@FluxXx:~/Desktop/uni/sem3/p3/servlets$javac SocketTest.java 
----------
1. ERROR in SocketTest.java (at line 11)
	Scanner in = new Scanner(inStream);
	^^^^^^^
Scanner cannot be resolved to a type
----------
2. ERROR in SocketTest.java (at line 11)
	Scanner in = new Scanner(inStream);
	                 ^^^^^^^
Scanner cannot be resolved to a type
----------
2 problems (2 errors)ja660k@FluxXx:~/Desktop/uni/sem3/p3/servlets$


```

but when i compile it anywhere else it works?
so its my java thats playing up

---

### Post by doas777 on 2009-03-27
> **ja660k said:**
> This is off topic but im having trouble with java on this machine...

thats why im doing everything remotely 

the error im getting is
```

ja660k@FluxXx:~/Desktop/uni/sem3/p3/servlets$javac SocketTest.java 
----------
1. ERROR in SocketTest.java (at line 11)
	Scanner in = new Scanner(inStream);
	^^^^^^^
Scanner cannot be resolved to a type
----------
2. ERROR in SocketTest.java (at line 11)
	Scanner in = new Scanner(inStream);
	                 ^^^^^^^
Scanner cannot be resolved to a type
----------
2 problems (2 errors)ja660k@FluxXx:~/Desktop/uni/sem3/p3/servlets$


```

but when i compile it anywhere else it works?
so its my java thats playing up

scanner is new to java 1.5. my guess is your javac is 1.42
what do you get from ```
javac -version
```?

---

### Post by ja660k on 2009-03-27
i get this:
```

ja660k@FluxXx:~/Desktop/uni/sem3/p3/servlets$javac -version
Eclipse Java Compiler v_774_R33x, 3.3.1, Copyright IBM Corp 2000, 2007. All rights reserved.

```

---

### Post by doas777 on 2009-03-27
are you compiling via eclipse or cli?
if so, what does it say under Windows -> Preferences -> Java -> Compiler -> JDK compliance?

if your compiling via cli, I'd recomend installing the sun jdk
```

sudo apt-get install sun-java6-jdk

```

---

### Post by ja660k on 2009-03-27
JDK compliance: compliance level = 5.0 and
its using the default compliance settings

as for the apt-get i get this output
```
ja660k@FluxXx:~/Desktop/uni/sem3/p3/servlets$sudo apt-get install sun-java6-jdk 
sudo: unable to resolve host FluxXx
[sudo] password for ja660k: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jdk is already the newest version.
The following packages were automatically installed and are no longer required:
  libwww-ssl0 libraptor1 amaya-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up sun-java6-doc (6-07-3ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
```

---

### Post by doas777 on 2009-03-27
ok, go ahead and abort. the java compiler is already installed and you don't need documentation on your server. 

type 
```

ls -l `which javac`

```
to determine where it is. javac is just a shortcut to the systems specific compiler. ls -l should print somthing like
"lrwxrwxrwx 1 root root 23 2008-11-11 13:45 /usr/bin/javac -> /etc/alternatives/javac"
the part after the '->' is location the link points to. in my case, it's another shortcut, so i went to '/etc/alternatives/' and found that the final destination is '/usr/lib/jvm/java-6-openjdk/bin/javac'

if I wanted to use this version of javac manually I thing i would just use the full path.
```

/usr/lib/jvm/java-6-openjdk/bin/javac ./*.java 

``` or whatever.

---

### Post by ja660k on 2009-03-27
so can i just make an alias in my .bashrc so javac points to

/usr/lib/jvm/java-6-openjdk/bin/javac ./*.java?

or what should i do to change it?
and in that directory i dont have javac?
```

/usr/lib/jvm/java-6-openjdk/bin/
java                javaws              orbd                pluginappletviewer  rmid                servertool          unpack200           
java-rmi.cgi        keytool             pack200             policytool          rmiregistry         tnameserv           

```

---

### Post by doas777 on 2009-03-27
> **ja660k said:**
> so can i just make an alias in my .bashrc so javac points to

/usr/lib/jvm/java-6-openjdk/bin/javac ./*.java?

or what should i do to change it?
the ./*.java is just somthing I do to compile all .java files in the current directory. you probably won't want to put that in an the alias. 
try just '/usr/lib/jvm/java-6-openjdk/bin/javac' but make sure that that is actually where the version you want is.

---

### Post by ja660k on 2009-03-27
usr/lib/jvm/java-6-openjdk/bin/javac
in that directory i dont have javac?
```

/usr/lib/jvm/java-6-openjdk/bin/
java                javaws              orbd                pluginappletviewer  rmid                servertool          unpack200           
java-rmi.cgi        keytool             pack200             policytool          rmiregistry         tnameserv           

```

---

### Post by doas777 on 2009-03-27
ok, whats the output of:
```

ls -l `which javac`

```

---

### Post by ja660k on 2009-03-27
```
ja660k@FluxXx:~$ls -l `which javac`
lrwxrwxrwx 1 root root 23 2008-12-04 17:35 /usr/bin/javac -> /etc/alternatives/javac
ja660k@FluxXx:~$

```
and that points to
```

$ls -l /etc/alternatives/javac
lrwxrwxrwx 1 root root 31 2009-02-15 19:33 /etc/alternatives/javac -> /usr/lib/jvm/java-gcj/bin/javac

```

i found this...
```

ja660k@FluxXx:~$/usr/lib/jvm/java-6-sun/bin/javac -version
javac 1.6.0_07

```

does that look good?

---

### Post by doas777 on 2009-03-27
looks just like mine. try compiling your app

---

### Post by infinitejones on 2009-03-27
> **doas777 said:**
> dude, that is righteously kewl! I've never seen that before. Thanks!

+1! All this time I've been messing around with folders on shared NFS mounts!

---

### Post by ja660k on 2009-03-27
perfect... thanks alot for your help :):)

---

### Post by llamabr on 2009-03-27
> **ja660k said:**
> 
is there a way i can keep alive my remote folders? on logout?


Screen.  You seek screen.

---

