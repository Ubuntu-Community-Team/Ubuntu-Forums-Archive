---
title: "Can't set static ip address in NetworkManager"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2008-11-08
Has anyone managed to set a static IP address in Intrepid? I tried and no avail. It just resets after reboot. Also net mask, which I guess should be 255.255.255.0 for some reason turns to just 24 every time.

---

### Post by anystupidname on 2008-11-08
I suspect the 24 you're talking about is 24 bit which is equivalent to 255.255.255.0

I have set a static IP in the networkmanager before successfully/without problems but I don't have access to the version you're likely using right now... What version is that anyway?

As a workaround, you can set a static IP in /etc/network/interfaces

example:
auto eth0
iface eth0 inet static
address 1.1.1.1
network 1.0.0.0
gateway 1.0.0.1
broadcast 1.0.0.255
netmask 255.255.255.0

---

### Post by Iowan on 2008-11-08
[This]("http://ubuntuforums.org/showthread.php?p=6121250#post6121250") thread might be useful.  Apparently NM has a bug that ignores /etc/network/interfaces.

---

### Post by foxy123 on 2008-11-09
I have found the way. You have to remove the wired connection ("Auto eth0" in my case) and create a new one with the settings you like. The System settings option should be ticked. In the process you've got to authorise the changes. Do not tick Remember authorisation option as it seems to be a bug. If it's set to sort of auto authorisation, it does not save any changes.

Oh, the reason I cannot remove NM is that I've got a laptop and without NM it will be difficult to connect to wireless networks.

---

### Post by Iowan on 2008-11-09
I'll try to remember this one for next time I see a  "Can't set IP address in Network Manager" thread.

---

