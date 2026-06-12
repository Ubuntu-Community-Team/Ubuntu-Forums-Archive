---
title: "Frustrated with printer setup"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by Al Fischer on 2009-02-18
I have spent the last 2 days TRYING to install 2 printers on 2 different print servers that are currently working in XP. I have searched and read many threads where it appears that this is a normal problem and there seems to be no solution. One thread said that cups services should be running, mine is not. Another rather lengthy thread stated that by default it was not started. Isn't attaching a printer a normal thing to want to do? I have NEVER seen a system from the lowest CPM or DOS to the highest water cooled IBM mainfram that had no printer attached.

Could someone please point me in the direction of installing a printer. 
Printer 1. HP Deskjet 5650  192.168.1.10 Server SC442410_P1
Printer 2. Hp Laserjet IID  192.168.1.11 Server SCB52836_P1

I even tried the cups setup but had not a clue what some of the entries such as URL would be. Not indicated anyplace on the XP print setup or for the server setup. The servers are both Linksys Etherfast EPSX3 and the setup was not at all difficult for XP.

Please, I am getting desperate.

---

### Post by cmnorton on 2009-02-18
As far as setting up printers, I suggest you use [http://localhost:631](http://localhost:631). Probably, you'll need to part of the lpadmin group. Ubuntu's printer setup is quite good, but I like CUPS' native interface. However, you don't need to use this interface to fix your problem.

I posted the necessary information in this link:

[http://ubuntuforums.org/showthread.php?t=1056006](http://ubuntuforums.org/showthread.php?t=1056006)

both for non-port 9100 devices and traditional HP JetDirect printers (port 9100). This shows the /etc/cups/printers.conf entries necessary for the connections.

---

### Post by scorchgeek on 2009-02-18
Are you sure the printers are compatible with Linux? Look them up at [http://www.linuxfoundation.org/en/OpenPrinting/Database/DatabaseIntro](http://www.linuxfoundation.org/en/OpenPrinting/Database/DatabaseIntro).

---

### Post by Al Fischer on 2009-02-18
Thanks. Your post is coming out of the printer right now. I will attack it with great vigor and post results. I WILL NOT give up!!!

---

### Post by click4851 on 2009-02-18
I have a working HP C-series AIO at home, when I get off work I can post my setup.

---

### Post by Al Fischer on 2009-02-18
I think what I need is how to accomplish it if possible using gnome but if need be I will open a terminal and struggle with VI. VI is still very new to me (less than a week) but I am one determined cuss!

Right now I have the cups page open and do not understand the "Device URI for Deskjet" panel.  Examples are shown but not sure which one to use or the term to enter.

---

### Post by cmnorton on 2009-02-19
The post I used is in the link I posted. That particular printer is not a Windows server printer; it's shared off an XP system.

---

