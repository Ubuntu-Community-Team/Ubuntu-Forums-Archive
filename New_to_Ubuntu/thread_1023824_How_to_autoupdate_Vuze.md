---
title: "How to autoupdate Vuze"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by peakshysteria on 2008-12-28
I can't seem to be able to set read/write permissions to Vuze. As long as I can't do this Vuze wont update. Now running version: 4.0.0.0. How can I make Azureus update. How can I set read/write permissions?

I've tried to follow [Forlong's blog]("http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu") without luck. I can't find any threads on the Vuze forums or the Ubuntu forums either.

---

### Post by nhasian on 2008-12-28
i just installed vuze yesterday.  its pretty cool!  it also updated itself from 4.0.0.2 to 4.0.0.4.  I extracted the Vuze folder inside my home folder.  the only special thing i had to do for vuze (azureus) was change the java i was using from opensource version to sun-java with the command:

```
 sudo update-alternatives --config java
```

as for permissions, the azureus script is owned by me with Read&Write access, the group is also set to me with read-only and others is also read-only

ls -l shows me:

```
-rwxr-xr-x 1 nhasian nhasian     5497 2007-09-20 16:54 azureus
-rw-r--r-- 1 nhasian nhasian 12315404 2008-12-26 18:59 Azureus2.jar
-rw-r--r-- 1 nhasian nhasian    33261 2008-10-24 22:38 ChangeLog.txt
-rw-r--r-- 1 nhasian nhasian    17594 2006-08-13 19:27 GPL.txt
-rw-r--r-- 1 nhasian nhasian        0 2007-12-07 00:25 installer.log
drwxr-xr-x 6 nhasian nhasian     4096 2007-09-20 00:19 plugins
-rw-r--r-- 1 nhasian nhasian      456 2007-08-16 19:26 README.txt
-rw-r--r-- 1 nhasian nhasian  1830860 2008-12-26 18:58 swt.jar
-rw-r--r-- 1 nhasian nhasian    73723 2008-06-16 15:39 TOS.txt
-rwxr-xr-x 1 nhasian nhasian      106 2007-08-16 11:42 updateAzureus
lrwxrwxrwx 1 nhasian nhasian        7 2008-12-26 18:17 vuze -> azureus
-rw-r--r-- 1 nhasian nhasian     5150 2008-10-15 01:41 vuze.png
```

---

### Post by peakshysteria on 2008-12-28
Everything is working pretty nice except for auto update which fails because of the wrong read/write permissions to /usr/share/vuze. How can I change this for an existing Vuze installation?

---

### Post by ovisan on 2009-05-23
Sorry for bumping an old thread but I got the same problem as peakshysteria. Can anyone help please?

---

### Post by nhasian on 2009-05-24
try starting it from a terminal with:

```
sudo vuze
```

then it should update normally.

---

### Post by jjosotoro on 2009-06-02
ok your problem is something a lot of people is passing trougth whit ubuntu jaunty, the way i solved it was very simple and actually gave me acces to other aplications i use a lot; what i did was adding the getdeb repository to mi source list

echo "deb [http://getdeb.masio.com.mx/](http://getdeb.masio.com.mx/) jaunty/" | sudo tee -a /etc/apt/sources.list.d/getdeb.list && sudo apt-get update

now if that gives an gpg error like this:

W: GPG error: [http://getdeb.masio.com.mx/](http://getdeb.masio.com.mx/) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D

you must use the following command in the terminal:

gpg --keyserver hkp://subkeys.pgp.net --recv-keys "XXXXXXXXXX"
sudo gpg --export --armor "XXXXXXXXXX" | sudo apt-key add -
sudo apt-get update

replacing the "XXXXXXXXXX" whit the number that appears in the message ex: B152F042D246C25D

$sudo apt-get update

just to check about the gpg error (it shouldnt appear anymore)

$sudo apt-get install vuze

this will install the version of vuze that is on getdeb (4.2.0.2) whit all dependencies, or you can install it using synaptics.

$sudo chmod -R 777 /usr/share/vuze

this will let vuze to do any upgrade

---

