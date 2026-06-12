---
title: "sending files over internet ssh"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by CameronCalver on 2007-12-10
Hello i have a problem , i need to be able to scan documents at home and copy them to a ssh on the computer an hour away threw the internet.
 i need some help forwarding the ports so i can connect to this computer over the internet  , i would also like to remote desktop.
Thanks 
Cameron

---

### Post by jasmuz on 2007-12-11
Hello,

Its very easy to do.. just have the remote machine install "ssh-server".
And on your machine make a connection to that machine.
In the GNOME menu, its Places-->Connect to server

That will make a desktop link to that machine's share. Allowing you to send and copy back in a seamless way the data you need.

Of course, the only thing you will need is the Host computer's IP address.

---

### Post by kevdog on 2007-12-11
Are both computers running linux, or is one running Windows?

On the remote computer are you going to be going through a router to connect to the computer?

---

### Post by CameronCalver on 2007-12-11
Both computers go threw a router yes so i dont need to do any port forwarding??
so i do
Server : the hosts ip address
Port: ??? is it 22 or what?
Folder: /home/calver/
Name: Server
 

Will this all work or what? also how would i do the same but vnc the host machine? 

P.S both gutsy gibbon

---

### Post by kevdog on 2007-12-11
So on the ssh server with the associated router, you need to port forward 22 to the internal LAN address of the server and make sure that you open port 22 on the server's firewall to allow inbound connections.  The easiest way to open port 22 on the firewall is to use either Guarddog or Firestarter.

Yes all of this will work.

Make sure you have a user account on the server with the public key (openssh) located in the ~/.ssh/authorized_keys file.

---

