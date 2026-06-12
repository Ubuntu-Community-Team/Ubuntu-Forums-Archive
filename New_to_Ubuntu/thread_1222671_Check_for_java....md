---
title: "Check for java..."
date: 2009-07-25
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-25
how do i check to see if i correctly installed java ???

thanks...

---

### Post by yeats on 2009-07-25
try

```
java -version
```

in the terminal

---

### Post by NOTAGEEK on 2009-07-25
> **chrissharp123 said:**
> try

```
java -version
```in the terminal


java -version
The program 'java' can be found in the following packages:
 * gij-4.3
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.2
 * jamvm
 * kaffe
Try: sudo apt-get install <selected package>
bash: java: command not found

---

### Post by yeats on 2009-07-25
Looks like it didn't get installed at all.  I'm assuming you've seen this(?):

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by SuperSonic4 on 2009-07-25
[http://java.com/en/download/help/testvm.xml](http://java.com/en/download/help/testvm.xml)

---

### Post by NOTAGEEK on 2009-07-25
> **chrissharp123 said:**
> Looks like it didn't get installed at all.  I'm assuming you've seen this(?):

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

i installed last night... it took 10-15 minutes and then re-directed to the java/sun page to accept the terms... i tried to click ok but nothing... it sat on that screen for 30 minutes and did nothing... i then tried to exit the terminal and was told it was still doing something... i just quit thinking it was hung up... now what ???

---

### Post by kpkeerthi on 2009-07-25
If you used apt-get it will not take you to sun's website to accept license. When the license agreement is displayed, scroll to the bottom of the page, press [TAB] key to highlight the OK/Accept button and press [Enter].

Or install the package using synaptic.

---

### Post by NOTAGEEK on 2009-07-25
> **NOTAGEEK said:**
> i installed last night... it took 10-15 minutes and then re-directed to the java/sun page to accept the terms... i tried to click ok but nothing... it sat on that screen for 30 minutes and did nothing... i then tried to exit the terminal and was told it was still doing something... i just quit thinking it was hung up... now what ???

sudo update-java-alternatives -l
[sudo] password for wxyz: 
awk: cannot open /usr/lib/jvm/*.jinfo (No such file or directory)
100_1576.jpg 100_1577.jpg 100_1578.jpg 100_1579.jpg 100_1580.jpg .adobe .bash_history .bash_logout .bashrc .cache .config .cups .dbus dcemail.abk ddiscvry.dps desktop Desktop .dmrc Documents .esd_auth .evolution examples.desktop .fontconfig .gconf .gconfd .gksu.lock .gnome2 .gnome2_private .gnupg .gstreamer-0.10 .gtk-bookmarks .gvfs .hplip .ICEauthority .icons .kde .local .macromedia .mozilla Music .nautilus nautilus- oundcore Photos Pictures player.swf prefguid.txt .printer-groups.xml .profile Public .pulse .pulse-cookie .recently-used.xbel .sane .sudo_as_admin_successful Templates .themes .thumbnails .tomboy .tomboy.log troubleshoot.txt Untitled-3.ogg .update-manager-core .update-notifier .usb-creator.log Videos .wapi .Xauthority .xchat2 .xine .xscreensaver-getimage.cache .xsession-errors /usr/lib/jvm/*

---

### Post by NOTAGEEK on 2009-07-25
> **kpkeerthi said:**
> If you used apt-get it will not take you to sun's website to accept license. When the license agreement is displayed, scroll to the bottom of the page, press [TAB] key to highlight the OK/Accept button and press [Enter].

Or install the package using synaptic.

perhaps i should start over and try again... i think i did use apt get... is it best to try through synaptics ???

thanks...

---

### Post by kpkeerthi on 2009-07-25
> **NOTAGEEK said:**
> sudo update-java-alternatives -l
[sudo] password for buzz: 
awk: cannot open /usr/lib/jvm/*.jinfo (No such file or directory)
100_1576.jpg 100_1577.jpg 100_1578.jpg 100_1579.jpg 100_1580.jpg .adobe .bash_history .bash_logout .bashrc .cache .config .cups .dbus dcemail.abk ddiscvry.dps desktop Desktop .dmrc Documents .esd_auth .evolution examples.desktop .fontconfig .gconf .gconfd .gksu.lock .gnome2 .gnome2_private .gnupg .gstreamer-0.10 .gtk-bookmarks .gvfs .hplip .ICEauthority .icons .kde .local .macromedia .mozilla Music .nautilus nautilus- oundcore Photos Pictures player.swf prefguid.txt .printer-groups.xml .profile Public .pulse .pulse-cookie .recently-used.xbel .sane .sudo_as_admin_successful Templates .themes .thumbnails .tomboy .tomboy.log troubleshoot.txt Untitled-3.ogg .update-manager-core .update-notifier .usb-creator.log Videos .wapi .Xauthority .xchat2 .xine .xscreensaver-getimage.cache .xsession-errors /usr/lib/jvm/*

You need to install Java before you do that. Have you installed it?

---

### Post by NOTAGEEK on 2009-07-25
> **kpkeerthi said:**
> You need to install Java before you do that. Have you installed it?
please see 2 posts up...

---

### Post by kpkeerthi on 2009-07-25
> **NOTAGEEK said:**
> please see 2 posts up...

Can't make anything out of it.If the below command works and prints Sun Java, you have Java installed and working

```
java -version
```

---

### Post by philinux on 2009-07-25
Synaptic is always the best way.

sudo apt-get install sun-java6-jre

---

### Post by NOTAGEEK on 2009-07-25
> **kpkeerthi said:**
> Can't make anything out of it.If the below command works and prints Sun Java, you have Java installed and working

```
java -version
```

> **philinux said:**
> Synaptic is always the best way.

sudo apt-get install sun-java6-jre


i think im good to go now---had a broken pkg that had to be fixed...

 java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Server VM (build 14.0-b16, mixed mode)

---

### Post by philinux on 2009-07-25
Good one.

You can test it at java.com

---

### Post by NOTAGEEK on 2009-07-25
> **philinux said:**
> Good one.

You can test it at java.com

excellent !!! ill test it...

thread closed...

thanks to all...

---

