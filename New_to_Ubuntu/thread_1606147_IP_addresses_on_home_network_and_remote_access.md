---
title: "IP addresses on home network and remote access?"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by ch40s on 2010-10-26
I'm using Ubuntu 10.10 and I'm trying to remotely connect to a Windows XP computer that is using the same internet connection. I'm just curious as to how this is done, both computers are mine. 

1. How would I find the IP address of the Windows computer on the same network remotely/without going on the other computer?

2. How do I remotely connect?

I only know very rudimentary terminal commands, how to navigate my own system, move and edit files, etc., no networking. :tongue:

If you don't want to explain it and know a good manual/guide online, then please share. I've been looking everywhere but haven't found anything on my level. 

Thanks in advance! :-)

---

### Post by bruno9779 on 2010-10-26
If you don't know the IP of a machine on the local Network, you can either look it up in the Router or try and guess it (if DHCP is used it shouldn't be hard to guess)

You need specific clients to connect to another machine.

ie. I can log into my wifes laptop via SSH as she uses Ubuntu as well. I can log in my computer via Windows with PuTTy. But I don't know how to get in a Win machine.

if you need graphic access to the desktop, and cross-plattfor compatibility Gitso (on google code) is worth trying out.

---

### Post by fatality_uk on 2010-10-26
Are you using a router to establish network connections? This is where you need to start. Open you routers homepage, it will usually be something like [http://192.168.1.254](http://192.168.1.254) and in there, depending on the type o router, there will be a page showing a list of all the PC's connected to your network.

Once you know that, there are a couple of options such as remote desktop viewer or VNC to allow you access to the XP machine.

---

### Post by msaravanan77 on 2010-10-26
1. How would I find the IP address of the Windows computer on the same network remotely/without going on the other computer?
    From ur ubuntu machine try Broadcast ping. (Ex: ping -b 192.168.0.0) and then try arp data. (Ex. arp -n).

---

### Post by rbc on 2010-10-26
I use nmap to find which IPs are assigned to which computers.
```
sudo apt-get install nmap
```
Then issue this command:
```
sudo nmap -PR -sP 192.168.1.0/24
```

You may have to change the IP address, depending on how your router assigns them. 

There is also, Zenmap, a graphical frontend for namp, and Angry IP Scanner. I am not sure if they are in the repos. I do not know why, but both GUI applications have trouble finding my Windows computer

---

