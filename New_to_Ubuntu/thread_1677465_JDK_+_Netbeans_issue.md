---
title: "JDK + Netbeans issue"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by todayisgood on 2011-01-28
I tried installing the jdk bin file available on the official site, got  it into the terminal, it unpacked and basically was installed but then  when I'm trying to install Netbeans it says this:

> Configuring the installer...
Searching for JVM on the system...
Java SE Development Kit (JDK) was not found on this computer
JDK 6 is required for installing the NetBeans IDE. Make sure that the JDK is properly installed and run installer again.
You can specify valid JDK location using --javahome installer argument.

To download the JDK, visit [http://java.sun.com/javase/downloads](http://java.sun.com/javase/downloads)
How do I specify the javahome installer argument on the line

> sh netbeans-6.9.1-ml-linux.shwhich is what I'm doing to install?

---

### Post by YesWeCan on 2011-01-28
The easy way is to download a NetBeans+JDK bundle...the .sh type so you get a friendly installation GUI. With a bundle there are no location issues.

It may be the location of your JDK installation is not in one of your standard search paths: 'echo $PATH' to see. So it may be that NB has looked in the PATH locations but not found the JDK.
Either add the JDK path to PATH or make a symbolic link to it:
ln -s /blah/blah/jdk6... /home/you/jdk
Or something similar. /home/you/ is in your PATH by default.

I had this problem. I had installed the JDK in /home/brian/Programming. I had to add the 
Programming directory to my PATH. This is called an environment variable. Check the Ubuntu site for how to change environment variables.

More recently, I installed jre, jdk and NetBeans in /opt. I then added symbolic links to them in /usr/local/bin, which is in all users' paths by default.

---

### Post by todayisgood on 2011-01-28
> **YesWeCan said:**
> The easy way is to download a NetBeans+JDK bundle...the .sh type so you get a friendly installation GUI. With a bundle there are no location issues.

It may be the location of your JDK installation is not in one of your standard search paths: 'echo $PATH' to see. So it may be that NB has looked in the PATH locations but not found the JDK.
Either add the JDK path to PATH or make a symbolic link to it:
ln -s /blah/blah/jdk6... /home/you/jdk
Or something similar. /home/you/ is in your PATH by default.

I had this problem. I had installed the JDK in /home/brian/Programming. I had to add the 
Programming directory to my PATH. This is called an environment variable. Check the Ubuntu site for how to change environment variables.

More recently, I installed jre, jdk and NetBeans in /opt. I then added symbolic links to them in /usr/local/bin, which is in all users' paths by default.

Sorry, I'm not really sure what you're talking about. Could you show an example of what I should put in the terminal?

---

### Post by cavh on 2011-01-29
See the *update-alternatives-java* command description here: 

[https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

---

### Post by YesWeCan on 2011-01-29
No problem.

1) You can tell NetBeans where the jdk directory is. Eg at the command terminal:

netbeans --jdkhome /home/brian/Programming/jdk1.6.0_23/

2) You can add the jdk directory's parent directory to your PATH. Eg at the command terminal

PATH=$PATH:/home/brian/Programming
export PATH

3) You can create a symbolic link to the jdk driectory from a location already within your PATH, eg

ln -s /home/brian/Programming/jdk1.6.0_23/ /home/brian/jdk

4) You can avoid all this by installing the NetBeans+JDK bundle. Uninstall your existing netbeans and kdk first.
The Netbeans+JDK bundle is here: [http://www.oracle.com/technetwork/java/javase/downloads/jdk-netbeans-jsp-142931.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk-netbeans-jsp-142931.html)

---

### Post by YesWeCan on 2011-01-29
Sorry, I just read your original post properly! Option 1) will only work once NetBeans is installed. So you should try option 2. This will give the NetBeans installer program the location of your jdk directory and then it should be happy.
But if you get really stuck then just download the bundle.


I think the problem here is that you have inadvertently installed the JDK in a location that is not a "standard" application location. This is not wrong at all but, in linux, things don't work like they do in Windows. There isn't a registry as such that keeps track of all your installations and where they are. Instead, there are specific file paths that executable application files normally reside in. The Java and NetBeans install scripts don't pay attention to this and install wherever they think you want them to at the time.
If you type 'echo $PATH' in a terminal you will see the standard paths where applications are usually located.

---

