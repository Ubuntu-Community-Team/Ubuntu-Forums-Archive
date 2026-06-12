---
title: "Why is it so complicated"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by thedrifter on 2009-03-20
Im new to Linux in general and im pulling my hair out.  I installed Ubuntu and no problem.  Except my Wireless doesnt work.

After some research I found that I have a Broadcom 4318.  Basically there are 2 ways of getting it to work.

1) install b43-fwcutter
2) install the windows drivers using ndiswrapper.

Should be simple...but ive been hacking at it for a couple hours a just trying to get commands to work in the terminal.

I do :
1. Sudo bash
2. apt-get install b43-fwcutter
3. Wait for install to complete
4. rmmod b43 ( ignore "not loaded" message)
5. modprobe b43
6. ifconfig wlan0 up

Everything working fine until the 6) where i get the message SIOSCIFFLAGS: no such file or directory

So I thought maybe ill try the other way - with ndiswrapper.  I managed to get the windows drivers i need, but i dont know where to go from there, where to get ndiswrapper how to set it up, if it needs anything else.

I want to get away from XP, but it shouldnt be this difficult :(

---

### Post by kanikilu on 2009-03-20
I feel your pain - even when I did eventually get wireless working on my laptop, I couldn't get it to work with the stupid 802.1X enterprise authentication that my university uses :???:

For ndiswrapper, did you already try following the documentation?

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

If so, post specific questions/problems, and hopefully someone can help you.

// Edit - Also, a quick search brought up this (somewhat old) thread that seems to apply to your specific wireless chipset. Not sure if it will help or not, but...can't hurt.

[http://ubuntuforums.org/showthread.php?t=265284](http://ubuntuforums.org/showthread.php?t=265284)

---

### Post by SunnyRabbiera on 2009-03-20
Wireless can be a pain, its not really any real fault of Ubuntu as when people make wireless devices they think only of Windows.
Actually if you want to save yourself some trouble try linux mint instead, Linux mink has NDISGTK a front end for NDISWRAPPER.
If its a broadcom as indicated, I am not surprised, Braodcom support sucks for Ubuntu.

---

### Post by ugm6hr on 2009-03-20
If you want help, confirm some details first.

See the Wifi help? link below.

If you have a wired connection, and are using 8.04 / 8.10, you should be able to just activate the driver in System -> Administration -> Hardware Drivers.

---

