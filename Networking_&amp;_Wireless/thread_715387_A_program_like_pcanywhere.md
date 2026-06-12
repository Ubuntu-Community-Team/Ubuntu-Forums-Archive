---
title: "A program like pcanywhere"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by TheMixtureMedia on 2008-03-04
HI there I am wondering if there is a program for Ubuntu that works like pcanywhere I want my 2nd computer to have no mouse no keyboard or monitor. I want to use it from my main computer can anyone help me with this oh and I do not want to use wine to run pcanywere I want one for linux please.

---

### Post by Whiffle on 2008-03-04
[http://en.wikipedia.org/wiki/Secure_Shell](http://en.wikipedia.org/wiki/Secure_Shell)

---

### Post by Joeb454 on 2008-03-04
Are you trying to connect from an Ubuntu machine to another Ubuntu machine?

And are you wanting to be able to see the desktop as well (i.e. not work from a terminal only)

---

### Post by Slingshot on 2008-03-04
Enable remote desktop from settings > preference. Tick Allow user to control my desktop. Untick ask for your confirmation box and set a password if you want. Write down your IP address so you know what to connect to later (from terminal type ifconfig or right click the network manager icon in system tray and click information).

At your main computer download a freeware VNC view (if its windows there WinVNC, ultraVNC - if its Ubuntu use the terminal client and select VNC). Enter the IP address to the Ubuntu machine and you away.

---

### Post by TheMixtureMedia on 2008-03-05
> **Joeb454 said:**
> Are you trying to connect from an Ubuntu machine to another Ubuntu machine?

And are you wanting to be able to see the desktop as well (i.e. not work from a terminal only)

Yes I want to use that machines desktop from another computer.

---

### Post by kevinatkins on 2008-03-05
Another possibility, given that you're using Ubuntu on both machines, would be to use XDMCP. This gives you a proper X session over your network. On the 'headless' machine that you want to log in to remotely, go to Administration -> Login Window, then choose the 'Remote' tab and change from disabled to one of the other options. On the machine from which you wish to connect, at the login window, choose 'XDMCP' option from the menu bottom-left, select the remote machine, and then click 'connect'...

There's just one small fly in the ointment here - er, XDMCP still seems to be borked in Ubuntu 7.10 - all other versions worked great though.....

---

