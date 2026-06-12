---
title: "Dia-Up - Can't connect, can't even start to try (7.10)"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by Robotman on 2008-05-23
Howdy folks,
I need to use a temporary dial-up account from my new ISP until I get my DSL hardware.  (Ugh!)
I can't seem to make any kind of progress in getting my 7.10 installation to even dial.
I've added the "Modem Monitor" applet to my launch panel, and from there I've entered in the connection info for my dial-up service.  When I left-click on the icon, nothing happens.  When I right-click, I see a menu with the "Activate" and "Deactivate" options darkened-out and unselectable.  All I can do is go to "Properties" and bring up the "Network Settings" window.
There, I see the "Modem connection" is indeed enabled.  I've even tried every option available in the "Modem port" section, but I still can't get the damn modem to dial.
Am I missing something here?  Do I need to change any other network settings, or am I going about this in the wrong way?
Please help me, I had to dust off a Windows partition on my laptop to post this! :shock:

---

### Post by Robotman on 2008-05-25
Anyone know what I'm doing wrong, or if something is just not working right in my system?  I need to get using Linux again.... after only using Windows for a day I've already picked up 3 malware files! :mad:

---

### Post by JAYCEE1 on 2008-05-25
I had this same problem.

[http://ubuntuforums.org/showthread.php?t=806248](http://ubuntuforums.org/showthread.php?t=806248)

I ran sudo pppconfig and filled in all of the blanks there. Then I edited /etc/ppp/peers/provider and put my userid (from ISP) and modem location. I now use pon and poff to connect which works alright.

My dialup is very slow. If you know how to speed it up I'd like to know.

Good luck!

---

### Post by Robotman on 2008-05-25
No luck.  I still can't even activate my modem.  Thanks anyway.

---

