---
title: "a few basic questions about networking an ubuntu box to a Windows 10 box..."
date: 2020-05-12
forum: Networking &amp; Wireless
---

### Post by the-ides-of-march on 2020-05-12
Dear All,

I am new to Ubuntu.  I have just installed Ubuntu DDE.

I have two machines that are connected the same domestic router.  One is an AMD FX8350 box (running Ubuntu) and the other is an AMD Kaveri box running Windows 10.

I am interested in a relatively simple way that I could be able to create network connection between the Ubuntu box and the Windows box.

Ideally I would like to be able to see the directories from my user account on the Windows machine on the Ubuntu one.

Then while working at the Ubuntu machine I would be able to do the following things:

1.  Create new directories on the Windows machine remotely from the Ubuntu one.

2.  Create new files (e.g. Word processing documents in Libreoffice) and copy or move them on to the Windows 10 machine remotely from the Ubuntu one.

If this is the wrong site to ask advice on such a topic I apologise for doing so.  

I would appreciate being directed to another more appropriate forum if necessary.

Many thanks

Regards

Michael Fothergill

---

### Post by TheFu on 2020-05-12
What do you know about TCP/IP networking?  
Do your system have static IPs on the LAN?
Which version of Windows is being run?
Which version of Ubuntu is being run?

The normal way do connect to Windows storage is by using either an SMB or CIFS client from any Linux/Unix system. Recent changes have made both Windows and Ubuntu releases need fairly specific settings to work.

You can also go the other direction.  Use Linux as the "server" with storage and allow access from other systems, including Windows, as the clients. There are generally more options going in that direction.

In general, it is best if all systems are wired ethernet onto the same LAN.  Flaky wifi is bad regardless of the method used.
For Win10 as the the file server, [https://ubuntuforums.org/showthread.php?t=2435292&p=13925468#post13925468](https://ubuntuforums.org/showthread.php?t=2435292&p=13925468#post13925468) If you have specific questions, someone may be able to help.

---

