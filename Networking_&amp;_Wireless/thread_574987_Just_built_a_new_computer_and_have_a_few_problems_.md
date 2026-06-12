---
title: "Just built a new computer and have a few problems with Ethernet and loading"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by FenrirVII on 2007-10-13
Ok we just built a new computer-

Intel Core 2 6300  processor with 1gig of Ram all using a Gigabyte mobo.

Used 64 bit live disc of Fiesty Fawn and installed it, was working good in Live disk mode.
After the reboot, it loads very slow.  Like 8 mins to just get to the Ussername and Password part.
And then to top it off.. The ethernet card is there, but its not getting a connection, and im using the same connection that im using on this computer.

And then i tried with the normal 32bit, Linux Mint.  It had every same symptom again, Loading real slow, and no ethernet.  Could it be the BIOS on the Mobo or anything?  Then I also Tried with a normal fiesty and then Damn Small Linux and still no connection with Ethernet.  Im just stumped at whats going on.. Ive been problem free for 5 months until i tried to build a new computer..

---

### Post by noob12 on 2007-10-15
If you have a very new wired Intel ethernet device and are running Feisty you may need to build your driver.  Here's a thread:  [http://ubuntuforums.org/showthread.php?t=551720](http://ubuntuforums.org/showthread.php?t=551720)

Use **lspci -nnvv** and check the device id of your Ethernet device against the list there to see if it is one of the ones listed.

---

