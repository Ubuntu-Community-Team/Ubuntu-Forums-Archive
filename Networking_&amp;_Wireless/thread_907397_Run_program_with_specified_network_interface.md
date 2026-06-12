---
title: "Run program with specified network interface"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by darkpaladin79 on 2008-09-01
I've been running Ubuntu Hardy for a while, and while I'm sure there's a way to do this, I don't know what to search for.  Basically I have a wired connection and a wireless connection.  Both are connected and run perfectly, and I want to tell a program to put all traffic over the wireless connection.  I would just disable the wired connection, but the computer is a headless box connected to my network with the wired.

Thanks,
Ivan

---

### Post by pytheas22 on 2008-09-01
I think it depends on the program--what exactly are you trying to run?  I'm also not sure exactly what your situation is--do you have your wireless card connected directly to the Internet, with the wired interface simply connected to a local network that's not part of the public Internet?

---

### Post by darkpaladin79 on 2008-09-01
Yes, I've got my main network connected to the internet, then a second wireless network not connected to the internet.  I've got a couple of computer in the wireless one that I use for some number crunching for a project I'm working on.  There's no sort of way I can launch a program telling it to only use one connection?  I wasn't thinking of an in-program kind of option, I was thinking of calling it from the command line or something.  I figured there had to be a way to do that.

In a post I found a while ago, someone had 2 separate wireless networks, and wanted to use some programs on each, to theoretically max the connection on both.  They thought he was trying to bridge his connection.  I've never done anything with bridging, from what I understand that involves forwarding packets from each to the other, which isn't what I'm trying to do.

Thanks,
Ivan

---

### Post by darkpaladin79 on 2008-09-01
Since this doesn't seem to be extremely easy to do, I think I'll just run the program in a VM and make the VM send all traffic to one connection.  I'm all up for easier solutions though.

---

### Post by mellowd on 2008-09-01
You might not even need to do this. Your internal network would be on a private IP range, anything else would go through the public IP address on your router. The router itself will determine whether traffic sent to it needs to be forwarded or not.

i.e. anything sent to the local range would only go there and nowhere else

---

### Post by ergosteur on 2008-10-21
I'm also looking for a way to do this.
In Windows, there's a handy little program called ForceBindIP that accomplishes this: [http://www.r1ch.net/stuff/forcebindip/](http://www.r1ch.net/stuff/forcebindip/).

I've got 2 NICs on the same subnet (10.10.50.xxx), and my net admin has implemented a 512kbps cap for each unique MAC address. I want to have for example all bittorrent traffic on eth1 and everything else on eth0, so as to allow my downloads to run without affecting my web browsing speed.

The only thing I've found so far that works is running a SOCKS proxy bound to eth1's IP and setting the bittorrent client to use the proxy for peer and tracker connections.

---

### Post by pytheas22 on 2008-10-21
You can use the 'route' command to direct certain types of traffic (determined by destination IP or port) over certain interfaces.  I don't know the syntax, but you could look it up.  Basically you'd want to write a rule that says something like 'all traffic on bittorent port goes over eth0; all other traffic goes over eth1'.

---

