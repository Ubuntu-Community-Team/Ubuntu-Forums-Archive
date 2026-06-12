---
title: "It can see the network but nothing"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by michael_besselman on 2007-05-15
I am relatively new at wireless networking with ububtu.  This system works with my windows OS so I know that there is no problem with the hardware.  Currently I have a wire to the computer for but it is running through the hall and you can imagine how my wife feels about that.

I have the wireless software installed.  It sees the network and I can enter my encription key.  However, it will not link up to the network.  Is there a way to set the channel that ububtu is looking for?  In the router I am set to 6.  If it is not possible to set the channel on the computer, I can change the channel number of the network to the one ubuntu wants, but how do I figure out what channel the computer is looking for?

Michael Besselman

---

### Post by chili555 on 2007-05-15
When you try to connect, it will run through all the channels until it finds a signal to try to connect to. Setting the channel explicitly is generally not required.

Are you running Feisty that installs Network Manager by default? According to the Ubuntu wiki:> Network Manager aims for Network Connectivity which "Just Works". The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection.So, as you can see, NM is designed to *not allow* a wireless connection if that ugly wire is hooked up. Please detach the wire, restart networking:```
sudo /etc/init.d/networking restart
```and see if your wireless starts. If not, post back and we'll troubleshoot your settings.

---

