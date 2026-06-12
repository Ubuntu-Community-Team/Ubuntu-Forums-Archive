---
title: "Connecting from windows xp to ubuntu"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by orestis25 on 2010-01-26
Hi everybody,

I would like to know a way to connect from the office (windows xp) to my home computer, where I have ubuntu installed(and XP as well).

I can leave my home computer on all day with ubuntu on.
I do not have a static IP but I have a name in DynDNS
I would like to be able to see graphics, mostly images.
Should I open a port in my modem-router?

I tried using vnc viewer but I got a 'connec&#964;ion timed out'
I probably am forgetting a bunch of stuff.

Thanks

---

### Post by blazemore on 2010-01-26
It's not recommended to run VNC over the unencrypted Internet.
You should use a technique called "ssh tunneling" to achieve a secure connection.

Here's what to do

**On your Ubuntu PC** (You'll only have to do this once)

[LIST=1]
[*]Install the *x11vnc* and *openssh-server* packages ([click here to install x11vnc and openssh-server]("apt:x11vnc,openssh-server"))
[*]If you have previously reconfigured the firewall on your PC, make sure the firewall allows incoming connections on port 22 from anywhere, and on port 5900 from localhost (also known as 127.0.0.1)
If you have not ever touched the firewall, you should be alright. (Someone correct me if I'm wrong)
[*]If your PC is connected to a router, set up port forwarding to forward all traffic on port 22 (ssh) to your Ubuntu PC. Your router's documentation will show you how to do this.
[/LIST]
[B]On the Windows (client) PC (You'll only need to do this once)
[/B]
[LIST=1]
[*]Download the application "Putty", which is standalone Free Software to start an SSH connection. If your workplace doesn't allow this, find out if they have other software which can do the same job. Putty can run off a flash drive.
[*]In the Putty configuration window, go to Connections -> SSH -> Tunnels
[*]In the Tunnels section of Putty, type 5900 for source port, and localhost:5900 for destination.
[*]Go back to the Sessions window of Putty
[*]type [email]YourUbuntuUsername@DynDNSURL.com[/email] in the Host Name (Or IP address) box and click SSH
[*]Type "Home" for Saved Sessions and click Save
[/LIST]
[B]On the Windows (client) PC (You need to do this every time you connect)
[/B]
[LIST=1]
[*]Run Putty
[*]Click the "Home" saved session, and click Open
[*]Type your password and hit return/enter on your keyboard
[*]Now you're logged in to your home PC, run ```
x11vnc -safer -localhost -nopw -once -display :0
```
[*]Use your favourite VNC viewer (I like TightVNC) to connect to *localhost::5900*
[*]Profit
[/LIST]

---

### Post by Kenny_Larsen on 2010-01-26
Also have a look at freeNX as well as VNC I tend to find it it faster more stable.

Kenny

---

### Post by airtonix on 2010-01-26
VNC won't let you copy the files from the ubuntu to your windows machine.

To do that you have two options : 

**Direct SSH Server**
 local loopback ssh connection to your ubuntu machine via putty for the windows machine, which you then use to point the win32-ssh-fuse driver at.

 requires : 
  1. ssh-server running on the ubuntu machine
  2. relevant ssh port forwarded to the ubuntu machine from its connected internet modem
  3. win32-ssh-fuse driver software on your windows machine Something like [Dokan]("http://dokan-dev.net/en/").

  *Opensource Method : *
  + [http://dokan-dev.net/en/docs/dokan-sshfs-readme/](http://dokan-dev.net/en/docs/dokan-sshfs-readme/)
  + [http://niallohiggins.com/2009/05/12/mount-remote-filesystems-via-ssh-on-windows-with-free-software/](http://niallohiggins.com/2009/05/12/mount-remote-filesystems-via-ssh-on-windows-with-free-software/)

  *Proprietary Method : *
  + [http://www.expandrive.com/windows/](http://www.expandrive.com/windows/)

**Samba Via SSH**
 local loopback ssh connection to your ubuntu machine via putty for the windows machine, which you then use to map the samba shares on your ubuntu machine to the windows machine.

  *Requires : *
  1. SSH server installed on your ubuntu machine
  2. samba installed on your ubuntu machine
  3. relevant ssh port forwarded to the ubuntu machine from its connected internet modem
  4. putty available on your windows machine
  5. permissions to change some network interface options on the windows machine

  *Method : *
  + [http://www.damtp.cam.ac.uk/user/jp107/xp-remote/ssh-map/](http://www.damtp.cam.ac.uk/user/jp107/xp-remote/ssh-map/)


--edit : adding Hamachi as an option.

I recently remembered that Hamachi is an option.

Hamachi provides a way to create a Virtual Private Network.
Hamachi can be used in place of ssh in the steps above.

---

