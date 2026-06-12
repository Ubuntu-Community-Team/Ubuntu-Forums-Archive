---
title: "I don't know how to install GUI to ubuntu server"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by Fibernet on 2010-02-04
Im using Ubuntu Server and I have cd which contain ubuntu-desktop but idont know how to install, I already try apt-cdrom and apt-get upgrade

---

### Post by overdrank on 2010-02-04
Hi and have you tried the suggestions in your other [thread]("http://ubuntuforums.org/showthread.php?t=1396730")?
If you are trying to use the cd I believe you will need the alternate cd.

---

### Post by Fibernet on 2010-02-04
yes I have already aternate cd the only problem i don't know how to install the ubuntu-desktop

---

### Post by tikal808 on 2010-02-05
If the server you want to install ubuntu-desktop is connected to the Internet you should be able to do it this way:

```
sudo apt-get install ubuntu-desktop

```
If it's not connected to the Internet or has a very slow connection, etc. It might be harder to do. You can try the steps I've put below.

I'm not sure if these steps will work or not, but you can try. I had to do something similar to what you are trying to do recently and I think this is what did the trick for me.

Use this method if the system being upgraded is not connected to the Internet.
or 
If you want to skip downloading the packages from the Internet because you already have downloaded an ISO file with the packages you need.

(In this case the package is ubuntu-desktop)

1.Download the alternate installation CD

2.Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded.

***If the ISO file is already on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO file as a drive with a command like:

```
sudo mount -o loop ~/Downloads/ubuntu-9.10-alternate-i386.iso /media/cdrom
```

3. ```
gksu "sh /cdrom/cdromupgrade"
```

Reference: [http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD]("http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD")

---

### Post by Iowan on 2010-02-05
Dunno if [this]("https://help.ubuntu.com/community/ServerGUI") one might help...

---

