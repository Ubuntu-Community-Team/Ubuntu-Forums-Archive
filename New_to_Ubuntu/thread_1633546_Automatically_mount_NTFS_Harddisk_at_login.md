---
title: "Automatically mount NTFS Harddisk at login"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by bokgeneraal on 2010-11-29
[SIZE=3]**RE: Automatically mount secondary NTFS harddisk**[/SIZE]
I have two seperate harddisks. One EXT4 and the other NTFS. How do get the NTFS drive to automount at login?:p

---

### Post by janpol on 2010-11-29
[http://ubuntuforums.org/showthread.php?t=785263]("http://ubuntuforums.org/showthread.php?t=785263")

---

### Post by karthick87 on 2010-11-29
**Install PYSDM**

```
sudo apt-get install pysdm
```After installing,it will be found under **System>>Administration>>Storage Device Manager**
Open it,
_[[IMG]http://hosting11.imagecross.com/image-hosting-56/7894Screenshot-Storage-Device-Manager.png[/IMG]]("http://www.imagecross.com/")_

Select your NTFS drive and click mount and Apply..

[B]Alternate way:
[/B]
**Install NTFS-CONFIG**

```
sudo apt-get install ntfs-config
```It will be found under **System>>Administration>>NTFS Configuration Tool**
Open it, Check **Write support for internal Device** and choose the drives you want to get auto-mounted during startup. Click on close and you are done.Now every time when you boot into you Ubuntu, you will have  your NTFS drives auto-mounted during the startup.

[**Also see this documentation**]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

### Post by bokgeneraal on 2010-11-30
Thanks for the help;)

---

### Post by karthick87 on 2010-11-30
You are welcome :)

---

