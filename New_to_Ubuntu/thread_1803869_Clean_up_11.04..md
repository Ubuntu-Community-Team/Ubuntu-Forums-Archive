---
title: "Clean up 11.04."
date: 2011-07-14
forum: New to Ubuntu
---

### Post by xXNI4NI on 2011-07-14
I have been upgrading my distros since 8.04 and I would really like to work from a blank slate. Is there a way to start with a clean 11.04 instead of doing a complete re-install? Or if I have to re-install is there a way to do so without a disk/usb?

---

### Post by Sonicrulz12 on 2011-07-14
to reinstall you have to download the 11.04 iso and put it on a usb or cd or dvd and just pop it in and install

---

### Post by Sonicrulz12 on 2011-07-14
i dont think you can re install with out a usb or disk

---

### Post by linuxman94 on 2011-07-14
If you've really been upgrading since 8.04, you are due for a complete re-install.  You'll need a usb drive or cd to do it.  Just back up your important documents before you install.

---

### Post by nomko on 2011-07-14
> **xXNI4NI said:**
> I have been upgrading my distros since 8.04 and I would really like to work from a blank slate. Is there a way to start with a clean 11.04 instead of doing a complete re-install? Or if I have to re-install is there a way to do so without a disk/usb?
 
In a terminal type the following commands:
```
 
sudo apt-get install autoremove

```
```
 
sudo apt-get install autoclean

```
Go to synaptic and search for deborphan and deborphangtk. This program will remove any unnecessary (orphaned) deb packages.
 
There are also some terminal commands for deborphan which can be handy to clean your system:
In a terminal type the following commands:
(To delete unnecessary data packages)
```
 
sudo deborphan --guess-data | xargs sudo apt-get -y remove --purge

```
(To delete unnecessary libraries)
```
sudo deborphan | xargs sudo apt-get -y remove --purge
```

---

### Post by 3rdalbum on 2011-07-14
> **linuxman94 said:**
> If you've really been upgrading since 8.04, you are due for a complete re-install.

Not necessarily. If everything's still working as it should, then be thankful that you don't have to do a fresh reinstall each time.

---

