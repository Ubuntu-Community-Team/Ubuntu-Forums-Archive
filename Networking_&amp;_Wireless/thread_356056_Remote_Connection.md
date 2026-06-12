---
title: "Remote Connection"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by Loki57701 on 2007-02-08
Im trying to setup my network so that I can use my WinXp laptop to login to my ubuntu desktop remotley. I tried vnc but that wasnt really what I was looking for. All it allowed me to do was if I was already logged in to ubuntu it would replicate my desktop on a diferent screen. Im looking for a program that will allow me to connect to ubuntu and login to my own session, without having to login in locally on ubuntu. Similar to windows remote desktop connection.

---

### Post by gradedcheese on 2007-02-08
In Ubuntu, go to System->Administration->Login Window and click the Remote tab.  Configure things there and you should be able to do what you are trying to do.  Next, you need an RDP client for Windows.  I know they exist but I don't know where you get one as I don't use Windows.  Hopefully someone else can help or you can find it by searching around.

If you want just a shell login, that's much easier.  You can install openssh-server:

sudo apt-get install openssh-server

and then from Windows, log in with an ssh client like Putty or whatever other ones you can get in Windows.

---

### Post by veloce on 2007-02-08
Well that doesn't work for me.  On the linux side it talks about XDMCP, is that the same as RDP?

Veloce.

---

### Post by gradedcheese on 2007-02-08
Sorry, I got myself all confused: RDP is actually the protocol Windows uses for its terminal services.  XDMCP is the remote X protocol, I think you can use a VNC client on Windows for that actually.  Can you test that?

---

### Post by veloce on 2007-02-08
VNC definately works, but it doesn't give quite the functionality (read performance) of rdp.  I suppose it transfers too much across the connection. 

Veloce

---

### Post by hebbal1273 on 2007-02-08
U can use NXClient from [www.nomachine.com](www.nomachine.com). Load the NXServer onto Ubuntu & the NXClient on XP. You can now connect remotely. Its very good & I can vouch for it. Remember to install ssh server first using the snaptic package manager.

---

