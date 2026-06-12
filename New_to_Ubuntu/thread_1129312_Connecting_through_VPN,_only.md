---
title: "Connecting through VPN, only"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-04-18
Would it be possible to set up ubuntu so it's only possible to connect to the Internet using VPN connection, in other word's if you not connecting using the VPN wont you be able to connect to the Internet. The reason I wonder is that you from time to time might lose your VPN connection and become completely unprotected.

---

### Post by The Cog on 2009-04-18
No. I think you misunderstand what a VPN is. A VPN is just a connection - a tunnel - between two computers done by encrypting the packets sent between them. The encryption is what makes the connection "private". The VPN connecton can be used to carry traffic between LANs that those computers are connected to, providing a connection between two company offices for instance. 

Given this description, two things are necessary. Firstly, you need two computers cooperating - you need somewhere else to talk to. Secondly, the computers at the tunnel ends need internet access on order to be able to send those encrypted packets to each other.

I get the impression that you think a VPN will somehow protect you while talking to the internet. I hope you see now that's not quite the case.

---

### Post by SpinningAround on 2009-04-18
> **The Cog said:**
> No. I think you misunderstand what a VPN is. A VPN is just a connection - a tunnel - between two computers done by encrypting the packets sent between them. The encryption is what makes the connection "private". The VPN connecton can be used to carry traffic between LANs that those computers are connected to, providing a connection between two company offices for instance. 

Given this description, two things are necessary. Firstly, you need two computers cooperating - you need somewhere else to talk to. Secondly, the computers at the tunnel ends need internet access on order to be able to send those encrypted packets to each other.

I get the impression that you think a VPN will somehow protect you while talking to the internet. I hope you see now that's not quite the case.
I might have missunderstod some parts or simply didn't express myself good enough.

A = my computer
C =  VPN
B = 'target computer/server'
As you are saying will I only connect through a VPN, instead of connection from A --> B will I instead connect from A --> C (VPN) --> B atlest that is how I understand it.

What I'm looking for (might be impossible because of the nature of VPN) is as follow. I'm using VPN to connect so I'm anonymous for computer B since it only see computer C (VPN), what I'm worried about is that for some reason will I lose the connection to computer C (VPN). This will (I guess) result in my computer A connection to computer B without going through the VPN. Because of the lost connection to the VPN will I get A --> B instead of A --> C --> B

My question was if it would be possible to to create a stop for the Internet connection if it didn't connect through or using the VPN. So if I didn't have the VPN would my computer not be able to connect to B. 

Did it become any clearer? :confused:

EDIT:
I might be completly wrong but isn't this site a VPN?
[http://ivacy.com/](http://ivacy.com/)

---

### Post by Marko723 on 2009-04-18
> **SpinningAround said:**
>  

I might be completly wrong but isn't this site a VPN?
[http://ivacy.com/](http://ivacy.com/)

A VPN is an encrypted tunnel between two devices.  Essentially what you're trying to do is block all out going ports from your computer except this secure channel.  If you place a firewall between your computer an the Internet this is easily achieved by only allowing your VPN port with an outbound rule and dropping all other protocols.  

A web site is not a VPN, but it can establish a VPN connection between itself and you if everything is configured correctly.

Mark

Edit:

But if you place a firewall between your computer an the Internet, you need not worry about being insecure.  By default most firewalls allow all out bound requests straight out of the box,and block all incoming traffic unless initiated by an outbound request.  

I took an old pII computer a couple years back and set up a IPCOP firewall (Linux based).  Best thing I did dropping my netgear home firewall.  I still keep it around for emergency, in case my P2 has a HW failure.

---

### Post by SpinningAround on 2009-04-18
> **Marko723 said:**
> A VPN is an encrypted tunnel between two devices.  Essentially what you're trying to do is block all out going ports from your computer except this secure channel.  If you place a firewall between your computer an the Internet this is easily achieved by only allowing your VPN port with an outbound rule and dropping all other protocols.  

A web site is not a VPN, but it can establish a VPN connection between itself and you if everything is configured correctly.

Mark

Edit:

But if you place a firewall between your computer an the Internet, you need not worry about being insecure.  By default most firewalls allow all out bound requests straight out of the box,and block all incoming traffic unless initiated by an outbound request.  

I took an old pII computer a couple years back and set up a IPCOP firewall (Linux based).  Best thing I did dropping my netgear home firewall.  I still keep it around for emergency, in case my P2 has a HW failure.

Thanks :) will only keep port 1723 (pptp) open then.

Since I'm a newbie, will I still be able to use Http/Https/ftp/ssl and all those even if there ports are blocked by my computer, will they somehow be able to connet through port 1723?

---

### Post by Marko723 on 2009-04-18
> **SpinningAround said:**
> Thanks :) will only keep port 1723 (pptp) open then.

Since I'm a newbie, will I still be able to use Http/Https/ftp/ssl and all those even if there ports are blocked by my computer, will they somehow be able to connet through port 1723?

No, not unless you figure out a way to port forward your requests.  Trying to achieve what you are talking about on a single box (with out any virtual machines) is going to take some creativity, and I'm not even sure it's possible.

I'd suggest you place either a appliance firewall (such as netgear or linksys) in between your computer(s) and the Internet.  You also might have luck picking up a really old computer cheap or even free, and install a Linux firewall on it.  Keep in mind you will require 2 NIC cards in the firewall box.

Others will correct me if I'm wrong, but if you start disabling ports, essentially they don't exist. So you will be breaking HTTP, SSL and all the rest.  The function of the VPN client software is to capture all protocols and tunnel them through the encrypted connection.  If you block these ports, there's nothing for the tunnel to capture.

My UNIX is pretty rusty, it was many many years ago since I spend any significant time on a machine.  I just purchased some new hardware to replace one of my older computers, as a result I've decided to retire one of my Windoze boxes and go with Ubuntu.  I'm just waiting for 9.04 to be released an I plan on installing it on this new machine.

---

### Post by The Cog on 2009-04-19
Depends if you block outgoing connections to port 80 etc, or block incoming connections to port 80 etc.

Blocking outgoing connections to port 80 etc. will prevent you connecting to those ports on the internet. It will stop your web surfing and all that stuff. 

Blocking incoming connections to port 80 etc. will stop other people from connecting to your webserver, https webserver, and all the other servers you have installed. 

If you haven't installed any such servers, then you don't need a firewall at all. If you have installed a server such as a web server, and you want the whole world to be able to connect to it then again, you have no use for a firewall. You can only make use of a firewall if you have installed a server of some sort, and you want to control which IP addresses can connect to it. I suspect that in your case you haven't installed any servers and so don't need a firewall. Making outgoing VPN connections doesn't constitute running a server - unless it also accepts incoming connections.

Connections made across the VPN would not be affected by any firewall rules - they go inside the VPN tunnel and the only thing the firewall would see is the VPN traffic (on port 1723 for instance). If you do decide to block everything else, don't forget that without DNS on UDP port 53 you won't be able to resolve names to IP addresses.

---

