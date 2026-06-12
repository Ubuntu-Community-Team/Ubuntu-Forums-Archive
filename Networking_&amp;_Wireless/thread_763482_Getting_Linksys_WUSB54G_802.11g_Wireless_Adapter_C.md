---
title: "Getting Linksys WUSB54G 802.11g Wireless Adapter Connected to Internet w/ 8.04"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by wron_00 on 2008-04-23
Called 1-800 # for Linksys.  They said there were no drivers created for Linux systems to make their adapter work.  I don't believe that.

For hours I have entered every combination of my 10 digit # written on my router, Authentication Setting, WEP-128, WEP64/128, etc to no avail.  My router shows up as being detected. Power light is on.  Link light flickers when it tries to connect.  Never connects.

Something else that is interesting that I can't figure out.  When I try to make the wireless connection on one computer, it automatically cuts the connection of my wired internet computer.  Why is that?

I am looking for an easy fix to be able to use Wireless Internet w/ Ubuntu 8.04 Hardy Heron.  I suspect it has something to do w/ a security setting or the information I am entering.

Any suggestions are appreciated.

---

### Post by Crafty Kisses on 2008-04-23
I have a Linksys router working fine with Linux, see if the following works:
```
192.168.1.1
```
See if you can enter the router, see if you need to change anything. I also have a older model of the Linksys router, so I find it hard that your router would not work in Linux.

---

### Post by nicedude on 2008-04-23
I just looked around and see that your USB wifi uses the Prism54 chipset so you can go here to learn more [http://prism54.org/](http://prism54.org/) but also I saw people say that Prism54 works with Ndiswrapper which is a program to let you install windows drivers for your Wireless device on a linux PC so you might want to check that as well. And yes its true that linksys doesn't make any Linux drivers for that device or any of their devices most likely, Its just part of the Microsoft anti-linux conspiracy. They have to keep people on their ship somehow and it sure isn't with quality products :-)

---

### Post by nicedude on 2008-04-23
Also your WUSB54G is a USB wireless adapter but what brand & model of router do you have? Have you used your wired PC to log into your router to set up your wireless? Like the other guy said just open a web browser on your wired computer and in the address bar type 192.168.1.1 should then ask you for your login

---

### Post by kevdog on 2008-04-23
Unless you use a different subnet, or bridge the connectors, or run Internet Connection Sharing, or do something different, you can't run wired and wireless at the same time.  Hence the reason why your wired connection is taken down when the wireless connection is brought up.

---

### Post by miesnerd on 2008-04-23
wron's connecting to a 2WIRE and it seems like he can connect, but cant get past the security. If anybody's got AT&T DSL, 2WIRE is the standard modem they use. He's referring to the 10 digit password on the bottom of his modem.

---

### Post by miesnerd on 2008-04-23
also, what are the chances wron can just install wicd and things will work?
I know sometimes its better at network connection than networkmanager.
Similarly,(this is my question, not wron's) why cant you have both wicd and network manager installed at the same time and choose to only have one run?
Why does installing one uninstall the other?

---

### Post by Happy Grandad on 2008-04-23
Try this thread: [http://ubuntuforums.org/showthread.php?t=588045](http://ubuntuforums.org/showthread.php?t=588045)

---

### Post by miesnerd on 2008-04-23
wron, the link that happy grandad provides is super long, but on page 17, people are reporting that a method by Pavlick (using Ndiswrapper) works. Since you have wired connection, you can follow that and should be able to have success.

---

