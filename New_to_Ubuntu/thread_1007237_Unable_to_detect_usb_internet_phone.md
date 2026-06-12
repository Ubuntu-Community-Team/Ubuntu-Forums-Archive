---
title: "Unable to detect usb internet phone"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by unknown user on 2008-12-10
[FONT="Tahoma"]I have a usb handset that I got with a Tesco internet phone package. It works tine in windows and I thought that I would try and set it up on my Ubuntu, but when I plug it is, nothing happens. The  system does not detect that the handset has been plugged in or anything like that.

Has anyone had this thing happen or know how I can get the system to detect that it is plugged in?

Cheers,[/FONT]

---

### Post by jman6495 on 2008-12-10
You Realy Need To Ask Tesco If They Have Drivers For Linux,
The Only Small Problem Is The Guy Behind The Desk Might Blankly Look At You And Ask "Whats Linux?".
Or If You USe WINE You Could Mabi INstall It Like That
Hope This Helps
   Jman6495

---

### Post by unknown user on 2008-12-10
Cheers for that Jman6495 I will email Tesco and check.

---

### Post by unknown user on 2008-12-14
[FONT="Tahoma"]Hiya, I got an email back from Tesco and they said that they do not deal with any other OS apart from windown. Lol the funny thing was that on the end the guy had signed it with his name and the saying for Tesco "Every little helps", not help me though.[/FONT]

---

### Post by unknown user on 2008-12-15
The unit is  e337 and I have read that the skypemate is needed to get it working. Does anyone know if this is right?

---

### Post by unknown user on 2008-12-16
[FONT="Tahoma"]I was looking on the PC Pitstop forum and there was something around this area and users not being able to see their usb devises in ubuntu and their comment was "you should be able to just go System>Administration>Restricted drivers manager. enable it. "

I must admit that I have not looked at this and wonder if anyone else has?[/FONT]

---

### Post by unknown user on 2008-12-17
I have been able to determine that my system has detected my phone by the following. Now I need to try and get the phone (Yealink Network Technology Ltd. VOIP USB Phone at usb-0000:00:1d.1-1) working on Ubuntu, any ideas?

unknown@unknown-laptop:~$ lsusb

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 007: ID 6993:b001 Freshtel FT-102 VoIP USB Phone

Bus 003 Device 002: ID 03f0:011d Hewlett-Packard Integrated Bluetooth Module

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 002: ID 413c:3016 Dell Computer Corp.

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

unknown@unknown-laptop:~$ sudo install Freshtel FT-102 VoIP USB Phone



unknown@unknown-laptop:~$ cat /proc/asound/cards

0 [ICH6 ]: ICH4 - Intel ICH6

Intel ICH6 with AD1981B at irq 21

1 [default ]: USB-Audio - VOIP USB Phone

Yealink Network Technology Ltd. VOIP USB Phone at usb-0000:00:1d.1-1

---

### Post by unknown user on 2008-12-17
[FONT="Tahoma"]I have read that I need to install skypemate to make the phone work by running the command line (./install-SkypeMate) so I will try this tonight and will post the results.[/FONT]

---

### Post by GrahamM on 2008-12-31
> **unknown user said:**
> [FONT="Tahoma"]I have read that I need to install skypemate to make the phone work by running the command line (./install-SkypeMate) so I will try this tonight and will post the results.[/FONT]

I am attempting to install my Power Voice Mate (Skypemate). I downloaded a linux driver from [www.voicegear.ca/downloads](www.voicegear.ca/downloads), unpacked it and placed the files in /home/graham/Skypemate . I then attempted to run the install-Skypemate file, but I guess I don't know how to!

Also not sure that file is suitable for Ubuntu - name is SkypeMate_linux_fedora_core3_1.1.0.01.zip and it is dated 2005.

---

### Post by unknown user on 2009-01-26
I found this link not sure if it is any good:

[http://forums.broadbandbuyer.co.uk/forum_posts.asp?TID=7924](http://forums.broadbandbuyer.co.uk/forum_posts.asp?TID=7924)

---

### Post by unknown user on 2009-02-04
Lol still had no luck with this one, think it might be a dead horse.
I am going to give virtual box a go before I say enough is enough though.

---

### Post by nmyrick on 2010-10-21
There have been many issues with Ubuntu not detecting USB devices.  Maybe, if we all complain enough, the Ubuntu developers will put something in the next rev that at least shows that the device is there, even if it has no driver.

Windows can do this, so I don't understand why this is an issue with Ubuntu.  With Windows, even if it doesn't have the driver, it still shows you that there is a device there without having to go to the command prompt.

---

