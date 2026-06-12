---
title: "Is there a default Ubuntu username and password"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by C.S.Cameron on 2010-01-13
Is there a default Ubuntu user name and password?
I think ubuntu is the default user name is there a password to suit?
I installed to USB flash drive using usb-creator, I made casper-rw and home-rw partitions inside an extended partition.
Everything starts to boot up ok but now a screen comes up asking for a username and password, but I have not yet defined a new user in users and groups?
This has not happened to me before.

---

### Post by x33a on 2010-01-13
A lot of people seem to have similar issues.

one solution is to boot into recovery mode and then create a new user.

---

### Post by C.S.Cameron on 2010-01-13
Thanks but how do I boot into recovery mode on a non persistent pendrive?

---

### Post by x33a on 2010-01-13
Hmm.. sorry i overlooked that fact :)

Maybe this could help:

[http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html)
or
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

you might want to use the livecd.

---

### Post by C.S.Cameron on 2010-01-14
Thanks again, but neither seemed to work with a Live USB.
What finally seemed to get rid of the password request was to install using usb-creator then manually delete the casper-rw file.
Not sure why.

---

### Post by Iowan on 2010-01-14
[Another]("http://www.psychocats.net/ubuntu/resetpassword") option - if you haven't got it fixed yet.

---

### Post by sturg_nz on 2010-01-14
Hi,
This sounds like what I had this morning
I was able to get past it on the live CD for 9.10 mobile linux by using the username ubuntu and no password... 

thanks

---

### Post by tom.swartz07 on 2010-01-14
> **sturg_nz said:**
> Hi,
This sounds like what I had this morning
I was able to get past it on the live CD for 9.10 mobile linux by using the username ubuntu and no password... 

thanks

+1

Thats what I use.

---

### Post by C.S.Cameron on 2010-01-15
User name ubuntu with no password is the first thing I tried then every combination of ubuntu, root and blank in upper and lower case I could think of.
I think this is just a bug in the 9.10 version of Ubuntu, I even tried installing 9.10 with the 9.04 version of usb-creator and the same thing happened.
The install has worked ok a couple times but I can't figure out why.
It may just be my 4GB Kingston Traveler. These sticks have caused me problems before with usb-creator.
Unetbootin installs seem to work fine.

---

### Post by farsight on 2010-01-15
does username "root" password "root" not work in this instance? I guess if it does then you have a means by which to create a personal username and passoword :)

---

### Post by sgosnell on 2010-01-15
If you want to actually use the drive for work, not just for installations, you need to install Ubuntu to it, not just make a LiveCD version.  Use the liveCD to install to the USB drive, and you have the full Ubuntu, with your own username and password.

---

### Post by C.S.Cameron on 2010-01-16
Thanks but this is just an academic issue to do with usb-creator installs.
A properly setup Live USB image install had few disadvantages over a Full install except when it comes to updating. However now with 9.10 they seem to have hidden the security tab that used to be located in system/Preferences/Log in Window so I can't boot into my username and password.

---

### Post by sgosnell on 2010-01-16
I had lots of issues with 9.10, so I'm still on 9.04, but running 10.04 on an SDHC card.  I've never seen a LiveUSB ask for a login of any kind, it just boots.  That's one of the things I don't like about using them for anything but installing the OS onto another drive.  Maybe I'm missing something somewhere, though.

---

### Post by C.S.Cameron on 2010-01-17
With 9.04 and previous you can add a user name and password to users and groups then select that user under System/Administration/Login Window/Security, and un-check Automatic and Timed Login options.
The persistent thumbdrive will then ask for a username and password at login.

---

### Post by sgosnell on 2010-01-17
OK, I've never done it that way.  I just use a 1GB drive to hold the LiveUSB, and do a full install to a larger drive for actual use.  The 'persistent' feature on the LiveUSB doesn't seem to work all that well for me, and I prefer the full install, which also has the install program, but it's a complete OS.

---

### Post by C.S.Cameron on 2010-01-17
I normally prefer a full install myself, however pre-8.10 I used  switchconf to swap xorg.conf files at login so I could boot with or without restricted drivers, (Nvidia). Now days these drivers seem to load automatically no mater what xorg.conf says.
Result is the Full install pendrive may not always work on every computer.
I should probably check if switchconf is working again with 9.10.

---

