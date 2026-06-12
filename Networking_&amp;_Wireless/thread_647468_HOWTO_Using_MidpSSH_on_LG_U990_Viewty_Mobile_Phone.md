---
title: "HOWTO: Using MidpSSH on LG U990 Viewty Mobile Phone"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by triplestones on 2007-12-22
Hello World!

This is my first posting, so apologies if it shouldn't be here, but I'm running ubuntu 7.10 and have just managed to establish a SSH connection to my box from my **LG U990 Viewty **(on 3 Network in the UK) using **MidpSSH **after a few attempts which initially failed and thought I'd share the knowledge!

Firstly, I have to make clear that I had already established a working SSH connection from an XP machine using **Putty** and this HowTo doesn't cover the setup of that... Mainly because a friend of mine took care of that for me. This infomation simply relates to the setting of **MidpSSH** on the phone as the default setting don't work.

The first step was to download **MidpSSH** via WAP to the phone. The link can be found here: 
[http://www.xk72.com/midpssh/download.php]("http://www.xk72.com/midpssh/download.php")
(I downloaded the "Full Build MIDP 2.0")

After an initial error ("Reader: java.io.IOexception") when trying to connect, I tinkered with the various settings and eventually hit on the following change which then got things working perfectly:

From the main menu, select "Settings" then "Network" and change "Polling I/O" to ON

Then all you have to do (if you already haven't) is setup your session so that it points to the internet IP/DNS of your ubuntu box and away you go!

Remember: If you're using a router, this will also need to be configured to forward Port 22 to the ubuntu box too if it hasn't already been done.


Enjoy! :D

---

### Post by K.Mandla on 2007-12-25
Moved to Networking and Wireless.

---

### Post by peher on 2008-03-31
Hello,

Does this work for everybody ?
I still have the Java.IO error.

---

