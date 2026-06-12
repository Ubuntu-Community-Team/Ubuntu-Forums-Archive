---
title: "How Can I install the latest version Java (6.11)?"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Martinex on 2009-01-04
How Can I install the latest version java from offcial site java.com?
[http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80)

I have no idea How Can I do it.

I have Linux Ubuntu 8.04 LTS and Web Browser Firefox 3.0.5.

---

### Post by Nepherte on 2009-01-04
You can find instructions on the sun java website: [http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting) There's only one difference. Every time they speak of logging in as root, ignore that directive (login as your user) and every time a command complains about not having rights, place sudo in front of the command. You should use the self extracting file by the way or the 64bit version if you use 64 bit (both are .bin files, do not take the .rpm).

---

### Post by Martinex on 2009-01-04
That is no helpful for me.
Working with Opera (path:/usr/lib/java), not working with Firefox.

---

### Post by Nepherte on 2009-01-04
I have no idea how to enable the java plugin in opera, but I *can* tell you that it doesn't rely on the install location of the java runtime environment. It's a matter of linking to the location of the plugin.

In the example, they use /usr/java as the install location. But as I told before, it doesn't matter where you put it. If you want to put it in /usr/lib/java, that's fine too.

---

### Post by Martinex on 2009-01-04
I set manually in settings (opera).
So How Can I Do on the firefox 3.0.5?

---

### Post by igknighted on 2009-01-04
> **Martinex said:**
> I set manually in settings (opera).
So How Can I Do on the firefox 3.0.5?

Opera links directly to your java install, firefox needs a plugin.  You need to link the plugin in the java directory (depends on where you installed it) to your mozilla folder (/usr/lib/mozilla/plugins).   You also need to remove any other plugins related to java that might confuse firefox (or manually set the java directories in about:config in firefox)

---

### Post by Martinex on 2009-01-04
How Can I do it?

[[IMG]http://img166.imageshack.us/img166/5572/screenshot1lo6.th.jpg[/IMG]](http://img166.imageshack.us/my.php?image=screenshot1lo6.jpg)

---

### Post by igknighted on 2009-01-04
What does about:plugins say?  Does it list that java plugin?  Also, what does about:config say about the location of java, and the name of the java plugin (search java in about:config)?

---

### Post by Martinex on 2009-01-04
There's no java in about:about
Screen from about:config under:

[[IMG]http://img167.imageshack.us/img167/3928/screenshot1hl9.th.jpg[/IMG]](http://img167.imageshack.us/my.php?image=screenshot1hl9.jpg)

---

### Post by igknighted on 2009-01-04
Try removing the default java plugin (icedtea6-plugin).

Also, if you want to post an image, just attach it using the Additional Options below.  Makes life much easier.

---

### Post by Martinex on 2009-01-04
That's my folder /usr/lib/mozilla/plugins

---

### Post by igknighted on 2009-01-04
Can you run the command 'ls -al /usr/lib/mozilla/plugins' instead?

Also, anything in about:plugins in firefox?

Finally, as you posted above, there is a symlink to your java plugin in /usr/lib/mozilla/plugins, the question is more how to make firefox see it.

How did you install this version of java?  Can you post the commands you used?  Finally, is there any reason you needed java version 1.6.11, instead of the simple to use and install 1.6.10 which is in the repo's?

EDIT: One last thing, what does the command 'java -version' say?

---

### Post by Martinex on 2009-01-04
martinex@martinex-desktop:~$ java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)
martinex@martinex-desktop:~$ 

I based on this tutorial: [http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting) , version 32bit in .bin


Reason? I'd like to have the latest version of java, maybe it faster than current version :P.


martinex@martinex-desktop:~$ ls -al /usr/lib/mozilla/plugins
total 1472
drwxr-xr-x 2 root root   4096 2009-01-04 21:54 .
drwxr-xr-x 4 root root   4096 2008-07-02 12:21 ..
lrwxrwxrwx 1 root root     39 2009-01-03 10:11 .backa.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root root     37 2009-01-03 10:51 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root     64 2009-01-04 21:54 libjavaplugin_oji.so -> /usr/java/jre1.6.0_11/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
-rw-r--r-- 1 root root 287328 2008-07-25 10:57 mplayerplug-in-dvx.so
-rw-r--r-- 1 root root   1067 2008-07-25 10:57 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 root root 287552 2008-07-25 10:57 mplayerplug-in-qt.so
-rw-r--r-- 1 root root   1067 2008-07-25 10:57 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root root 287616 2008-07-25 10:57 mplayerplug-in-rm.so
-rw-r--r-- 1 root root   1067 2008-07-25 10:57 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root root 289244 2008-07-25 10:57 mplayerplug-in.so
-rw-r--r-- 1 root root 289248 2008-07-25 10:57 mplayerplug-in-wmp.so
-rw-r--r-- 1 root root   1067 2008-07-25 10:57 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root root   1067 2008-07-25 10:57 mplayerplug-in.xpt
martinex@martinex-desktop:~$

---

### Post by igknighted on 2009-01-04
What folder did you install to?  Did you use /usr/java, or did you pick a different folder?

---

### Post by igknighted on 2009-01-04
Sorry to DP

You need to switch your system-wide link to java to point toward your new install.  Run the command 'sudo update-alternatives --display java'

---

### Post by jamesstansell on 2009-01-04
> **Martinex said:**
> 
Reason? I'd like to have the latest version of java, maybe it faster than current version :P.


Java 6 update 11 was a security release to fix problems in u10 and earlier.  If anyway finds that it's faster then I'd like to know about it!

The way I installed it was to grab the packages I wanted from the jaunty (ubuntu 9,04) repository.  You can use a browser or a tool like wget or curl.  You can go to a mirror of the repository or download from packages.ubuntu.com or [https://launchpad.net/ubuntu/+source/sun-java6](https://launchpad.net/ubuntu/+source/sun-java6)

Because they are based on sun's binaries they are compiled in a way that will work for most ubuntu versions.  I used "sudo dpkg -i" to install the packages.

Because this was a security update it would be good for it to be added to the hardy-updates and intrepid-updates repositories.  I'm not sure why it hasn't been already. (I don't think it would go in the -security archives because these are multiverse packages.)

Note: there are other ways to get java6u11 installed from the jaunty repository.  In particular a technique called "apt pinning" could probably be used to add it to synaptic and the other package managers.  I just haven't trod that route.

---

### Post by baracuda68 on 2009-02-01
> **igknighted said:**
> Sorry to DP

You need to switch your system-wide link to java to point toward your new install.  Run the command 'sudo update-alternatives --display java'


So, what IS the default " system-wide" java link directory?;)

---

### Post by igknighted on 2009-02-02
> **baracuda68 said:**
> So, what IS the default " system-wide" java link directory?;)

Depends what version of java you have installed.  I don't believe it is set to anything, as I don't think that icedtea java is in the default install.  But if you have 3 or 4 java installs (open source, repo's, maybe an update, and the latest from the sun site), you can easily switch back and forth.

---

