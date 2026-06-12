---
title: "Network through windows to access internet"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by dp_wilson on 2006-10-12
I am attempting a changeover from XP to Ubuntu Dapper, and have been running around in circles trying to get my modem to work (as where I currently am all I have available is dial-up) so that I can connect to the internet to get drivers etc to get everything else working. Only my modem in my laptop appears to be an agere ac97... in otherwords a software modem with no drivers... I have tried for hours to get it working, following how to's and the like, but getting nowhere at all...
So I am now attempting to set up an network from an XP laptop to my linux one. XP one connected to the net, and connected to the linux with a crossover cable...
I have found a few threads which dance around things I could do, but none which address this specifically...
If anyone has an idea how to do this please tell me...
Thank you
Dan...

---

### Post by darrenm on 2006-10-12
Should be easy. Enable sharing of the connection in XP then in the network setup in Ubuntu set the XP box as the default gateway. If XP isnt letting you access DNS use 195.92.195.95 as your DNS server. Check its forwarding IP by pinging that IP from Ubuntu.

That being said.. Cant you just get a hardware external modem?

---

### Post by dp_wilson on 2006-10-12
don't have one lying around... and it would be a waste as I won't be here much longer...
But before I leave i would like to have most drivers etc set up, and I can't do that without internet access...
I will try that, do I need any programs on Ubuntu or is everything that I need there...

---

### Post by gewitty on 2006-10-12
I have the same issue. I've just started using Ubuntu today and am new to Linux, but need to connect the Ubuntu server through a Windows XP box in order to access a wireless broadband connection. I've enabled ICS on the XP machine, but need some guidance on what command line instructions I have to use in order to get Ubuntu talking to the Windows newtork. Any help would be much appreciated.

---

### Post by dp_wilson on 2006-10-12
thanks all done... worked a treat... I had some settings wrong on the xp machine...
Dan

---

### Post by Iowan on 2006-10-12
> **gewitty said:**
> I have the same issue.
Same basic advice - set up ICS on the Windows box, crossover cable (or hub/switch w/ straight cables) between the two.  You'll need to know (set?) the IP address of the ethernet port in the Windows box to use as the gateway on the Ubuntu box.

Command line... you *should* be able to do most (or all?) of the setup from System(or is it Settings?)>Administration>Networking - eth0 Properties. I've probably missed something, but that should get you started.

---

### Post by gewitty on 2006-10-12
Sorry to be thick, but I'm looking at a black screen with a 'username@ubuntu' prompt. Where do I find the admin screen(s) you mention? These sound like a GUI front-end, which I don't have installed yet.

---

### Post by gewitty on 2006-10-12
Maybe I should have made it clear that I'm working with a basic LAMP installation.

---

### Post by darrenm on 2006-10-12
That would be different then ;)

You will be wanting something like:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1

```

With gateway being the IP of the windows box in /etc/network/interfaces. Then put the IP of the windows box in /etc/resolv.conf

---

### Post by gewitty on 2006-10-12
No luck with those commands. None of them were recognised. It just keeps responding with 'command not found'.

Am I working with the wrong installation?

I've been able to ping my XP box with IP 192.168.1.100, so the network connection looks OK.

---

### Post by Iowan on 2006-10-13
Oops! sorry, I assumed (and we know where THAT gets you) that you were working from Gnome...
Let's back up a little (although we're kinda going off topic from the original thread).
Try ```
**more /etc/network/interfaces**
```

---

### Post by gewitty on 2006-10-13
OK that got a response. 

'This file describes the network interfaces available on your system and how to activate them. For more information, see interfaces (5).

The loopback network interface
auto lo
iface lo inet loopback

The primary network interface
auto eth0
iface eth0 inet dhcp'

That's it.

---

### Post by Iowan on 2006-10-17
gewitty:
Sorry to leave you hanging...
I doubt you're gonna want a server getting it's address via DHCP (unless you've set up a static lease).  You're probably gonna want to set up a static address in the same subnet as the Windows box.  You should be able to find the Windows address by **Run>cmd**. At the prompt, type **ipconfig**.  If the address is not in the private range (192.168.x.x or 10.x.x.x  - forgot the other one), you'll need to set it under **My Network Places >Properties>Local Area Connection>Properties>Internet Protocol (TCP/IP>Properties**.

---

