---
title: "Error resolving server on auto update"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by 2ill4brasil on 2010-09-02
Hey guys,

Just installed Ubuntu to set up my first web server, and everything seems to be running smoothly except for a very minor detail: the internet connection.


To do an auto update I type: sudo aptitude update && sudo aptitude dist-upgrade

I get this in response:

Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
   Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
   Temporary failure resolving 'us.archive.ubuntu.com'
... [repeats for about 12 other links]

I'm running an ethernet cable directly from my cable modem (comcast) to my computer ethernet port. My ethernet appears to be working: when I type ifconfig, there are about 14 MB of RX bytes and 417 KB of TX bytes.


My other computers run all internet connections smoothly from the modem.

Any ideas on how to troubleshoot? All input is greatly appreciated; I'm 100% fresh off the windows boat, so total Ubuntu noob. Btw I'm following this guide: [http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)


Thank you!!! :popcorn:

---

### Post by 2ill4brasil on 2010-09-02
Update: How do I fix this?

---

### Post by llamabr on 2010-09-02
Right.  does your internet work normally, and you're just having trouble updating?  Or are you complaining that you don't have any internet?

The problem with that error is some messed up lines in your /etc/apt/sources.list or /etc/apt/sources.list.d/

Have you messed with those?

---

### Post by Cypress421 on 2010-09-02
Change the server to main in Software Sources, under the system, admin menu instead of your local one.

---

### Post by 2ill4brasil on 2010-09-02
Cypress, that makes no sense to me :p but would be interesting to find out what you mean



llamabr: THANK YOU for your input. I researched sources.list and updated something. . . Not sure what I did but now I'm updating like there's no tomorrow.

For future reference here's the link I used: [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by Cypress421 on 2010-09-02
Go to System -> Administration -> Software Sources, enter your password, then choose the main server and reload, the errors should disappear.

---

