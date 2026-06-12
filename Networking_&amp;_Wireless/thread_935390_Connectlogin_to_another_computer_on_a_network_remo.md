---
title: "Connect/login to another computer on a network remotely - help"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by joao82 on 2008-10-01
Hi.
I have two laptops running Ubuntu connected to a modem/router making a small home network.
One of the laptops is suddenly giving a bios beep error indicating the graphic adapter isn't working so there's nothing on the screen. After the beep code the computer boots normally but still without any display.
I can see a shared folder from the troubled laptop being shared through samba on the network, but that's all, I can't access the rest of the files.
So everything is connected and working... I wanted to know if there's a simple way to login to the damaged laptop from the one that's working and access its files. Like a remote login or something.
I know the ip, user names and passwords from all the computers on the network.

when I use nmap i get this:

```
~$ nmap 192.168.1.*

Starting Nmap 4.53 ( http://insecure.org ) at 2008-10-01 21:11 WEST
Interesting ports on portatil.lan (192.168.1.101):
Not shown: 1712 closed ports
PORT    STATE SERVICE
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Interesting ports on hp-laptop.lan (192.168.1.102):
Not shown: 1712 closed ports
PORT    STATE SERVICE
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Interesting ports on speedtouch.lan (192.168.1.254):
Not shown: 1709 filtered ports
PORT     STATE SERVICE
21/tcp   open  ftp
23/tcp   open  telnet
80/tcp   open  http
443/tcp  open  https
1723/tcp open  pptp

Nmap done: 256 IP addresses (3 hosts up) scanned in 21.482 seconds

```

Is it possible to access it?
Thanks in advance

---

### Post by pytheas22 on 2008-10-02
I don't think you can access it.  If you had installed an ssh or vnc server on it previously, you'd be able to log in, but by default Ubuntu Desktop Edition doesn't run any services that would allow you to connect remotely, even if you know the IP and usernames.  I do see some open ports (ftp, telnet) that might help you, but I think they're on your router, not your laptop.  Which machine is named speedtouch.lan with IP 192.168.1.254?

You could try swapping in a different video card to get the machine working, or, if you just want to get your files back, take the hard drive out and put it into another computer.

---

### Post by joao82 on 2008-10-02
Ok, thanks for the advices.
The speedtouch.lan device is the modem/router.

---

