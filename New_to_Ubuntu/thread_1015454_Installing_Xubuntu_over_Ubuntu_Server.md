---
title: "Installing Xubuntu over Ubuntu Server"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by amenotatsujin on 2008-12-18
I have a computer with no internet access that has Ubuntu Server 8.10 installed. I have the live cd for Xubuntu, and I want to install it over Ubuntu Server. I cannot get the CD to start using BIOS. How would I go about doing this?

---

### Post by dwasifar on 2008-12-18
You'd add the CD to /etc/apt/sources.list, then:

```
sudo apt-get update 
sudo apt-get install xubuntu-desktop
```

The format for putting the CD in the list is like this:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

Obviously you would want to modify that for your particular CD and release names.

---

### Post by amenotatsujin on 2008-12-19
I do not know what the name of the CD would be for that entry. The CD has Xubuntu 8.10, but I don't know what to type for that. My main issue is that it will not access the internet. I cannot update anything. Would you know a way to resolve that?

---

### Post by taurus on 2008-12-19
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

---

### Post by amenotatsujin on 2008-12-19
```

end_request: I/O, dev sr1, sector 1207264
Buffer I/O error on device sr1, logical block 150908

```
I keep getting these messages when I try to mount the drive.

If it helps any, this is a list of details about this computer:
-The computer is running Ubuntu Server 8.10
-The computer has two CD-ROM drives, and doesn't recognise either of them.
-The computer is plugged into the internet through a wired connection, but cannot access the internet

I have two goals:
-To get the internet working
OR
-To get Xubuntu Desktop installed from the live cd

---

### Post by amenotatsujin on 2009-02-14
Still doesn't work.

---

### Post by hyper_ch on 2009-02-14
this above works only with the alternate cd not with the desktop one.

---

### Post by amenotatsujin on 2009-03-14
This is not working with the alternate CD either.

---

### Post by SuperSonic4 on 2009-03-14
Does ```
sudo dhcpcd eth0
``` work for the internet?

---

### Post by amenotatsujin on 2009-03-14
This is what it returned. 
```
sudo: dhcpcd: command not found
```

---

### Post by hyper_ch on 2009-03-15
> **amenotatsujin said:**
> This is not working with the alternate CD either.

it does :) what did you do to try to make it work?

---

### Post by kansasnoob on 2009-03-15
Well for a minute forget any CD. It sounds like you can get to Terminal from your server install so simply run:

```
sudo apt-get install xubuntu-desktop && sudo apt-get -f install
```

Totally ignorant post! Sorry!

Looking back I see you have no internet!

---

