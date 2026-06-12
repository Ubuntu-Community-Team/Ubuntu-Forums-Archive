---
title: "[SOLVED] Firefox can't browse web"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by markzimmerly on 2008-12-04
I've been using Ubuntu 6.10 for a few years but am still a complete beginner.  Recently I changed internet providers and now firefox generally can't browse the web even though my Windows Vista laptop can.  For some reason it worked a couple times a month or so ago but hasn't since.  I am still able to install Ubuntu updates and the network looks connected (via ethernet cable), but still no browsing.  I am using an Actiontec modem with DSL.  "Browse Offline" is NOT checked.  

ifconfig returns the following:

eth0     Link encap:Ethernet  HWaddr 00:D):B7:7D:D8:91
         inet addr:  192.168.0.6  Bcast:192.168.0.255  Mask:  255.255.255.0
inet6 addr:  fe80::2d):b7ff:f37d:d891/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:  250 errors:0 dropped: 0 overruns:0 frame:0
TX packets 331 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:42017 (41.0 kiB)  TX bytes:38376 (37.4 KiB)

lo     Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU: 16436 Metric:1
RX packets: 1673 errors:0 dropped:0 overruns:0 frame:0
TX packets: 1673 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes: 145776 (142.3 KiB) TX bytes: 145776 (142.3 KiB)

Any thoughts?

---

### Post by Wickd on 2008-12-04
Open a terminal (Applications --> Accesories --> Terminal) and type the following:

www-browser [www.google.co.za](www.google.co.za)

Does it browse to a web page?

---

### Post by markzimmerly on 2008-12-04
No progress with that command.  It says "Opening socket. . ." but then "can't load [www.google.co.za](www.google.co.za).

---

### Post by Michael.Godawski on 2008-12-04
So you say you are connected to the internet. You can update your machine and stuff like 
```
sudo apt-get update
```is working.

Have you tried out another web-browser, so we can be sure the problem lies on the side of Firefox?

---

### Post by markzimmerly on 2008-12-04
The above command works fine so I'm pretty sure I'm connected to the internet, but the Epiphany Web Browser also fails to browse, so I'm thinking it may be a setting on my modem, but I don't understand what needs to change or how to change it.

---

### Post by Michael.Godawski on 2008-12-04
Perhaps the old ipv6 story. Try this:


[LIST]
[*][https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)
[/LIST]

If you are still using the 6.06 version:


[LIST=1]
[*]Open a terminal and type: 
```
gksudo gedit /etc/modprobe.d/blacklist
```
[*]Add this line: 
```
blacklist ipv6
```
[*]Save the file and restart your computer
[/LIST]

---

### Post by Malalo on 2008-12-04
Perhaps you already checked, in Firefox :

Edit -> Preferences -> Advanced Tab -> Network Tab -> Settings button (near "Connection") ...
Make sure it says "No proxy"...

---

### Post by markzimmerly on 2008-12-04
I tried both the above suggestions to no avail.  Firefox is set to connect to the internet directly and ipv6 has been blacklisted.  You were right though--I'm running 6.06 "Dapper Drake" (not 6.10!)

---

### Post by Michael.Godawski on 2008-12-04
> I'm running 6.06 "Dapper Drake" (not 6.10!) 	

wow.... I have hidden telekinetic and psychic abilities... actually this was a typo.

---

### Post by annda on 2008-12-04
it looks that probably somewhere along the way you have a problem with the DNS name server. unless you have set a static IP address for your ubuntu machine, you can run a quick check with with the ping command in the terminal:

```
ping 209.85.171.100
```

and CTRL+c after a few seconds to stop connecting. any packet loss? i suppose not, since the internet connection seems to be working. try:

```
ping google.com
```

is it still ok, or do you get an error message about 'host unknown'? if so, please check and post here the output of 
```

cat /etc/resolv.conf
```

if you have new hardware from your new provider, the IP there might need changing.

---

### Post by markzimmerly on 2008-12-04
> **annda said:**
> it looks that probably somewhere along the way you have a problem with the DNS name server. unless you have set a static IP address for your ubuntu machine, you can run a quick check with with the ping command in the terminal:

```
ping 209.85.171.100
```

and CTRL+c after a few seconds to stop connecting. any packet loss? i suppose not, since the internet connection seems to be working. try:

```
ping google.com
```

is it still ok, or do you get an error message about 'host unknown'? if so, please check and post here the output of 
```

cat /etc/resolv.conf
```

if you have new hardware from your new provider, the IP there might need changing.

No packet loss, but it does say "host unknown"--here is the result of cat /etc/resolv.conf  
search domain.actdsltmp
nameserver 192.168.0.1
nameserver 205.171.3.25

I've also noticed that a simple software update request returns an error of "Temporary failure resolving 'security.ubuntu.com'" Is this related?  I'm wondering if a firefox update might solve the problem. . .

---

### Post by newbee70 on 2008-12-04
> **markzimmerly said:**
> No packet loss, but it does say "host unknown"--here is the result of cat /etc/resolv.conf  
search domain.actdsltmp
nameserver 192.168.0.1
nameserver 205.171.3.25

I've also noticed that a simple software update request returns an error of "Temporary failure resolving 'security.ubuntu.com'" Is this related?  I'm wondering if a firefox update might solve the problem. . .

if you right click on your computer connection in the upper right of your upper toolbar and click on the ? mark what info does it give you. 

anything like this?

---

### Post by markzimmerly on 2008-12-04
> **newbee70 said:**
> if you right click on your computer connection in the upper right of your upper toolbar and click on the ? mark what info does it give you. 

anything like this?

Sadly, no--I think you must be running a more recent version of Ubuntu--I have no such icon.

---

### Post by newbee70 on 2008-12-04
> **markzimmerly said:**
> Sadly, no--I think you must be running a more recent version of Ubuntu--I have no such icon.

Sorry your right; I did not see the 6.10, I run 8.04

---

### Post by newbee70 on 2008-12-04
> **newbee70 said:**
> Sorry your right; I did not see the 6.10, I run 8.04

Did you try this " the thumbnail?

or this?

    * System -> Administration -> Networking
    * Network settings 

Connections Tab -> Select "Ethernet connection" -> Activate/Deactivate


or this?

 How to configure network connections

  
    * System -> Administration -> Networking
    * Network settings 

Connections Tab -> Select "Ethernet connection" -> Properties
Connection -> Enable this connection (Checked)
Connection Settings -> Configuration: Select "DHCP/Static IP address" ----SET TO DHCP  and try that.

and if you need to change these you have to get the info from your ISP.

DNS Tab -> DNS Servers -> Add/Delete



By the way this does look wrong.

**inet addr: 192.168.0.6 Bcast:192.168.0.255 Mask: 255.255.255.0 **

192.168.0.1 or 192.168.1.1 maybe. but that is out of my league.

---

### Post by markzimmerly on 2008-12-06
I've been doing some more research hoping that there would be a simple reason why I still can't get to the net, but nothing has worked.  
I confirmed with my ISP that I should be connecting via DHCP, which I am, and I double checked my modem settings and all is as it should be.  
I can ping 192.168.0.1 and google.com with no problems.  
I can do sudo apt-get update 
What I still can't do is browse the internet--in the terminal or in firefox.  
Any idea of what I might have missed?  I'd be grateful for any suggestions whatsoever as I really need to get this computer to work. . .

---

### Post by markzimmerly on 2008-12-08
I finally updated to 8.04LS and that seems to have solved the problem.  Thanks everyone for all your help.

---

