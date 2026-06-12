---
title: "cant install nvidia sound driver"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by stu28stu on 2009-05-13
HI

I am new to using linux, first time today. seems to br going ok so far.
But i cant install my nvidia sound driver, i keep getting this message

[/home/stu/Desktop/DriverRobot_Setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/stu/Desktop/DriverRobot_Setup.exe or
          /home/stu/Desktop/DriverRobot_Setup.exe.zip, and cannot find /home/stu/Desktop/DriverRobot_Setup.exe.ZIP, period.

I really dont mind replys being very very simple to understand, 
hope some one can help

stuart

---

### Post by Skripka on 2009-05-13
In the 1st case, you should not need a sound driver.  ALSA is your sound driver, and odds are it should work fine and was installed by default.

In the second case, *.exe are windows executable files-they are not suited to Linux, especially for installing drivers.

---

### Post by MontelEdwards on 2009-05-13
> **Skripka said:**
> In the 1st case, you should not need a sound driver.  ALSA is your sound driver, and odds are it should work fine and was installed by default.

In the second case, *.exe are windows executable files-they are not suited to Linux, especially for installing drivers.
He is right.


Most of the time, there is an error with your settings or Ubuntu. Most sound card drivers are already supplied in the Kernal. But I would check your volume and PCM levels. And i would google "ubuntu 9.04 no sound" or whatever distro you have.

---

