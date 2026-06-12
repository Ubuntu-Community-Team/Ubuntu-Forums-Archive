---
title: "remote connecting &amp; dynamic IP"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by StOoZ on 2008-04-25
I have ubuntu 7.10 installed, and another remote computer which uses windows xp OS.
I would like to be able to connect from the remote computer (and any other one which uses windows xp...)  to my ubuntu machine, without the need to rememeber my  IP all the time (I have a dynamic IP, whenever I restart/disconnect and reconnect again, the IP changes).
is there anyway to do this?

---

### Post by Monicker on 2008-04-25
You can use a freedynamic dns service such as provided by [www.dyndns.com](www.dyndns.com) or [www.no-ip.com](www.no-ip.com).  From you can get a hostname like stooz.dyndns.org.  A client installed on your workstation will periodically report your ip address to them and associate it with your chosen hostname.

ddclient and no-ip are a couple of the clients in the ubuntu repositories.  If you have a router at home which supports it, the router will send the information for your account.

---

### Post by StOoZ on 2008-04-25
so basically I need to sign up to the no-ip site, download 'ddclient' from the repositores, configure it, and then it will automatically notify the noip service about my IP each time it changes.

but, how do I connect to my computer remotely? (assuming I have a hostname like stooz.dyndns.org)

thanks.

---

### Post by Monicker on 2008-04-25
How you connect depends on what type of service you intend to run for remote connections.

Are you wanting to remote control your home system, or just be able to get into it?  Are you talking about specific services such as a web or ftp server?


You could run a vnc server for remote control. If you just need remote command line access, then ssh will do.

There are many windows vnc clients out there.  Putty will work for ssh access; WinSCP could be used for file transfers.

---

### Post by StOoZ on 2008-04-25
I only need access to my system via the terminal.
I mean, I would like to be able to access my computer remotely, and use the terminal to copy files from it the the guest (windows system).

---

### Post by Monicker on 2008-04-25
Use ssh.  sudo apt-get install openssh-server.  You may want to read this for informatoin about ensuring good security for SSH access:  [https://help.ubuntu.com/community/AdvancedOpenSSH]("https://help.ubuntu.com/community/AdvancedOpenSSH")

Putty will allow you terminal access to your linux machine.  Transferring files from linux to a Windows machine over the internet will require that the Windows machine has an acceesible service.

---

### Post by StOoZ on 2008-04-25
well thanks a alot!
gonna try it , and test it on a virtual machine (windows).

---

