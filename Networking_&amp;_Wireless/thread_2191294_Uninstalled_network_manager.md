---
title: "Uninstalled network manager"
date: 2013-12-01
forum: Networking &amp; Wireless
---

### Post by robbie9513 on 2013-12-01
I accidentally uninstalled my network manager, and now I can't reinstall it. How can I connect to wifi through command line, or install network manager another way?

---

### Post by varunendra on 2013-12-03
Welcome to the forums robbie9513 !

Please try this -

[indent]**1)** Open a terminal (Ctrl-Alt-T) and run the following command in it -
```
apt-get install --reinstall --print-uris network-manager-gnome
```
It should return some output, at the bottom of which it should give you one or more download URIs of the required packages.

**2)** Copy these URIs and use them to download the packages on another computer where internet is working.

**3)** Copy the downloaded package(s) back to your Ubuntu desktop in a new, empty folder. For sake of clarity, let's name this folder "netman"

**4)** Open a terminal, change to this directory and install the package(s) as follows -
```
cd Desktop/netman
sudo dpkg -i *
```[/indent]

This method assumes your package manager database has the information about default packages and their package URIs, which sometimes requires that the database has been updated at least once. If the apt-get command suggested above doesn't return any URIs, it means the database does not have this information. In that case, you can do the same from the live cd/usb from which you installed the OS. Make sure it is exactly same one from which you installed Ubuntu. NM and a working wireless should be available on the live session to make things easy.

---

### Post by robbie9513 on 2013-12-06
This worked so well. Thank you!!!

---

### Post by varunendra on 2013-12-06
You're welcome ! :)

---

