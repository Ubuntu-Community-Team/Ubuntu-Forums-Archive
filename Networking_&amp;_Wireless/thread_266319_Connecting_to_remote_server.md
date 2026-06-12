---
title: "Connecting to remote server"
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by Michiba on 2006-09-27
Hi all,

I would like to connect to my work server from home, I will give some detail and hope some one can point me in the right direction.

Ok work server is as follows :-

Windows Server 2000 set up as a domain running exchange. ADSL broadband connection.

Home:-

7 PC network with a standard HUB, 1 Win XP one Windows Me and the rest Linux, all internet sharing through the XP machine which is directly connected to the cable internet.

Equipment at my disposal- 1 Dlink Broadband router 4 ports and one WAN port.

So how do I do this I want all seven PC's at home to access the internet but the broad band router has 4 ports. Can I uplink connect my home Hub to the router ? and does the Router connect directly to my cable modem. How do I find the work server and do I need something like tight VCN to acces it?

Thanks in advance for your help.
Michiba

---

### Post by mips on 2006-09-27
Who owns the work server ? Is it your business or another company.

First ask permission.
Is the server protected by a firewall etc ? Security is a great concern !!!

The only way I would go is with a secure VPN.

---

### Post by Michiba on 2006-09-27
Hi,

It's a work Server, My business, so no permission problems. Just a question of how to.

Thanks

Michiba

---

### Post by neouser99 on 2006-09-28
First off, might i recommend not using the winxp computer as the gateway, and either use your dlink router or turn one of the linux machines lying around into your router/firewall/dns type server. here is a greating product that will do it for you if you don't want to hassle with a distro setup [http://www.ipcop.org/](http://www.ipcop.org/) | [http://smoothwall.org/](http://smoothwall.org/) | [http://m0n0.ch/wall/](http://m0n0.ch/wall/)

once that is done, you can just use the same hub behind it to have your pc's on your local lan. as mips stated, security is the main thing you have to pay attention to, and some sort of vpn is the best way to do things. i am guessing you don't have a cisco firewall at your work network, but if you do then getting their vpn setup on your windows machine would be the best, otherwise something like [http://hamachi.cc/](http://hamachi.cc/) or [http://openvpn.net/](http://openvpn.net/) would probably work just as well. From there, it is just a matter of remote desktop, windows shares, dns, or whatever it is that you would like to share from your home computers to your office. 

if you really want to get fancy you could setup a ipsec route from your 
firewall to your office, creating a virtual link between the two locations, bypassing the need for vpns or such on all the machines, but this is much more difficult and not the easiest thing to setup, not to mention its probably overkill, but hey, i thought i would throw it out there.

-neo

---

