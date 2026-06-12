---
title: "How Do I Tell Ubuntu to Dial"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by dgoddard1 on 2008-09-15
I am fairly new to Ubuntu and have only dabbled in Linux, I know a little command line but most of the "jargon" confuses me.  I am trying to get free from the clutches of MS.

-- I now have a new Dell Studio 1535
-- The Ubuntu version is 8.04
-- I have a US Robotics USB modem  Model USR5637
-- -- For this modem, US Robotics claims that if the kernel is 2.4.20 or higher that installation of the modom is fully automatic (if plug an play module is enabled)  
-- I have everything done in the network settings (System/Administration/Network/Network settings/Point to Point connection/Properties) except I am waiting for the DNS addresses from my internet service provider.  This was done as instructed by System/Help and Support/Internet/Modems/Connecting 

What I don't have the foggiest idea how to do is how to tell Ubuntu to go ahead use the modem to dial me into my internet service provider.

I don't want the various applications to initiate the dialing.  I want to be the only one to tell Ubuntu when to dial.  It is a control issue for me.  I don't want software making connection without my explicit case by case permission.

A 
How do I tell Ubuntu to make the connection.
B.
How do I keep software applications from initiating a connection?

---

### Post by ModelM on 2008-09-15
I think you'll get some useful info by looking at [ _this thread](http://ubuntuforums.org/showthread.php?t=873268)_.

---

### Post by Winston_Smith on 2008-09-15
I just setup my modem also, I had problems with network manager. You can get a program called Gnome-ppp which is pretty much just like the windows dialer. You start Gnome-ppp up enter all your settings and click dial.

If your currently setup with network manager you'll want to remove the modem settings from it. You'll find it under System>>Administration>>Network You want to disable the point to point connection for your modem.

Installing Gnome-ppp is easy, sudo apt-get install gnome-ppp

Now you have full control over when it dials in.

---

