---
title: "pretty urgent Help!! An unusual problem with connecting to internet by network card"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by Kaykha on 2008-10-15
hi all sirs
Im newbe in ubuntu linux
I installed 8.04.1 last night and i have some problem with it
the most important of them is that i cant connect to internet via my network card although os found it and it is active on the notification area.. when i operate "sudo pppoeconfig" it search for interface then says Access concentrator of your provider did not respond..

see picture:
[IMG]http://i33.tinypic.com/2yozths.jpg[/IMG]

but when i searched hardwares ubuntu knew it
[IMG]http://i36.tinypic.com/taj02x.png[/IMG]

and one time sayed:
[IMG]http://i36.tinypic.com/20af57b.png[/IMG]

and at the network tools when i want to configure network card i receive this error:
[IMG]http://i34.tinypic.com/nwem87.png[/IMG]

see this pic u can see the icon in notification and ubuntu found its hardware but when i want to connect it encounters problem:
[IMG]http://i35.tinypic.com/20qxpiq.png[/IMG]

and another place that shows ubuntu found even my dial up modem is here:
[IMG]http://i34.tinypic.com/2wfjs3n.jpg[/IMG]

and im sure that the network connection is true because i can open the site of university ( my vpn network is in university ) but i cant connect to internet with my user name and password
please help me...

another problem is that ubuntu cant play my sound and video clips but i think it will resolve if internet connection become true what do u think..

im waiter its urgent to me thanks..

---

### Post by ByteJuggler on 2008-10-15
OK I think you're confusing 2 things: 
1) Your network card and whether it's working (connected to the internet at large), and
2) Your VPN connection to your university, that goes via the internet.  

It appears from what you've posted that your internet connection is actually working OK (e.g. your network card is working), but that you're having difficulty connecting to your University VPN. Is that correct?  

If so, what type of VPN does your university use?  (PPTP, IPSEC?)  And, what VPN client/VPN setup have you used on Ubuntu so far?

---

### Post by Kaykha on 2008-10-15
No
Im sure that my network card working 
first i should say i use adsl connection by a dlink modem 
it connects to vpn network of university and i can see university site and its intranet but i cant create a internet connection becasue of the problem in the fisrt picture..
i need to create a vpn connection to become able to connect to internet from university's vpn network..
i hope i could say my meanning..
thanks

---

### Post by ByteJuggler on 2008-10-15
> **Kaykha said:**
> No
Im sure that my network card working 
first i should say i use adsl connection by a dlink modem 
it connects to vpn network of university and i can see university site and its intranet but i cant create a internet connection becasue of the problem in the fisrt picture..
i need to create a vpn connection to become able to connect to internet from university's vpn network..
i hope i could say my meanning..
thanks

Sorry I'm having difficulty understanding. So you're using an ADSL modem, where does that connect to?   The internet (e.g. via an ISP)?  Or the university directly?

---

### Post by Kaykha on 2008-10-15
ok 
let me to say in another way
when u use a adsl modem when u turn on ur pc and modem you will connect to isp's vpn network instantly then if u want to connect to internet in windows u create new connection to a vpn server and then u become connected to internet by isp..
my isp is university and my pc connects to university network instantly with its turning on but i need to create a vpn connection to connect to internet and i saw in help that i must use pppoeconfig for this..
..

---

### Post by ByteJuggler on 2008-10-15
> **Kaykha said:**
> ok 
let me to say in another way
when u use a adsl modem when u turn on ur pc and modem you will connect to isp's vpn network instantly then if u want to connect to internet in windows u create new connection to a vpn server and then u become connected to internet by isp..
my isp is university and my pc connects to university network instantly with its turning on but i need to create a vpn connection to connect to internet and i saw in help that i must use pppoeconfig for this..
..

OK, I think there's some terminology problems here re "VPN".  When an ADSL modem connects to an ISP, no VPN (Virtual Private Network) is involved.  You should therefore not talk about a VPN in that context yet as it would be incorrect/confusing usage of the term VPN.  Connecting to a VPN is then normally, a seperate issue/step after you've established a connection to the internet.  Connecting to a VPN is also normally exactly the reverse of connecting the (public) internet, and you normally do not connect to the internet via a VPN connection.  Rather, conventionally, one connects to the internet, THEN you connect to a private network (e.g. your university or work network) using a VPN (by using VPN client software and setting up to talk to a VPN server.)

Anyway, it's now not at all clear to me how your connection is actually set up.  Can you please clarify the following:

1) Do you have a DSL modem or a DSL modem/***router***? 
2) E.g. is your DSL Modem connected to you computer's network port, or its USB port?
3) Is your University truly your ISP or is there an ISP in the picture that I'm not aware of?
4) Assuming that your univesity uses some strange VPN setup for access to the public internet, what VPN details have you been given?  (E.g. VPN concentrator address and or type of VPN?)
5) What is the output when you enter the following into a terminal window (might help clarify whats going on):

```
ping www.google.com
```

Are you posting these postings from your Ubuntu?  (I take it not?)

---

### Post by Kaykha on 2008-10-15
Its may be you are right..
In windows i have a local area connection via network card
which enable me too use university sites
..
and then when i want to connect to internet i create a new vpn connection and i enter my user name and pass then i connect to internet..
answer of ur qs:
1) I have wireless adsl 2 + router modem which has network nodes and a wireless antena..
2) Network Port
3)Only university

pinging has no resaults because im not connected to internet..
no Im using windows

.................
and what about u 
what do u use for connecting to internet pptp connection and how do u connect to internet explain please
thanks

---

### Post by ByteJuggler on 2008-10-15
OK I understand better I think.  It's an interesting setup, obviously your university has a private network which is accessed with DSL router, and they've set up a VPN concentrator/router for public internet access.  It's rather unusual but obviously possible. 

Anyway, to answer your question:  I have a DSL modem/router with wireless access point.  The router part has 4 network ports, a phone line socket, and as mentioned the wireless antennas.  The DSL modem connects to the my Internet Service Provider and uses the PPPOA protocol (directly configured on the router, no PC involvement) to establish a n effective direct TCP/IP link to the internet.  I configure my ISP username and password credentials on the router and it connects and manages the lower level DSL connection as well as the TCP/IP pipe (PPPOA) to the internet.  We have a wireless laptop that then connects to the router, it is given a private IP address via the router (via DHCP) and can then freely access the internet.  I also have a desktop that's wired into one of the ehternet network sockets that is also given an IP address via the router (via DHCP) and that can freely access the internet.  

Apart from that, I sometimes connect to my workplace's network via the internet.  For this purpose I have a VPN connection defined on Windows using Windows built in networking, which is a PPTP connection.  Alternatively I also have the Cisco VPN client software installed which supports making an IPSEC VPN connection.  From Linux however, I cannot use the Linux PPTP client -- for some reason there's some sort of compatibility between the VPN concentrator at my workplace and the PPTP VPN client on Linux, so I'm forced to use "vpnc" which can be used to establish an IPSEC VPN connection.  (As an aside, IPSEC is actually more secure than PPTP so its probably just as well.)

Your video and sound codec problems are probably solvable by installing the appropriate packages, which will be possible once your internet connection is sorted out.

Anyway, hope that helps.

---

