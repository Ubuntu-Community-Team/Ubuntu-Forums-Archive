---
title: "Ubuntu as a USB server?"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by bigkahuna on 2008-11-12
I've got a bit of an unusual project that I need some help with.  I have a number of USB devices (1 webcam, 1 GPS, and 2 machine controllers) that I want to access remotely (these will be used in a robot).  I've looked at using a USB extender, but for the same amount of money I can get a mini-ITX board computer so that got me thinking.  Why not us Linux on a mini-ITX as a USB server?  Basically I'd have a mini-ITX computer in the robot connected to the USB devices and running Ubuntu then connect to a second computer via a peer to peer network.  Is this even possible with Ubuntu?  I know I can share drives over a network but can I share USB devices?  I'm a bit of a noob when it comes to networking and haven't done much with Linux or Ubuntu in a long time, any advice is appreciated.  Thanks!

---

### Post by Rhubarb on 2008-11-12
I'm not sure this is possible for you, but I do know a few things that may be of help to you:

You should be able to stream the webcam video stream across a network, vlc is one such example that should be able to do this.

There's a really nice application called "gpsd" - GPS (Global Positioning System) daemon.
It allows you to share access to your GPS device among several applications simultaneously.  It also works over a network on TCP port 2947.

I hope this is of some help.

---

### Post by bigkahuna on 2008-11-12
VLC - That's an excellent idea.  I never realized it was capable of video streaming.  Plus I might be able to do it from a Windows machine, which would give me all sorts of flexibility.

I looked at GPSD once before a while back, I'll give it another look.

Any idea how I would access other USB devices?  I need to basically send/receive ASCII strings to a particular USB port from a remote computer.  I found some commercial apps that claim to enable this, but the price for the software is nutz (as much as the computer).

---

### Post by Rhubarb on 2008-11-12
I don't really know what you could use to do that.
If the robot runs Linux, then I'd imagine it'd be easier to achieve.
And if it was done via serial port it'd be much easier again to do.

---

### Post by bigkahuna on 2008-11-12
Well the robot can run any OS we decide on using, my preference would be some flavor of Linux (preferably Ubuntu).

Assuming VLC will handle the video stream, all I need next is to be able to send / receive some ASCII strings to various USB ports.  It was suggested on another forum that I might be able to do this via SSH, but as I'm pretty noobish to both networking and Linux I'll have to do some homework to understand what that means... :)

---

