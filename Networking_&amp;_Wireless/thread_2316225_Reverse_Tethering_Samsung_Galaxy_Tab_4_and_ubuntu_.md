---
title: "Reverse Tethering Samsung Galaxy Tab 4 and ubuntu 14.04"
date: 2016-03-06
forum: Networking &amp; Wireless
---

### Post by gam01hr on 2016-03-06
I'm trying to use internet on my tablet by wired USB connection (without tablet rooting). I followed instruction of "Reverse Tethering" android app. There is a problem on PC server side. The Java server refuses to run.
> 
PC side: [http://fdmobileinventions.blogspot.cz/p/reversetethering-server.html](http://fdmobileinventions.blogspot.cz/p/reversetethering-server.html)
Android 4.4.2 side: [https://play.google.com/store/apps/details?id=com.floriandraschbacher.reversetethering.free](https://play.google.com/store/apps/details?id=com.floriandraschbacher.reversetethering.free)
pictures: [https://drive.google.com/folderview?id=0B_Hh2KkkSOTsV2dKSG5WT0gtMEk](https://drive.google.com/folderview?id=0B_Hh2KkkSOTsV2dKSG5WT0gtMEk)

```

ubuntu@ubuntu:~/ReverseTetheringServer_1.0.1$ lsb_release -r
Release:    14.04

ubuntu@ubuntu:~/ReverseTetheringServer_1.0.1$ java -versionjava version "1.7.0_80"
Java(TM) SE Runtime Environment (build 1.7.0_80-b15)
Java HotSpot(TM) 64-Bit Server VM (build 24.80-b11, mixed mode)

ubuntu@ubuntu:~/ReverseTetheringServer_1.0.1$ java -jar ReverseTetheringServer_1.0.1.jar 
Exception in thread "main" java.lang.UnsupportedOperationException
    at java.awt.TrayIcon.<init>(TrayIcon.java:144)
    at java.awt.TrayIcon.<init>(TrayIcon.java:168)
    at java.awt.TrayIcon.<init>(TrayIcon.java:197)
    at java.awt.TrayIcon.<init>(TrayIcon.java:227)
    at p.<init>(Unknown Source)
    at com.floriandraschbacher.reversetetheringserver.Main.main(Unknown Source)

```
Please would you advice me fix or other way how to do this? I understand I can buy additional wireless usb adapter on PC side but I would like try the USB connection first. Thx.

---

