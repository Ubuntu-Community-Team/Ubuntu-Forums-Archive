---
title: "unable to define JAVA_HOME"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by diabolator2 on 2009-10-07
Hi all! Help me define JAVA_HOME, cos I can't and tried all.

I have Ubuntu 9.04. I used Add/Remove... to install Eclipse and Sun Java 6 Runtime (OpenJDK Java 6 Web Start and OpenJDK Java 6 Runtime are also installed). I try to use Eclipse with OpenXava's workspace. At a moment I have to start my database server: from command line I go to openxava-3.x/tomcat/bin folder and execute 

               ./start-hsqldb.sh management-db 1666

and I got this: 

Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program

the command  export JAVA_HOME=/PATH TO JDK/ does'n work. Actually, I have sevaral java folders in /usr/lib/jvm but none of them work. I also have a jdk1.6.0_16 installed from jdk-6u16-linux-i586.bin(downloaded by myself),this doesn't work too. 

Please help! Thanks!

---

### Post by Mighty_Joe on 2009-10-07
> **diabolator2 said:**
> Hi all! Help me define JAVA_HOME, cos I can't and tried all.


*Exactly *what have you tried?  
What do you get if you execute "java -version"?
What do you get if you execute "sudo update-java-alternatives -l"?

---

### Post by diabolator2 on 2009-10-07
look what I've got:

cristi@book:~$ java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu11)
OpenJDK Client VM (build 14.0-b08, mixed mode, sharing)
cristi@book:~$ sudo update-java-alternatives -l
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun
java-gcj 1042 /usr/lib/jvm/java-gcj

---

### Post by nathanagood@yahoo.com on 2009-10-07
@diabolator2:

You didn't mention if you run:

$ export JAVA_HOME=/usr/lib/jvm/java-6-openjdk

From the same command window in which you run the command:

$ ./start-hsqldb.sh management-db 1666

This is important, so make sure you are NOT opening one window and typing the first command and then typing the second command in another window.  The variable will not be set across different instances of the terminal, and will go away when you close a terminal window.

To verify, right before trying to start hsqldb, type:

$ echo $JAVA_HOME

If it prints nothing, you know the variable isn't set correctly.  If it prints something, then the path probably isn't correct.  The Java home should not include "bin" at the end, but "bin" should be in the directory defined by $JAVA_HOME.  So "$JAVA_HOME/bin/java" should resolve to a command (if defined correctly, you should be able to run that from the command line).  

It's usually best if it's the same version you get when you run "java -version" from the command line, unless you know why it should be different.

---

### Post by diabolator2 on 2009-10-08
ok, look what I've got, in a single terminal:

cristi@book:~$ export JAVA_HOME=/usr/lib/jvm/java-6-openjdk
cristi@book:~$ echo $JAVA_HOME
/usr/lib/jvm/java-6-openjdk
cristi@book:~$ cd /media/Work/a/openxava-3.1.4/tomcat/bin/
cristi@book:/media/Work/a/openxava-3.1.4/tomcat/bin$ sudo ./start-hsqldb.sh management-db 1666
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program
cristi@book:/media/Work/a/openxava-3.1.4/tomcat/bin$ 

Maybe I should download another JDK version?

---

### Post by nathanagood@yahoo.com on 2009-10-08
Your problem is here:

$ **sudo** ./start-hsqldb.sh management-db 1666

When you run sudo, it runs the script as a different user (root).  Your environment variables don't go across user boundries.  To prove this out, right before running the script, define it for yourself and then run:

$ sudo echo $JAVA_HOME

---

### Post by diabolator2 on 2009-10-08
did you mean to do this way?

cristi@book:~$ export JAVA_HOME=/usr/lib/jvm/java-6-openjdk
cristi@book:~$ sudo echo $JAVA_HOME
/usr/lib/jvm/java-6-openjdk
cristi@book:~$ cd /media/Work/a/openxava-3.1.4/tomcat/bin/
cristi@book:/media/Work/a/openxava-3.1.4/tomcat/bin$ sudo ./start-hsqldb.sh management-db 1666
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program
cristi@book:/media/Work/a/openxava-3.1.4/tomcat/bin$

Wow, late entry, I've just tried ./start-hsqldb.sh management-db 1666 without sudo: 

cristi@book:/media/Work/a/openxava-3.1.4/tomcat/bin$ ./start-hsqldb.sh management-db 1666
[Server@19b49e6]: [Thread[main,5,main]]: checkRunning(false) entered
[Server@19b49e6]: [Thread[main,5,main]]: checkRunning(false) exited
[Server@19b49e6]: Startup sequence initiated from main() method
[Server@19b49e6]: Loaded properties from [/media/Work/a/openxava-3.1.4/tomcat/bin/server.properties]
[Server@19b49e6]: Initiating startup sequence...
[Server@19b49e6]: Server socket opened successfully in 8 ms.
[Server@19b49e6]: Database [index=0, id=0, db=file:.././data/management-db, alias=] opened sucessfully in 313 ms.
[Server@19b49e6]: Startup sequence completed in 330 ms.
[Server@19b49e6]: 2009-10-08 15:55:16.375 HSQLDB server 1.8.0 is online
[Server@19b49e6]: To close normally, connect and execute SHUTDOWN SQL
[Server@19b49e6]: From command line, use [Ctrl]+[C] to abort abruptly

It seems everything runs ok! Thanks, man!

---

### Post by nathanagood@yahoo.com on 2009-10-08
Sorry about that, I gave you a flawed test (I didn't run it--I went by memory--lesson learned there!).  The sudo answer is still correct, though.  I verified that this test shows the correct scenario.  Given a shell script:

#!/bin/bash
echo $FOO

If I type:

$ export FOO=bar
$ sudo ./myscript.sh

Output:

<nothing>

---

### Post by nathanagood@yahoo.com on 2009-10-08
You can get this to work a couple different ways.  Each of them have their advantages and disadvantages, but I would suggest this:

Create a light wrapper script.  Considering my example in my last post, this script:

#!/bin/bash

export FOO=bar
./myscript.sh

Will output, when run as sudo:

bar

---

### Post by diabolator2 on 2009-10-08
Err... look, Nathan(or I dunno your name), you a talking to a seriously GREEN Ubuntu user, maybe I could follow your advice if you'll explain what to do step by step. Till here, thanks!

---

### Post by nathanagood@yahoo.com on 2009-10-08
No problem.

Use your favorite editor (gedit, whatever), to create a new file, and put this code into your new file:

[FONT="Courier New"]#!/bin/bash

export JAVA_HOME=/usr/lib/jvm/java-6-openjdk
cd /media/Work/a/openxava-3.1.4/tomcat/bin/
./start-hsqldb.sh management-db 1666

# end script[/FONT]

Make sure to include the first line (#!/bin/bash).  Save the file as something like "hsqldb-start.sh" or any other name that is meaningful to you, in a directory you want.  You've just created a shell script, which is nothing more than a text file that is run line-by-line as if you were putting the commands yourself into the terminal.  Before you can run the script, you need to make it executable.  The easiest way to do that is this:

$ cd <the location you saved it>
$ chmod 755 hsqldb-start.sh

Now you can run the script, as sudo:

$ sudo ./hsqldb-start.sh

Does that help?

*Edit:  I just noticed the other post about your non-sudo working.  That's great!  You can use this advice for future reference in case you ever need it, but I would recommend running it as a non-root user if you have the permissions to do so.  The typical rule of thumb is NOT to run things with any more elevated permissions than what is absolutely necessary!*

---

### Post by diabolator2 on 2009-10-09
well, I've named the script burst.sh, but take a look:

cristi@book:/media/Work/a/openxava-3.1.4/tomcat/bin$ sudo burst.sh
[sudo] password for cristi: 
sudo: burst.sh: command not found
cristi@book:/media/Work/a/openxava-3.1.4/tomcat/bin$

I tried to doubleclic burst.sh and notind except "Run in Terminal" goes. BUT, the terminal appears for a second and dissapears away. Althow, I could notice that something was going on in that terminal, I guess the server is started. Now I tried to see my project's result (I have to open a localhost for it) and got "could not connect to remote bla, bla, bla", it means, the server is not running. I tried to run ./start-hsqldb.sh managementdb 1666 and look: 

cristi@book:/media/Work/a/openxava-3.1.4/tomcat/bin$ ./start-hsqldb.sh management-db 1666
[Server@83cc67]: [Thread[main,5,main]]: checkRunning(false) entered
[Server@83cc67]: [Thread[main,5,main]]: checkRunning(false) exited
[Server@83cc67]: Startup sequence initiated from main() method
[Server@83cc67]: Loaded properties from [/media/Work/a/openxava-3.1.4/tomcat/bin/server.properties]
[Server@83cc67]: Initiating startup sequence...
[Server@83cc67]: [Thread[HSQLDB Server @83cc67,5,main]]: run()/openServerSocket(): 
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.PlainSocketImpl.bind(PlainSocketImpl.java:365)
	at java.net.ServerSocket.bind(ServerSocket.java:319)
	at java.net.ServerSocket.<init>(ServerSocket.java:185)
	at java.net.ServerSocket.<init>(ServerSocket.java:97)
	at org.hsqldb.HsqlSocketFactory.createServerSocket(Unknown Source)
	at org.hsqldb.Server.openServerSocket(Unknown Source)
	at org.hsqldb.Server.run(Unknown Source)
	at org.hsqldb.Server.access$000(Unknown Source)
	at org.hsqldb.Server$ServerThread.run(Unknown Source)
[Server@83cc67]: Initiating shutdown sequence...
[Server@83cc67]: Shutdown sequence completed in 12 ms.
[Server@83cc67]: 2009-10-09 14:51:20.553 SHUTDOWN : System.exit() is called next
cristi@book:/media/Work/a/openxava-3.1.4/tomcat/bin$

Maybe you could read the above and say this in english? :)
Note: Whatever the the problem is, all get's to normal after a reboot. see you.

---

### Post by Mighty_Joe on 2009-10-13
> **diabolator2 said:**
> 
java.net.BindException: Address already in use


Some program, like another instance of hsqldb, is already running and is bound to port 1666.  Since it is fine after a reboot, my guess is that you ran your startup script twice without shutting down the database.

---

