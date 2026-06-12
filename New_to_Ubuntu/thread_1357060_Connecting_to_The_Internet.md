---
title: "Connecting to The Internet"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by Fernglougher on 2009-12-16
First of all, I am excited to be a new Ubuntu user, but I concerned that I am not yet able to get Ubuntu to the point where it can do useful things.  For instance, I am writing this on the Windows partition of a machine that dual boots a Windows OS and Ubuntu 9.04 because I cannot get Ubuntu to connect to the Internet.  I have noticed that there are a lot of posts in this general category, but was disappointed that was not able to find anything that related to my problem connecting to the Internet.

The Gnome interface seems to provide some programs called Network Tools and Network Connections.  These are Gnome-based user interface tools that I assume are supposed to be helpful to people like me who are just getting started, but unfortunately they were really not that helpful.  For example, in Network Tools, when I clicked on Help, I get to a page that says, "Introduction.  This is only a template to get the documentation done.  It should not be translated."  Another words, a dead end.  In Network connections, there is no help at all (which is probably better than offering help and then disappointing).

The first place I looked was in the Ubuntu Help Center Under Connecting to the Internet, then Wired (LAN) and then to Static Connections, which is how the network that I am connecting to works.  I followed those instructions, but was dismayed to find an instruction that said "Enter your details and click OK."  I took this as a hint that if you had no idea what "your details" meant, you should go back to using Windows.

So, then I went online to the Ubuntu documentation site, clicked on documentation for 9.10 (which is what I have), then Internet, and Wired LAN, and got to the same "enter your details" message.

So, just flying by the seat of the pants, entered 192.168.1.42 (my static IP address), 255.255.255.0, 192.168.1.1 (my gateway) and 208.67.222.222 plus 222.67.220.220 as my IP address, submask, gateway and DNS servers for eth0 and clicked accept -- assuming that's what "your details" meant, but was never able to ping to anything past my router using the Ping tab in Network Tools.

And just for fun, I launched FireFox and typed in "www.ubuntu.com" as well as "www.google.com" and got nowhere fast.

Then I looked at the online documentation under #5, Wired Troubleshooting, and did a ping to ubuntu.com, just as the documentation suggested, but no graph showed up and I got a bunch of zeros.  The documentation says that "Your computer has a very bad connection, or is connected to an access point or router which is not connected to the Internet."  Well, I am not sure what "bad" means, but I am using the same connection now through the same router and the same PC through Windows, so I suspect that the author of the documentation was probably a little short on time and didn't have time to list some of secret reasons that this might be working that only the experts know about.

It quickly became apparent that the Gnome interface and the "tools" it includes were kind of like a movie set:  they appear real to the casual viewer, but are really facades and the only way to get something to work would be to delve into the terminal and grapple with learning enough arcane command-line based tools to get any further.  I think this is also the point where a lot of people decide to go back to Windows or buy an Apple computer.

Anyway, pressing on, the online documentation suggested that I try going into the terminal program and trying ipconfig eth1 and also ipconfig eth0 (which is what I configured in the Network Connections), but I was dismayed to get the succinct response "bash: ipconfig: command not found." 

At that point I realized that I was in a very unhappy place and that I would need to learn a lot more about how Ubuntu and Linux worked then I ever really wanted to as an end user if I was going to get connect my computer to the Internet, even just to open Firefox and browse a Web site.  However, before I ran out and bought as may shares of Microsoft and Apple that I could afford, I figured I would try out this community support thing and see where it got me.  

So, I am sure there are some very knowledgeable people who might think what I am puzzled by is child's play and may even being getting a chuckle that I cannot find the release for the snare that trapped me here, but I could use a few pointers to set me in the right direction again.

Thanks for taking the time to read this.  And if you have any suggestions, I would love to hear them.  Although, it looks like I will have to boot my Windows partition to read them.

---

### Post by marshmallow1304 on 2009-12-16
Does your router not have a DHCP server?

Anyway, if you enter
```
ipconfig /all
```
in the Windows command line (Start->Run, enter 
```
cmd
```
in the box and click OK.) that should give you all the info you need to enter in Ubuntu.


> **Fernglougher said:**
> Anyway, pressing on, the online documentation suggested that I try going into the terminal program and trying ipconfig eth1 and also ipconfig eth0 (which is what I configured in the Network Connections), but I was dismayed to get the succinct response "bash: ipconfig: command not found." 

In Linux, the command you want is
```
ifconfig
```
istead of
```
ipconfig
```

---

### Post by Grey Seal on 2009-12-16
If you are hardwired, unplug and replug.
If wireless you will have to go to the router... and do the same.

---

### Post by 3rdalbum on 2009-12-16
There is an icon on your top panel, toward the right (it should be next to your volume control). Click it. This is the Network Manager. Does it allow you to connect to your network?

If not, then right-click it and choose Edit Connections. Fill in whatever information you need to in here for your wired Ethernet connection. (tip: Use the "IPv4 Settings" tab for now). Click "Apply" to apply your changes. Left-click on the Network Manager again and disconnect from your network, and then go back there and connect again using the connection name that you set (by default it will probably be called Auto eth0).

This should connect.

---

### Post by Fernglougher on 2009-12-16
Thanks to the first three responders.  Here is what happened in each case, unfortunately without much success.

**_marshmallow1304_**

The router is not configured for DHCP.   Address on the LAN must be static and DNS must be supplied.  I use OpenDNS and provide their primary and secondary DNS server addresses:  208.67.222.222 and 208.67.220.220

I was able to use ifconfig from the terminal and it reports the correct IP address. 
It reports successful RX and TX packets with no errors.
However, there is still no connection beyond the router.  
I cannot ping external addresses such as 4.2.2.2

**_Grey Seal_**

I am using a wired connection.   I shut everything down, including my router, unplugged all the cables, waited ten minutes and reconnected everything, starting with the router and worked my way back to the computer.   Unfortunately, I am still unable to connect.


**_3rdalbum_**

I filled in the ip4 connections tab, disconnected, and reconnected.  I can ping the router at 192.168.1.1 successfully, but cannot reach any IP address outside of my network.

---

### Post by k3lt01 on 2009-12-16
> **Fernglougher said:**
> Thanks to the first three responders.  Here is what happened in each case, unfortunately without much success.

**_marshmallow1304_**

The router is not configured for DHCP.   Address on the LAN must be static and DNS must be supplied.  I use OpenDNS and provide their primary and secondary DNS server addresses:  208.67.222.222 and 208.67.220.220

I was able to use ifconfig from the terminal and it reports the correct IP address. 
It reports successful RX and TX packets with no errors.
However, there is still no connection beyond the router.  
I cannot ping external addresses such as 4.2.2.2

**_Grey Seal_**

I am using a wired connection.   I shut everything down, including my router, unplugged all the cables, waited ten minutes and reconnected everything, starting with the router and worked my way back to the computer.   Unfortunately, I am still unable to connect.


**_3rdalbum_**

I filled in the ip4 connections tab, disconnected, and reconnected.  I can ping the router at 192.168.1.1 successfully, but cannot reach any IP address outside of my network.

OK so you have got wired working to a degree, in other words it sees your router but nothing past it. This exact problem hits my machines every 2nd release of Ubuntu, usually the .10 release (i.e. 7.10, 8.10, 9.10). So what do I do about it? I automatically follow [these instructions]("http://ubuntuforums.org/showpost.php?p=3996845&postcount=5") now and get my connection back within minutes.

---

### Post by plainswolf on 2009-12-16
thanks for this thread, I'm having a hell of a time trying to connect to internet after installing dual boot ubuntu, but I really want to use this OS.. will study this some more and try again tomorrow


Plainswolf
(Mark)

---

