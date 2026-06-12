---
title: "Greenfoot install"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by MelDJ on 2009-08-24
can anyone help me install sun's greenfoot?

---

### Post by MelDJ on 2009-08-24
its a .jar file. could any1 pls help me install it?? any help will be appreciated :(

---

### Post by MelDJ on 2009-08-24
er...bump:confused:

---

### Post by ainsworth_t on 2009-08-25
First, you must verify that you have Java installed by running the following command in a Terminal:
```
java -version
```

If you have Java installed, you will get a similar output:
> ####@hostname:~$ java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu10)
OpenJDK Client VM (build 14.0-b08, mixed mode, sharing)


If you do not have Java installed, you must install it by running the following command in a Terminal:
```
sudo apt-get install sun-java6-jdk
```

After you have installed or verified the Java installation, according to the Greenfoot installation instructions ([http://www.greenfoot.org/download/install.html](http://www.greenfoot.org/download/install.html)), Greenfoot will install to whatever directory the installer is launched from, so it's probably a good idea to copy the installation file from wherever you downloaded it to /opt/greenfoot or /usr/local/greenfoot (either directory will need to be created).

Once you have the file copied, move to the directory you copied the installation file to and run the following command:
```
sudo java -jar Greenfoot-generic-154.jar
```

This will launch the Greenfoot installer. From this installer you can select the Directory installation path (leave at default) and the JDK directory (typically located at /usr/lib/jvm/java-6-sun-1.6.0.14). Once both of these fields are populated, click the "Install" button. When the installation is finished, click "Done".

To start Greenfoot, in a Terminal window, navigate to the directory that it was installed to and run the following command:
```
sudo ./greenfoot
```

If you don't want to have to run it as SUDO, you will have to change the ownership/group to your username or you can just change the permissions to Read+Write+Execute for everyone.

Hope this helps.

---

### Post by MelDJ on 2009-08-25
works..thanks:)

---

### Post by whistlerspa on 2009-11-23
worked for me too  - many thanks

---

### Post by zengrz on 2010-06-29
Thanks so much!

---

