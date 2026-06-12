---
title: "SSH Tunnel"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by DoubleMcLovin on 2008-12-18
Ok heres the idea:

I want to have another computer connect to this computer via an automated script using SSH and create an encrypted tunnel with port forwarding.

Using this tunnel I plan on connecting to the computer via a VNC application. But I require the tunnel first, which will be listening in on the port that the VNC application is waiting for to ensure that all traffic goes through this tunnel.

My hopes is that by doing this, I can avoid setting a static IP address on the computer running the script (client) though I don't mind setting a static IP address on the computer it will connect to (host).

I am currently configuring a test environment locally so as to avoid any forwarding right now.

Basically my question is:
How do I configure my OpenSSH-Server on the (host) computer to allow all of this? Can I set up a user account that has no access privileges that the (client) can connect as that way I can ensure security for the (host) and still be capable of doing all of this? And finally, do I even need to enable the port forwarding in the SSH for this setup to operate effectively?

---

### Post by overdrank on 2008-12-18
Hi and this may help
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by physeetcosmo on 2009-03-17
> **overdrank said:**
> Hi and this may help
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Thanks overdrank, great info!!

---

### Post by blueridgedog on 2009-03-17
Here is my collection of random junk that I noted down when trying to get this working.  It is pretty much some random copy/paste text from research, and links to where it came from.  It may get you thinking.  As a rule, I generally create these sort of text files (that seem to stay with me for years) when researching something.  I have some dated back to '94 (getting inet.d working)

ssh -L 5921:localhost:5920 [email]user@ssh.server.com[/email]

$ ssh -L 5901:localhost:5901 -N -f -l rocky sshserver.mydomain.com
OR

$ ssh -L 5901:127.0.0.1:5901 -N -f -l rocky 192.168.1.100

Where,

    * -L 5901:localhost:5901 : Specifies that the given port on the local (client) host is to be forwarded to the given host and port on the remote side. Here you are using port 5901 on the localhost to be forward to sshserver.mydomain.com on the 5901 port.
    * -N : Do not execute a remote command i.e. just forward ports.
    * -f : Requests ssh to go to background just before command execution. Requests ssh to go to background just before command execution. Once password supplied it will go to background and you can use prompt for type commands on local system.
    * -l rocky : rocky is the user to log in as on the remote machine (sshserver.mydomain.com).
    * sshserver.mydomain.com (192.168.1.100): Remote system with VNC server

In your localhost VNC client use 127.0.0.1:5901 for connection. Make sure you use appropriate port i.e. 5901 (VNC server was running on display 1).

vncviewer -via user@host localhost:0

To get the server installed:
 
sudo apt-get install openssh-server openssh-client 


[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

