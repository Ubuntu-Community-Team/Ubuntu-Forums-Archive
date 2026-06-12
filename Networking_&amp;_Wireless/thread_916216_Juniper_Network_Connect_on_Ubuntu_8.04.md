---
title: "Juniper Network Connect on Ubuntu 8.04"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by rpug on 2008-09-10
Hi everyone,

Has anyone had any luck getting Juniper Network Connect to work under Ubuntu 8.04?  I tried to use madscientist's script ([http://mad-scientist.us/juniper.html](http://mad-scientist.us/juniper.html)), but I can't even get the java applet to install.  The java applet fails with the following error

java.lang.ClassFormatError: Incompatible magic value 171731060 in class file SecureNCLauncher
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:192)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:127)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:632)
	at sun.applet.AppletPanel.createApplet(AppletPanel.java:786)
	at sun.plugin.AppletViewer.createApplet(AppletViewer.java:2108)
	at sun.applet.AppletPanel.runLoader(AppletPanel.java:715)
	at sun.applet.AppletPanel.run(AppletPanel.java:369)
	at java.lang.Thread.run(Thread.java:619)


I'm using Firefox 3 and the sun-java6-jre.  Any thoughts?

---

### Post by rpug on 2008-09-11
Apparently, if I run Firefox as root and then go to the page, the applet loads fine.  The Juniper applet must not be smart enough to seek SU access.

---

### Post by chengt on 2008-11-04
I'm getting the same message but running firefox as root didn't help.

This is using:
Java Plug-in 1.6.0_10
Using JRE version 1.6.0_10 Java HotSpot(TM) Client VM

```

java.lang.ClassFormatError: Incompatible magic value 171731060 in class file SecureNCLauncher
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:621)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:192)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:127)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:632)
	at sun.applet.AppletPanel.createApplet(AppletPanel.java:785)
	at sun.plugin.AppletViewer.createApplet(AppletViewer.java:2302)
	at sun.applet.AppletPanel.runLoader(AppletPanel.java:714)
	at sun.applet.AppletPanel.run(AppletPanel.java:368)
	at java.lang.Thread.run(Thread.java:619)
Ignored exception: java.lang.ClassFormatError: Incompatible magic value 171731060 in class file SecureNCLauncher

```

It looks like an error from using the wrong version of java but that is strange since I'm using the latest public release.

---

### Post by sapg on 2009-04-12
Did anyone figure out the solution to this?  I'm on 8.10 and I have exactly the same problem, I've tried everything I've found on Google, nothing worked.  I'm also on 1.6.0_10.

Thanks

---

### Post by ejjp on 2009-07-08
It seems that the madscientist script does not get the connection at last.

Try it. you have to ensure that you have the .vpn.crt file in your $HOME.
(use the madscientist script, this part works)

Fill the variables according your requeriments in this script

#!/bin/bash
#
# script for connection into a vpn with juniper
############################
#
cd
#Set your values below
HOSTVPN=
USERVPN=
REALMVPN=
CERTVPN=~/.vpn.crt
#introduce the password
echo "vpn password?:"
read -s PW
#
cd ~/.juniper_networks/network_connect 
sudo ./ncsvc -h $HOSTVPN -u $USERVPN -p $PW -r $REALMVPN -f $CERTVPN 


execute the script above and you can see the next message:
Connecting to $HOSTVPN : 443

You will see (ifconfign -> tun0 or checking the ip) that the connection is ok.

When Ctrl+C of close the terminal window the vpn connection will be closed. 


Acknoledgments:
[http://www.entropy.ch/blog/Mac+OS+X/?permalink=Juniper-Network-Connect-SSL-VPN-and-Virtualization.html](http://www.entropy.ch/blog/Mac+OS+X/?permalink=Juniper-Network-Connect-SSL-VPN-and-Virtualization.html)

---

