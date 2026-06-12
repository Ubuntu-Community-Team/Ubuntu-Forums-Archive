---
title: "Problem installing Juniper SSL VPN/network connect in Kubuntu 8.04 beta"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by ubunew1124 on 2008-03-30
I upgraded my Kubuntu 7.10 to 8.04 Beta. Juniper SSL VPN/network connect was working in 7.10 based on instructions in another thread esp. from madscientist. However after upgrading to 8.04Beta I have reached a point where the installNC.sh and xlaunchNC.sh don't give
any errors and I am prompted for password by xterm, but I don't
get the network connect window when it launches network connect.

Not sure if anyone tried installing network connect on 8.04 Beta.

--------------------------------
From java debug console: (after clicking on 'network connect')

=========
Launching "/usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/bin/java" "-classpath" "/home/aman/.juniper_networks/network_connect/NC.jar" "NC" "-h" "sa.juniper.net" "-n" "" "-t" "" "-x"
basic: New window ID: 0
basic: Stopping applet ... <--- why??
=========

See more details below:

The 2 'File not found/permission denied' errors below I presume are
 due to the juniper ssl code trying to copy installNC.sh and
 xlaunchNC.sh in the network_connect/ directory but which I have
 run 'chattr +i ' (making them immutable -since juniper scripts are bad)
 and the file copy fails which should not be of concern.

basic: Removed progress listener: sun.plugin.util.GrayBoxPainter@73a7ab
basic: New window ID: 16016e9
basic: Value of xembed: 1
basic: setWindow: call before applet exists:16016e9
basic: Referencing classloader: sun.plugin.ClassLoaderInfo@157aa53, refcount=1
basic: Added progress listener: sun.plugin.util.GrayBoxPainter@6210fb
basic: Loading applet ...
basic: Initializing applet ...
basic: Starting applet ...
basic: Referencing classloader: sun.plugin.ClassLoaderInfo@157aa53, refcount=2
basic: Releasing classloader: sun.plugin.ClassLoaderInfo@157aa53, refcount=1
Calling Super Init.
network: Connecting [https://sa.juniper.net/dana-cached/nc/ncLinuxApp.jar](https://sa.juniper.net/dana-cached/nc/ncLinuxApp.jar) with proxy=DIRECT
security: Loading certificates from Deployment session certificate store
security: Loaded certificates from Deployment session certificate store
network: Connecting [https://sa.juniper.net/dana-cached/nc/ncLinuxApp.jar](https://sa.juniper.net/dana-cached/nc/ncLinuxApp.jar) with cookie "DSSignInURL=/; DSID=57f99e9aefaed44e5d3059661acb0966; DSFirstAccess=1206851709; DSLastAccess=1206851738"
network: Server [https://sa.juniper.net/dana-cached/nc/ncLinuxApp.jar](https://sa.juniper.net/dana-cached/nc/ncLinuxApp.jar) requesting to set-cookie with "DSLastAccess=1206851740; path=/; Secure"
/home/aman/.juniper_networks
File not found
java.io.FileNotFoundException: /home/aman/.juniper_networks/network_connect/installNC.sh (Permission denied)
        at java.io.FileOutputStream.open(Native Method)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:179)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:131)
        at FileUtil.copyFile(FileUtil.java:188)
        at FileUtil.copyFile(FileUtil.java:176)
        at FileUtil.copyFile(FileUtil.java:171)
        at InstallNC.copyFile(InstallNC.java:43)
        at InstallNC.main_run(InstallNC.java:91)
        at SecureNCLauncher.RunTargetApp(SecureNCLauncher.java:251)
        at SecureLauncherApplet.startTargetApp(SecureLauncherApplet.java:358)
        at SecureLauncherApplet.doInstall(SecureLauncherApplet.java:214)
        at SecureLauncherApplet.start(SecureLauncherApplet.java:194)
        at sun.applet.AppletPanel.run(AppletPanel.java:420)
        at java.lang.Thread.run(Thread.java:595)
File not found
java.io.FileNotFoundException: /home/aman/.juniper_networks/network_connect/xlaunchNC.sh (Permission denied)
        at java.io.FileOutputStream.open(Native Method)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:179)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:131)
        at FileUtil.copyFile(FileUtil.java:188)
        at FileUtil.copyFile(FileUtil.java:176)
        at FileUtil.copyFile(FileUtil.java:171)
        at InstallNC.copyFile(InstallNC.java:43)
        at InstallNC.main_run(InstallNC.java:92)
        at SecureNCLauncher.RunTargetApp(SecureNCLauncher.java:251)
        at SecureLauncherApplet.startTargetApp(SecureLauncherApplet.java:358)
        at SecureLauncherApplet.doInstall(SecureLauncherApplet.java:214)
        at SecureLauncherApplet.start(SecureLauncherApplet.java:194)
        at sun.applet.AppletPanel.run(AppletPanel.java:420)
        at java.lang.Thread.run(Thread.java:595)
Here is the standard output of the command:

No difference found
Here is the standard error of the command (if any):

in get Proxy info..
No Proxy configured to for [http://sa.juniper.net/](http://sa.juniper.net/)
linux_start_script=
linux_end_script=
para 0 is /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/bin/java
para 1 is -classpath
para 2 is /home/aman/.juniper_networks/network_connect/NC.jar
para 3 is NC
para 4 is -h
para 5 is sa.juniper.net
para 6 is -n
para 7 is
para 8 is -t
para 9 is
para 10 is -x
liveconnect: the url of the applet is [https://sa.juniper.net](https://sa.juniper.net) and the permission is = true
liveconnect: JSObject::getMember: name=document
liveconnect: the url of the applet is [https://sa.juniper.net](https://sa.juniper.net) and the permission is = true
liveconnect: JSObject::getMember: name=cookie
liveconnect: the url of the applet is [https://sa.juniper.net](https://sa.juniper.net) and the permission is = true
DSID=57f9
Launching "/usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/bin/java" "-classpath" "/home/aman/.juniper_networks/network_connect/NC.jar" "NC" "-h" "sa.juniper.net" "-n" "" "-t" "" "-x"
basic: New window ID: 0
basic: Stopping applet ... <--- why??
basic: Finding information ...
basic: Releasing classloader: sun.plugin.ClassLoaderInfo@157aa53, refcount=0
basic: Caching classloader: sun.plugin.ClassLoaderInfo@157aa53
basic: Current classloader cache size: 2
basic: Done ...
basic: Removed progress listener: sun.plugin.util.GrayBoxPainter@6210fb
basic: Destroying applet ...
basic: Disposing applet ...
basic: Quiting applet ...
basic: Joining applet thread ...
----------------------------------------------------

DIrectories:

.:
total 572
-rw-r--r-- 1 aman aman  48272 2008-03-29 21:35 dsHCLauncher_linux1.log
-rw-r--r-- 1 aman aman      6 2008-03-29 21:35 hcport.txt
-rw-r--r-- 1 aman aman 137845 2007-12-25 22:28 hostchecker.jar
-rw-r--r-- 1 aman aman 375118 2007-12-25 22:14 ncLinuxApp.jar
drwxr-xr-x 2 aman aman   4096 2008-03-29 21:35 network_connect
drwxr-xr-x 3 aman aman   4096 2008-03-29 21:35 tmp

./network_connect:
total 912
-rw-r--r-- 1 aman aman    329 2008-03-29 21:35 installnc.log
-rwxr--r-- 1 aman aman    730 2008-03-29 01:15 installNC.sh
-rw-r--r-- 1 aman aman 493680 2008-03-29 21:35 libncui.so
-rw-r--r-- 1 aman aman      0 2008-03-29 21:35 missing.info
-rwxr--r-- 1 aman aman  24888 2008-03-29 21:35 ncdiag
-rwxrwxrwx 1 aman aman  45478 2008-03-29 21:35 NC.jar
-rws--s--x 1 root root 332044 2008-03-29 01:16 ncsvc
-rw-r--r-- 1 aman aman     14 2008-03-29 01:16 version.txt
-rwxr--r-- 1 aman aman   1637 2008-03-29 01:12 xlaunchNC.sh

./tmp:
total 916
-rw-r--r-- 1 aman aman    770 2008-03-29 21:35 getx509certificate.sh
-rw-r--r-- 1 aman aman    716 2008-03-29 21:35 installNC.sh
-rw-r--r-- 1 aman aman 493680 2008-03-29 21:35 libncui.so
drwxr-xr-x 2 aman aman   4096 2008-03-29 21:35 META-INF
-rw-r--r-- 1 aman aman  24888 2008-03-29 21:35 ncdiag
-rw-r--r-- 1 aman aman  45478 2008-03-29 21:35 NC.jar
-rw-r--r-- 1 aman aman 332044 2008-03-29 21:35 ncsvc
-rw-r--r-- 1 aman aman     14 2008-03-29 21:35 version.txt
-rw-r--r-- 1 aman aman   1632 2008-03-29 21:35 xlaunchNC.sh

./tmp/META-INF:
total 12
-rw-r--r-- 1 aman aman 2952 2008-03-29 21:35 IMPORTED.RSA
-rw-r--r-- 1 aman aman  631 2008-03-29 21:35 IMPORTED.SF
-rw-r--r-- 1 aman aman  578 2008-03-29 21:35 MANIFEST.MF

---------------------------------------------
Scripts:
xlaunchNC.sh
#!/bin/sh
# launch to install the service
# 20051220 : Javeed : Added -n to modprobe for dry run. We dont want to insmod, just check if tun
#                                               is available.

if [ "$#" -lt "1" ]
then
        echo "Insufficient number of params"
        echo "$0 <install dir> "
        echo "$*";
        exit
fi

#echo "$*";

#moved code from installNC.sh to here so that we call xterm only if needed.
flag=1

if [ -e "$1/ncsvc" ]
then
        if [ -e "$1/version.txt" ]
        then
                old_version=`grep -i "Version" $1/version.txt | cut -f 2 -d " "`;
                new_version=`grep -i "Version" $1/../tmp/version.txt | cut -f 2 -d " "`;
#               echo "$old_version == $new_version"
                if [  "$old_version" \< "$new_version"  ]
                then
                        echo "Need to install the new service"
                else
                        flag=0
                        echo "No difference found"
                fi
        fi
else
        echo "Service needs to be installed for the first time"
fi
if [ "$flag" -eq "1" ]
then
    echo "calling $1/installNC.sh"
    chmod 744 $1/installNC.sh
    `xterm -e $1/installNC.sh $1`
fi

#export LD_LIBRARY_PATH=/usr/X11R6/lib

# no need to check for ncui. Have to check for openssl package and tun driver.
#ldd $1/ncui | grep "not found" | tr -d "\t" | cut -d " " -f 1 | tee $1/missing_libs
# check if modprobe can locate the tun module.
#Adding dry run option we dont want to insmod, just check if tun is available

rm -rf $1/missing.rpt
/sbin/modprobe -n tun 1> $1/missing.info
if [ "$?" -ne "0" ]
then
    echo "Modprobe for Tun driver failed." > $1/missing.rpt
#    rpm -q tun 1> $1/missing.rpt
fi
#check if openssl is installed
#rpm -q openssl 1>> $1/missing.info
#if [ "$?" -ne "0" ]
#then
#    echo "RPM query for openssl failed." >> $1/missing.rpt
#fi
nstallNC.sh:
#!/bin/sh
# Install the service

if [ "$#" -lt "1" ]
then
        echo "Insufficiant number of parameters"
        echo "$0 <install dir>"
        exit;
fi

if [ -e "$1/ncsvc" ]
then
        echo "Service needs to be reinstalled."
else
        echo "Service needs to be installed for the first time."
fi

ok="try"
until [ "$ok" = "done" ]
do
        echo "Please enter the root/su password"
        su root -c "install -m 6711 -o root $1/../tmp/ncsvc $1/ncsvc"
        if [ "$?" -eq "0" ]
        then
                cp $1/../tmp/version.txt $1/
                ok="done"
                rm -rf $1/../tmp
        else
                echo "Invalid su password and/or Unable to install ncsvc"
                echo -n "Do you want to try again (enter y to try again):";
                read choice;
                if [ "$choice" != "y" ]
                then
                        ok="done"
                fi
        fi
done
chmod 744 $1/ncdiag
------------------------------------

Any help appreciated,

Thanks!
ubunew1124

---

### Post by madscientist on 2008-04-01
I've been using a new script-based method of installing/starting/stopping Network Connect, rather than doing it through the browser.  For me it's a lot simpler and more stable.

Although I have only tried it on Ubuntu, assuming you have zenity installed in your Kubuntu system it should work there as well.  Give it a try and let me know.

[http://mad-scientist.us/juniper.html](http://mad-scientist.us/juniper.html)

---

### Post by senga on 2008-04-28
> **madscientist said:**
> I've been using a new script-based method of installing/starting/stopping Network Connect, rather than doing it through the browser.  For me it's a lot simpler and more stable.

Although I have only tried it on Ubuntu, assuming you have zenity installed in your Kubuntu system it should work there as well.  Give it a try and let me know.

[http://mad-scientist.us/juniper.html](http://mad-scientist.us/juniper.html)

I tried your script on ubuntu 8.04 and see this error
Exception in thread "AWT-EventQueue-0" java.lang.ExceptionInInitializerError
        at NC$3.run(NC.java:1282)
        at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
        at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
Caused by: java.lang.ArrayIndexOutOfBoundsException: 3
        at JavaNC.<clinit>(NC.java:443)
        ... 9 more

This stack trace comes up right after I enter my password. Any suggestions on what could be the problem?

---

### Post by madscientist on 2008-04-28
> **senga said:**
> I tried your script on ubuntu 8.04 and see this error
Exception in thread "AWT-EventQueue-0" java.lang.ExceptionInInitializerError
  ...
        ... 9 more

This stack trace comes up right after I enter my password. Any suggestions on what could be the problem?Hm.  I updated my Ubuntu system to 8.04 last week and I've been using NC just fine with my script.  So, there's something different about our environments.

What version(s) of Java do you have installed on your system?  Run something like "dpkg -l \*java\* | grep ^i" from a terminal window to find out.

Also, what version of ncsvc are you running?  Run "~/.juniper_networks/network_connect/ncsvc --version" and show the output.

---

### Post by senga on 2008-04-28
> **madscientist said:**
> 
What version(s) of Java do you have installed on your system?  Run something like "dpkg -l \*java\* | grep ^i" from a terminal window to find out.

Here is the output from "dpkg -l \*java\* | grep ^i"
ii  java-common                                0.28ubuntu3                                        Base of all Java packages
ii  libhsqldb-java                             1.8.0.9-2                                          Java SQL database engine
ii  libjaxp1.3-java                            1.3.04-2                                           Java XML parser and transformer APIs (DOM, S
ii  libjline-java                              0.9.93-1ubuntu1                                    Java library for handling console input
ii  libservlet2.3-java                         4.0-10                                             Servlet 2.3 and JSP 1.2 Java classes and doc
ii  libservlet2.4-java                         5.0.30-6ubuntu1                                    Servlet 2.4 and JSP 2.0 Java library.
ii  libxalan2-java                             2.7.0-5                                            XSL Transformations (XSLT) processor in Java
ii  libxerces2-java                            2.9.0-1                                            Validating XML parser for Java with DOM leve
ii  openoffice.org-java-common                 1:2.4.0-3ubuntu6                                   OpenOffice.org office suite Java support arc
ii  sun-java5-bin                              1.5.0-15-0ubuntu1                                  Sun Java(TM) Runtime Environment (JRE) 5.0 (
ii  sun-java5-jre                              1.5.0-15-0ubuntu1                                  Sun Java(TM) Runtime Environment (JRE) 5.0 (
ii  sun-java6-bin                              6-06-0ubuntu1                                      Sun Java(TM) Runtime Environment (JRE) 6 (ar
ii  sun-java6-jdk                              6-06-0ubuntu1                                      Sun Java(TM) Development Kit (JDK) 6
ii  sun-java6-jre                              6-06-0ubuntu1                                      Sun Java(TM) Runtime Environment (JRE) 6 (ar
ii  sun-java6-plugin                           6-06-0ubuntu1                                      The Java(TM) Plug-in, Java SE 6

Also, "java -version" shows:
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)

> **madscientist said:**
> 
Also, what version of ncsvc are you running?  Run "~/.juniper_networks/network_connect/ncsvc --version" and show the output.
The command "~/.juniper_networks/network_connect/ncsvc --version" fails with error:
error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

---

### Post by senga on 2008-04-29
> **senga said:**
> 
The command "~/.juniper_networks/network_connect/ncsvc --version" fails with error:
error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

I now downloaded and installed libstdc++2.10-glibc2.2_2.95.4-27_i386.deb and the command "~/.juniper_networks/network_connect/ncsvc --version" shows:
Juniper Network Connect Server for Linux.
Version         : 1.2
Release Version : 5.4-0-Build11359
Build Date/time : Nov 29 2006 22:07:01 

I'll try connecting to the vpn in few hrs and post the results here.

Thanks.

---

### Post by madscientist on 2008-04-29
> **senga said:**
> I now downloaded and installed libstdc++2.10-glibc2.2_2.95.4-27_i386.deb and the command "~/.juniper_networks/network_connect/ncsvc --version" shows:
Juniper Network Connect Server for Linux.
Version         : 1.2
Release Version : 5.4-0-Build11359
Build Date/time : Nov 29 2006 22:07:01 

I'll try connecting to the vpn in few hrs and post the results here.

Thanks.Thanks.  Interesting; where did you find that DEB?  I don't see anything like that in the Ubuntu repositories, but maybe I just don't have the right repos enabled.

---

### Post by senga on 2008-04-30
> **madscientist said:**
> where did you find that DEB?

I got it from debian. [http://http.us.debian.org/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb](http://http.us.debian.org/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb)

I can now connect to the vpn thru firefox. Tried the same with your script.Connection is failing with messages:

---START MESSAGES---
Connecting to server.com port 443
Generating Certificate .... done.
Searching for ncsvc in current working directory
Searching for ncsvc in /home/senga/.juniper_networks/network_connect done.
ncapp> Failed to connect/authenticate with IVE. Error 2
ncapp> Please check the ive hostname/ip and the ive certificate.
---END MESSAGES---

I don't know why it is trying IVE directly. Thru firefox, it would first connect to NCSVC and then IVE. By the way, I don't know what IVE and NCSVC mean. This is just my observation.

Does it look like a generic problem or problem with just my employer's network?

---

### Post by raghaven.kumar on 2008-04-30
Hi,
I m using ubuntu 7.04 to connect to vpn in **amd64** architecture
i recieve the error [COLOR="Red"]**X**[/COLOR] on applet while conecting to juniper vpn
which states
```

load: class SecureNCLauncher.class not found.
java.lang.ClassNotFoundException: SecureNCLauncher.class
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:183)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:127)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:626)
	at sun.applet.AppletPanel.createApplet(AppletPanel.java:778)
	at sun.plugin.AppletViewer.createApplet(AppletViewer.java:2045)
	at sun.applet.AppletPanel.runLoader(AppletPanel.java:707)
	at sun.applet.AppletPanel.run(AppletPanel.java:361)
	at java.lang.Thread.run(Thread.java:619)
Caused by: javax.net.ssl.SSLKeyException: RSA premaster secret error
	at com.sun.net.ssl.internal.ssl.RSAClientKeyExchange.<init>(RSAClientKeyExchange.java:97)
	at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverHelloDone(ClientHandshaker.java:574)
	at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:197)
	at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:511)
	at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:449)
	at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:817)
	at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1029)
	at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1056)
	at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1040)
	at sun.net.www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:405)
	at sun.net.www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:170)
	at sun.net.www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:981)
	at java.net.HttpURLConnection.getResponseCode(HttpURLConnection.java:373)
	at sun.net.www.protocol.https.HttpsURLConnectionImpl.getResponseCode(HttpsURLConnectionImpl.java:318)
	at sun.applet.AppletClassLoader.getBytes(AppletClassLoader.java:284)
	at sun.applet.AppletClassLoader.access$100(AppletClassLoader.java:44)
	at sun.applet.AppletClassLoader$1.run(AppletClassLoader.java:173)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:170)
	... 9 more
Caused by: java.security.NoSuchAlgorithmException: SunTlsRsaPremasterSecret KeyGenerator not available
	at javax.crypto.KeyGenerator.<init>(DashoA13*..)
	at javax.crypto.KeyGenerator.getInstance(DashoA13*..)
	at com.sun.net.ssl.internal.ssl.JsseJce.getKeyGenerator(JsseJce.java:223)
	at com.sun.net.ssl.internal.ssl.RSAClientKeyExchange.<init>(RSAClientKeyExchange.java:89)
	... 27 more
```

i used the [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins") to configure firefox to 32-bit.
i even installed jsse and jce packages for java.

Any suggestions?

---

### Post by elenctic on 2008-05-19
Has anyone gotten Juniper SSL VPN/network connect to work in Ubuntu 8.04?  If so, how?  If not, have you concluded that it is impossible for some reason?

---

### Post by madscientist on 2008-05-19
> **elenctic said:**
> Has anyone gotten Juniper SSL VPN/network connect to work in Ubuntu 8.04?  If so, how?  If not, have you concluded that it is impossible for some reason?It's working fine for me.  I have Ubuntu 8.04 running on a 32bit system.

---

### Post by ruffwuk on 2008-05-30
I am having similar issues with my work Juniper access.  Gutsy works fine.  but now I have Hard, Juniper cannot recognize my java version....

Any help would be greatly appreciated! I went back and installed jre 142 and the plugins to see if maybe I outpaced our Juniper updates, but no luck.

---

### Post by madscientist on 2008-05-30
Looks like you are having a problem with the Firefox/Java plugin integration.  Unfortunately, I can't help much with that but if you go looking for that problem rather than anything to do with Juniper VPN you might have more luck.

To be honest, I never use the "start from the web" method anymore.  I found that annoying and time-consuming so I wrote a script that I can use to kick off the VPN directly.  You can find more info at:

[http://mad-scientist.us/juniper.html](http://mad-scientist.us/juniper.html)

---

### Post by ruffwuk on 2008-05-30
> **madscientist said:**
> Looks like you are having a problem with the Firefox/Java plugin integration.  Unfortunately, I can't help much with that but if you go looking for that problem rather than anything to do with Juniper VPN you might have more luck.

To be honest, I never use the "start from the web" method anymore.  I found that annoying and time-consuming so I wrote a script that I can use to kick off the VPN directly.  You can find more info at:

[http://mad-scientist.us/juniper.html](http://mad-scientist.us/juniper.html)
  Yes i think you are correct.  I can get to some of my published Juniper apps, but i cannot execute apps that need Java scripts.  I will explore the java and firefox 3.05 beta issues.  Thanks for pointing me in  the right direction.
and as always.... heed my advice.  :)

---

