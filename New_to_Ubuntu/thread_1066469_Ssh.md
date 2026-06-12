---
title: "Ssh"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by DesChamos on 2009-02-10
If I want to SSH into my linux laptop from another computer, how do I find out the information.  I know the command is more or less ssh username@ip, but where do I go on the linux laptop to find out that information?  I'm on a college network, but I've SSHd in a mac before so I know it is possible.  The only thing is, on the mac, the area after the @ was a full domain name.  Where on the laptop can I find this?

---

### Post by HermanAB on 2009-02-10
First note that ssh-server is not installed by default.  You got to do it with Synaptic.  Now to get your IP address, open a console and type:
$ /sbin/ifconfig

Otherwise, use a browser and go to [http://whatismyip.com](http://whatismyip.com)

Then, go to the other PC and type:
$ ssh username@ipaddress

Cheers,

Herman

---

### Post by DesChamos on 2009-02-12
Thanks, it wasn't installed.

---

### Post by hyper_ch on 2009-02-12
if you don't have a static IP on the machine you want to ssh into you might want to have a look at tools like [http://www.no-ip.com](http://www.no-ip.com) or [http://www.dyndns.org](http://www.dyndns.org)

---

### Post by geirha on 2009-02-12
An easier way of getting the local ip address is to right click the network manager icon and choose Connection Information.

---

