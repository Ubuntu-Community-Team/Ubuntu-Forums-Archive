---
title: "Ubuntu sharing internet from windows"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by AlexBIOSS on 2007-12-12
Hello,
  I want to get started with Ubuntu (linux in the process) on my desktop and I need to connect it to the internet. The internet is being used by a computer running windows. I have a ethernet LAN cable running between the 2 computers and the internet connection on windows I have set the properties to share. On Ubuntu I searched the network places and saw a windows icon appear, but it did nothing when clicked on and Ubuntu does not have its internet working. The connection on the windows machine is through usb and I do not have a wireless router. I do not know what is meant by a switch either. 
From another post I gathered this suggestion, but should this work?

Code:
   sudo gedit /etc/network/interfaces
and add the following lines:
Code:
   auto eth0
   iface eth0 inet static
   address <your ip>
   subnet <your subnet>
   gateway <your windows machines ethernet cards ip address>
and then restart networking:
Code:
   sudo /etc/init.d/networking restart

How should I go about the problem?
Thanks, Alex M.

---

### Post by schmildo on 2007-12-12
Yeah I think that code should work, that is probably the ticket. Please let me know how it goes, I was trying to help someone else out with a similar setup over here:

[http://ubuntuforums.org/showthread.php?t=638521](http://ubuntuforums.org/showthread.php?t=638521)

Do you have two network cards in one machine?

A switch is just a physical box with usually  5 or 8 ethernet ports (the same port that is on the back of your network cards that the ethernet cable plugs into). You plug all your computers (and your router) into it. It allows each computer to send data directly to where they want to go, instead of having to go through another machine. It actually looks at the packets of data and inspects who sent it, and where it's going, then sends it directy to that PC.

If you have one I suggest you grab it and use it. It'll make your life easier.

---

