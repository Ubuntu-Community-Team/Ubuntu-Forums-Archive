---
title: "Trying to find a way to run a .bat file in ubuntu 9.04?"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by marshalmike9 on 2009-07-14
Hi,

I'm trying to run this batch file (for a game) and I am willing to do all steps provided to get it to work. I think I might have to make a .sh file out of it? I don't know anything about ubuntu so please be clear with instructions, here is wat the "code" is when i try to open the batch file.

@ECHO OFF 
TITLE Sanity 
java -Xmx500m -cp .;Theme.jar Gui

---

### Post by CatKiller on 2009-07-14
You're right that .bat (batch) files are the DOS equivalents of shell scripts (.sh). That file is barely a batch file, though. The only command in there is the last line. I'd imagine that you can just run that.

---

### Post by jerome1232 on 2009-07-14
wine can do it, I believe you do "wineconsole" then cd to the bat file and run it.

edit: It's changed
```
wine cmd "/path/to/batch/file"
```

---

### Post by marshalmike9 on 2009-07-14
> **jerome1232 said:**
> wine can do it, I believe you do "wineconsole" then cd to the bat file and run it.

edit: It's changed
```
wine cmd "/path/to/batch/file"
```
im an absolute linux noob, so im sorry but ok i type in wine cmd and then it just stays in the terminal is another page supposed to open up? or am i supposed to do something within the terminal? im really sorry!

---

### Post by jerome1232 on 2009-07-14
If you just typed "wine cmd" then you should get a new dos style prompt (like this)

```
jeremy@psion:~$ wine cmd
CMD Version 1.0.1

Z:\home\jeremy>

```

let's say your bat file is sitting on your desktop and it's named amazinggame.bat, this is how you would run it

```
jeremy@psion:~$ wine cmd
CMD Version 1.0.1

Z:\home\jeremy>cd Desktop
Z:\home\jeremy\Desktop>amazinggame.bat
```

edit: If you ran "wine cmd" and you got a response about the programe wine not being found, then you just need to install wine then run it. To install wine you would do this.

```
sudo apt-get install wine
```

---

### Post by marshalmike9 on 2009-07-14
> **jerome1232 said:**
> If you just typed "wine cmd" then you should get a new dos style prompt (like this)

```
jeremy@psion:~$ wine cmd
CMD Version 1.0.1

Z:\home\jeremy>

```let's say your bat file is sitting on your desktop and it's named amazinggame.bat, this is how you would run it

```
jeremy@psion:~$ wine cmd
CMD Version 1.0.1

Z:\home\jeremy>cd Desktop
Z:\home\jeremy\Desktop>amazinggame.bat
```edit: If you ran "wine cmd" and you got a response about the programe wine not being found, then you just need to install wine then run it. To install wine you would do this.

```
sudo apt-get install wine
```
Ok, thanks i understand it now but its still not working! this is exactly what i did.


michael@michael-laptop:~$ wine cmd
CMD Version 1.0.1

Z:\home\michael>cd desktop
Z:\home\michael\Desktop>cd Game
Z:\home\michael\Desktop\Game>Run.bat
File not found

Z:\home\michael\Desktop\Game>^Cmichael@michael-laptop:~$ 



idk why it is saying file not found!

---

### Post by jerome1232 on 2009-07-14
Well that batch file does seem to be doing something with java (I'm not familiar enough with java commands to know what that line actually does) 

Out of curiosity what are the contents of that games directory? Are there any java files?

```
ls -l ~/Desktop/Game
```

---

### Post by marshalmike9 on 2009-07-14
> **jerome1232 said:**
> Well that batch file does seem to be doing something with java (I'm not familiar enough with java commands to know what that line actually does) 

Out of curiosity what are the contents of that games directory? Are there any java files?

```
ls -l ~/Desktop/Game
```
Yeah it is a Java based game. what is that code you just sent?

---

### Post by jerome1232 on 2009-07-14
ls it lists out the contents of a directory, similar to dir in windows.

---

### Post by marshalmike9 on 2009-07-14
> **jerome1232 said:**
> ls it lists out the contents of a directory, similar to dir in windows.
ok well here are the contents

-rw-r--r-- 1 michael michael    2006 2009-05-22 16:03 A.class
-rw-r--r-- 1 michael michael     371 2009-05-22 16:03 AI.class
-rw-r--r-- 1 michael michael     872 2009-05-22 16:03 AZ.class
-rw-r--r-- 1 michael michael    4973 2009-05-22 16:03 B.class
-rw-r--r-- 1 michael michael    2657 2009-05-22 16:03 BI.class
-rw-r--r-- 1 michael michael    1648 2009-05-22 16:03 BZ.class
drwxr-xr-x 3 michael michael    4096 2009-05-22 16:01 cache
-rw-r--r-- 1 michael michael     248 2009-05-22 16:03 C.class
-rw-r--r-- 1 michael michael   11435 2009-05-22 16:03 CI.class
-rw-r--r-- 1 michael michael    3604 2009-05-22 16:03 CZ.class
-rw-r--r-- 1 michael michael    1377 2009-05-22 16:03 D.class
-rw-r--r-- 1 michael michael   16521 2009-05-22 16:03 DI.class
-rw-r--r-- 1 michael michael     203 2009-05-22 16:03 DZ.class
-rw-r--r-- 1 michael michael    1718 2009-05-22 16:03 E.class
-rw-r--r-- 1 michael michael    2167 2009-05-22 16:03 EI.class
-rw-r--r-- 1 michael michael    6403 2009-05-22 16:03 EZ.class
-rw-r--r-- 1 michael michael    4546 2009-05-22 16:03 F.class
-rw-r--r-- 1 michael michael    5581 2009-05-22 16:03 FI.class
-rw-r--r-- 1 michael michael    1234 2008-08-12 11:11 FileOperations.class
drwxr-xr-x 3 michael michael    4096 2009-05-22 15:27 Files
-rw-r--r-- 1 michael michael    8183 2009-05-22 16:03 FZ.class
-rw-r--r-- 1 michael michael     408 2009-05-22 16:03 G.class
-rw-r--r-- 1 michael michael    1762 2009-05-22 16:03 GI.class
-rw-r--r-- 1 michael michael    6598 2009-05-22 16:03 Gui.class
-rw-r--r-- 1 michael michael     354 2009-05-22 16:03 GZ.class
-rw-r--r-- 1 michael michael     986 2009-05-22 16:03 H.class
-rw-r--r-- 1 michael michael    4884 2009-05-22 16:03 HI.class
-rw-r--r-- 1 michael michael     686 2009-05-22 16:03 HZ.class
-rw-r--r-- 1 michael michael    8085 2009-05-22 16:03 I.class
-rw-r--r-- 1 michael michael     245 2009-05-22 16:03 II.class
-rw-r--r-- 1 michael michael    1883 2009-05-22 16:03 IZ.class
-rw-r--r-- 1 michael michael    2797 2009-05-22 16:03 J.class
-rw-r--r-- 1 michael michael    7039 2009-05-22 16:03 JI.class
-rw-r--r-- 1 michael michael     349 2009-05-22 16:03 JZ.class
-rw-r--r-- 1 michael michael     724 2009-05-22 16:03 K.class
-rw-r--r-- 1 michael michael     327 2009-05-22 16:03 KI.class
-rw-r--r-- 1 michael michael     217 2009-05-22 16:03 KZ.class
-rw-r--r-- 1 michael michael    1940 2009-05-22 16:03 L.class
-rw-r--r-- 1 michael michael    1376 2009-05-22 16:03 LI.class
-rw-r--r-- 1 michael michael    4632 2009-05-22 16:03 LZ.class
-rw-r--r-- 1 michael michael     342 2009-05-22 16:03 M.class
-rw-r--r-- 1 michael michael    2159 2009-05-22 16:03 MI.class
drwxr-xr-x 6 michael michael   12288 2009-05-22 15:27 models
-rw-r--r-- 1 michael michael    2278 2009-05-22 16:03 MZ.class
-rw-r--r-- 1 michael michael    2227 2009-05-22 16:03 N.class
-rw-r--r-- 1 michael michael    1501 2009-05-22 16:03 NI.class
-rw-r--r-- 1 michael michael    3535 2009-05-22 16:03 NZ.class
-rw-r--r-- 1 michael michael    2183 2009-05-22 16:03 O.class
-rw-r--r-- 1 michael michael   19634 2009-05-22 16:03 OI.class
-rw-r--r-- 1 michael michael   14336 2009-05-22 16:03 OZ.class
-rw-r--r-- 1 michael michael    2681 2009-05-22 16:03 P.class
-rw-r--r-- 1 michael michael     593 2009-05-22 16:03 PI.class
-rw-r--r-- 1 michael michael   58261 2009-05-22 16:03 PZ.class
-rw-r--r-- 1 michael michael   25517 2009-05-22 16:03 Q.class
-rw-r--r-- 1 michael michael    3459 2009-05-22 16:03 QI.class
-rw-r--r-- 1 michael michael   63609 2009-05-22 16:03 QZ.class
-rw-r--r-- 1 michael michael     240 2009-05-22 16:03 R.class
-rw-r--r-- 1 michael michael    1323 2009-05-22 16:03 RI.class
-rw-r--r-- 1 michael michael      58 2009-04-20 15:53 Run.bat
-rw-r--r-- 1 michael michael     690 2009-05-22 16:03 RZ.class
-rw-r--r-- 1 michael michael    2114 2009-05-22 16:03 S.class
-rw-r--r-- 1 michael michael     212 2009-05-22 16:03 SI.class
drwxr-xr-x 2 michael michael    4096 2009-05-22 16:00 sign
drwxr-xr-x 6 michael michael    4096 2009-05-22 15:27 Sprites
-rw-r--r-- 1 michael michael    1318 2009-05-22 16:03 SZ.class
-rw-r--r-- 1 michael michael     436 2009-05-22 16:03 T.class
-rw-r--r-- 1 michael michael 1777876 2009-02-07 17:02 Theme.jar
-rw-r--r-- 1 michael michael     186 2009-05-22 16:03 TI.class
-rw-r--r-- 1 michael michael    1805 2009-05-22 16:03 TZ.class
-rw-r--r-- 1 michael michael     312 2009-05-22 16:03 U.class
-rw-r--r-- 1 michael michael    9040 2009-05-22 16:03 UI.class
-rw-r--r-- 1 michael michael     599 2009-05-22 16:03 UZ.class
-rw-r--r-- 1 michael michael    1099 2009-05-22 16:03 V.class
-rw-r--r-- 1 michael michael    1749 2009-05-22 16:03 VI.class
-rw-r--r-- 1 michael michael  141315 2009-05-22 16:03 VZ.class
-rw-r--r-- 1 michael michael     240 2009-05-22 16:03 W.class
-rw-r--r-- 1 michael michael    1772 2009-05-22 16:03 WI.class
-rw-r--r-- 1 michael michael     297 2009-05-22 16:03 X.class
-rw-r--r-- 1 michael michael    1355 2009-05-22 16:03 XI.class
-rw-r--r-- 1 michael michael     281 2009-05-22 16:03 Y.class
-rw-r--r-- 1 michael michael    1901 2009-05-22 16:03 YI.class
-rw-r--r-- 1 michael michael    1112 2009-05-22 16:03 Z.class
-rw-r--r-- 1 michael michael    2401 2009-05-22 16:03 ZI.class
-rw-r--r-- 1 michael michael     576 2009-05-22 16:03 ZZ.class

---

### Post by jerome1232 on 2009-07-14
Try what catkiller suggested, running that last command in the batch file

```
cd ~/Desktop/Game
java -Xmx500m -cp .;Theme.jar Gui
```

---

### Post by marshalmike9 on 2009-07-14
> **jerome1232 said:**
> Try what catkiller suggested, running that last command in the batch file

```
cd ~/Desktop/Game
java -Xmx500m -cp .;Theme.jar Gui
```
michael@michael-laptop:~$ cd ~/Desktop/Game
michael@michael-laptop:~/Desktop/Game$ java -Xmx500m -cp .;Theme.jar Gui
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)

where options include:
    -d32          use a 32-bit data model if available

    -d64          use a 64-bit data model if available
    -client      to select the "client" VM
    -server      to select the "server" VM
    -hotspot      is a synonym for the "client" VM  [deprecated]
                  The default VM is client.
                  
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
                  enable assertions
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions
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
bash: Theme.jar: command not found




did i do that right? cause i dont think it worked.

---

