---
title: "Routing wireless to wired"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Malalo on 2009-03-26
Hi guys,

Let me put you in situation first :
1 Windows PC, 2 Ubuntu, 1 XboX 360. All computers have wired and wireless interfaces. The XboX only has wired.
I have 1 Wired D-Link router, 1 Airport Express Wireless.

Everything connected to the internet through the D-Link, wired, when suddenly the D-Link's power stopped working. So I decided to switch to wireless. Now all computers connect to the internet with the wireless connection.

I tried sharing internet on the Windows PC and then connect the XboX to it. Internet sharing on Windows is a real pain in the you_know_what. 

My question is : if I connect the XboX to a Ubuntu's wired interface, how can I route the wireless internet connection ? I'm guessing it has something to do with adding a route or something but I'm really stumped...

---

### Post by cariboo on 2009-03-26
Have a look at this [howto]("http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html") it should do what you need.

Jim

---

### Post by perrti-y02 on 2009-03-26
The simplest way to do this is using a program called firestarter. It is in fact a firewall but it allows you to share an Internet connection and is very easy to set up.

Install it through synaptic then when you run it for the first time follow the Wizard that comes up.
The first screen asks for where the internet comes in (probably wlan0)
THe second asks where is it going out from (probably eth0). Say no to DHCP.

You will then need to tell the xbox and ethernet card their IP addresses and subnet mask and such like. The Xbox will also ask for name servers and default route.

I would say that you should make the Xbox's IP 192.168.2.101 subnet 255.255.255.0 and broadcast address 192.168.2.100.
The ethernet card should be 192.168.2.100 subnet 255.255.255.0 and broadcast address should be whatever is the IP of the wireless card.

Name servers for both can be found in the information for your wireless network in the Network Manager applet in the system tray.

Hope that helps and makes sense

---

### Post by Malalo on 2009-03-26
Both of you helped very much.
I shall try this at home tonight !

One question to perrti : when you say "broadcast", do you mean "gateway" ?

---

### Post by perrti-y02 on 2009-03-26
Yes. It has different names on different places. On my installation asked me for a broadcast address. On NM it asks for a gateway.

---

### Post by Malalo on 2009-03-27
Allright, it worked with Firestarter.
Only thing now, but it's not really a problem, is that my XboX states that my NAT is "Moderate", and it needs an "Open" NAT for a better online gaming experience.
I ignored the message since I wanted to connect primarily for updates, but if any of you have any suggestions as to how I could "open" the NAT, it'd be appreciated.
Thanks again for your help !

---

### Post by blastus on 2009-03-27
> **Malalo said:**
> Hi guys,

Let me put you in situation first :
1 Windows PC, 2 Ubuntu, 1 XboX 360. All computers have wired and wireless interfaces. The XboX only has wired.
I have 1 Wired D-Link router, 1 Airport Express Wireless.

Everything connected to the internet through the D-Link, wired, when suddenly the D-Link's power stopped working. So I decided to switch to wireless. Now all computers connect to the internet with the wireless connection.

I tried sharing internet on the Windows PC and then connect the XboX to it. Internet sharing on Windows is a real pain in the you_know_what. 

My question is : if I connect the XboX to a Ubuntu's wired interface, how can I route the wireless internet connection ? I'm guessing it has something to do with adding a route or something but I'm really stumped...

You'd be better off getting a router (like WRT-310N), flashing it with DD-WRT, and setting up a [wireless bridge](http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge). Then you can plug in your XBox or ANY computer into the router and it would be instantly on your network. Or you could plug both your XBox and Ubuntu machines into the bridged router (technically the term is "client bridge") and then you don't have to mess with wireless in Ubuntu. 

And once it is setup you never have to setup it up again which makes it easier to reinstall Ubuntu for example--no wireless configuration or connection sharing setup would be necessary anymore.

---

### Post by Malalo on 2009-03-27
> **blastus said:**
> You'd be better off getting a router (like WRT-310N), flashing it with DD-WRT, and setting up a [wireless bridge](http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge). Then you can plug in your XBox or ANY computer into the router and it would be instantly on your network. Or you could plug both your XBox and Ubuntu machines into the bridged router (technically the term is "client bridge") and then you don't have to mess with wireless in Ubuntu. 

And once it is setup you never have to setup it up again which makes it easier to reinstall Ubuntu for example--no wireless configuration or connection sharing setup would be necessary anymore.

Thank you for this information. However, I just setup the NAT on one of my Ubuntu computers and it cost 0$. Your WRT-310N is sold around 100$. That's 100$ that's still in my pocket :P

---

