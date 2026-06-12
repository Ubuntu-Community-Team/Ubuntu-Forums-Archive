---
title: "Shared Windows Connection"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by adelgado on 2006-12-18
There are two PCs in my house, mine and my parents'. 

Their PC uses Windows XP and has a connection to the internet, and my PC dual-boots between Windows XP and Ubuntu 6.06.1 LTS (I believe it is the "Dapper"). The two PCs are in a network.
When in Windows XP, I can connect to the Internet with the connection on their PC, wich is shared. With Ubuntu I also can, since I've mapped the host with Samba. The connection is auto-setted by Ubuntu, I believe, since I didn't actually configured anything of the connection itself.

The problem is that when the connection to the internet on the other computer is down, in Windows XP I can activate it, but in Ubuntu I can't, basicaly because I don't know how to do it. Where does Ubuntu lists the connections? How can I activate it? 

I've doen some research in the Forum and some Googling but I didn't find anything wich leaded me to solve the problem.

I already appreciate your helping, thanks...

---

### Post by adelgado on 2006-12-19
Up!

---

### Post by adelgado on 2006-12-23
Up!

---

### Post by jimcooncat on 2006-12-23
Please describe your setup a little more.

How are you connecting to the Internet? With dialup from the Windows box?

Or do you have a separate "modem" (cable, dsl) with an ethernet connection? If so, how do the wires go?

---

### Post by dbott67 on 2006-12-23
What kind of internet connection do you have?  Cable? DSL? Dialup?

Can you also describe how the computers are connected together (router, switch, hub)?

How is the internet connection shared (Windows ICS, router)?

Thanks,
Dave

DOH!!!! Too slow typing!!!  What jimcooncat said! :)

---

### Post by adelgado on 2006-12-24
The Windows box connects itself with a DSL (or would it be ADSL?) connection. o be more precise, the Windows box states "Miniporta WAN em PPPoE"; the Ubuntu doesn't states anyhing since I can't connect with it...

The Windows box is hooked up with the Ubuntu/Windows via a RJ45 cable. (By the way, is this Ethernet? Ethernet = RJ45?)

The connection is shared via an option on the Connection's properties window: it's a checkbox "Permitir que outros usuários da rede se conectem por essa conexão à Internet" wich means somethig as "Allow other users of the network to use this conection to connect o the Internet". Is this "Windows ICS"? (I'm assuming it is since I'm asuming that ICS stands for Internet Connection Sharing or something like that).

The wires go:

Modem <===USB===> Windows box <===RJ45===> Ubuntu/Windows Box

Just making it clearer: I CAN use the shared connection with Ubuntu, I just can't connect it if it is down, I have to go on Windows XP, connectit, restarst ad go o Ubuntu to use it...

Many thanks for the help!

---

### Post by adelgado on 2006-12-25
Up!

---

### Post by dorcssa on 2006-12-25
Why don't you get a router?

---

### Post by adelgado on 2006-12-25
> **dorcssa said:**
> Why don't you get a router?

Well, it isn't my call, because I manage only my computer and my pieces of hardware, but the network management is made by some random guy wich work for my mother...

I think that some time ago, we configured the modem as a router so that we wouldn't need the second computer to be turned on for me to access the Internet from my box, but the network was necessary to share the printer...

I think that some time we even considered purchasing a hub, but it was too expensive, even the little ones.

And the network itself isn't the problem, it does work with Windows... In terms of networking, everthing wokrs fine - with Windows... I just don't know how to connect with Ubuntu...

Thanks a lot!

---

### Post by jimcooncat on 2006-12-25
I'm guessing that whatever you do to the Windows side to get a direct connection to the router needs to be duplicated on your Ubuntu side.

Maybe if you could describe the steps you go through to get a direct connection on your Windows side, we could give you some steps you could take with Ubuntu to get the same effect.

Happy Holidays.

---

### Post by jimcooncat on 2006-12-25
Yes, ICS - Internet Connection Sharing, is what the Windows box has. That's why you're able to connect to the internet when that box is gone. 

Somehow you're still tunnelling through that box when it's off -- when you're on your Windows side.

It must still be providing some kind of service between the ethernet (that's your RJ45 jacks and wires) to the USB connection. 

So you may have to describe for us some very detailed information as to how your Windows side connects through the other Windows computer to the USB connection.

I'm guessing that you make a PPPoE connection straight through to your ISP using a username and password -- but that's just a guess. If I'm right we can probably figure how to do that.

So post everything you can see describing that connection, whether you understand it or not. We may be able to help.

I'm sorry we've been so slow to respond.

---

### Post by jimcooncat on 2006-12-25
[IMG]http://fhctech.org/fhc/networking/images/ics-onfig.gif[/IMG]

You should be able to find a dialog like this on your Windows side, with Control Panel. What would be interesting is knowing what network components are shown here.

Also if you can click the TCP/IP entries, then click the "Properties" button, and describe what that screen shows.

It'll probably be a lot of info for you to gather, but it's the only way I know of to be able to get you some help.

---

### Post by adelgado on 2006-12-25
**When the Internet is up:** 
_Windows side:_
Don't do anyhing, the gateway etablishes itself by its own. I can see both the "Conexão Local" and the "Velox em Simone" going to "My Computer > Conrol Panel > Network Connections".
 
"Velox" is the name of the connection to the internet.
"Smone" is the name of the computer wich connects o the internet.
"Conexão Local" is the Windows network between my computer and Simone.
 
_Ubuntu side:_
Don't do anyhing, the gateway etablishes itself by its own. I can't see any of the connections, because I don't know if Ubuntu has a place for listing all the connections, and if it has, I don't know where it is...
 
**When the Internet is down:**
_Windows side:_
Go to "My Computer > Control Panel > Network Connections"
Right-Click on "Velox em Simone" and chose the option "Connect".
 
_Ubutnu side:_
Reboot, go to Windows, and do the "Windows side" procedures; then reboot, and go back to Ubuntu, and the connection is up...
 
 
I believe this will help! 
Any more questions, I'd be glad to answer.
Thanks alot!
 
Merry Christmas!

---

### Post by jimcooncat on 2006-12-26
I've no experience with this, so maybe *someone else with experience* out there can give us some help, too.

Am I right that Simone is powered down? Or just is not connected to the internet?

**If Simone is powered down.**

In trying to figure out how your Windows side gets the connection going with the ICS computer powered down, I can only guess that it's sending a Wake-On-LAN signal to power it up. But that's a guess, and I'm not finding any documentation to support this theory.

If it is working that way, you can download a tool for Ubuntu that can wake it up. You have to have the Universe repository enabled for this one. Install "etherwake" from Synaptic, or from the command line:
```
sudo apt-get install etherwake
```

You can then try to wake up Simone using the "broadcast address".

```
ether-wake -b
```

Or maybe you'd have luck with

```
ether-wake simone
```

If that doesn't work, then you need to find out the IP address of Simone. I'm sorry, but I can't figure how how at this moment. Once you have it though, you can try (with Simone off)

```
ether-wake *Simone's IP Address*
```

like

```
ether-wake *192.168.0.1*
```

**If Simone is powered up, but not connected to the internet.**

*Help from others, please!*

Perhaps your Ubuntu needs to be setup to get it's IP address with DHCP?

---

### Post by adelgado on 2006-12-26
No, no... **Alessandro (My Box) cannot connect to the Internet when Simone is down!**
Neither on the Ubuntu side nor on the Windows side.

When I mean "dowm connection", I'm talking about the nternet connection on Simone, wich is called "Velox", not about the connection from Alessandro to Simone, with is called "Conexão Local".

_If he Simone box is turned off, I can't connect to the Internet,_ but that's ok...

What I mean is that when Simone is powered up, but Velox at Simone is not up, I can't connect Velox when in Ubuntu; when in Windows I just go Conrol panel > Network Conenctions, and I connect "Velox em Simone".

By the way, the connectio is set by DHCP, and Simone's IP is always 192.168.0.1 .

What I want to learn is how o connect Velox, wich is a connection at Simone, and Veox is shared through the Ethernet connection, by a direct RJ45 cable between Alessandro and Simone. 

Thanks for the help!

---

### Post by jimcooncat on 2006-12-26
Well then. It seems to me that you would, on your Ubuntu computer, do something to jump Simone into action. Like try to open a web page. Simone would get your request, and attempt to make an internet connection.

Now your first request won't go. That's because your web browser won't get an answer from the internet in the expected timeframe. But after Simone has had a chance to connect to the internet, then everything should work OK.

I'd like to know how that works for you, but I'm afraid I'm out of answers if that doesn't work.

---

### Post by adelgado on 2007-02-05
I'll try this as soon as I get home, but sincei'm updating to Edgy right now, things my changes...

Thanks for the help, and sorry for late-answering: I had traveled...

---

### Post by adelgado on 2007-03-04
OK... Time has passed, and wanting to see Beryl with my own eyes I've upgraded to 6.10... The upgrade screwed up my system, and, I didn't enjoyed Beryl. But I was able to enter the Internet with 6.10...

So I've formated and reinstaled 6.06. Since I remembered that Firefox didn't had a Flah plugin for 64b version yet, I instaled the 32b version. And, to my surprise, the Internet stopped majorly. Not only I wasn't able to connect the connection, but I wasn't able to Samba the share on the other computer, nor was I able to use the already-active Internet connection . I was completly stucked. So I reinstalled the 64b version, wich I believed would solve the problem. It didn't.

So I reinstalled one more time, because I though that maybe I should install with the Internet connection active, maybe the Ubuntu installer would pick up and understand... Well, it haven't...

So, now I'm completly stucked without any kind of network connectivity on the Ubuntu side, wven with the Windows side working properly.




When I look in the "Network connections" window in Ubuntu I get that the loopback inerface "lo" is configured with both IPv4 and IPv6; but the ethernet connection "eth0" has only IPv6 configured in it; well, at least it is the only thing shown. But my network is IPv4, since this is the only protocol XP works with. I believe this is the problem, but I'm not sure.


Thanks in advance for any help!

---

### Post by adelgado on 2007-03-05
Up!

---

### Post by adelgado on 2007-03-07
As requester earlier by **jimcooncat**, here go some screenshots of the Windows side. If needed, I can post some of the Ubuntu side also...

[ATTACH]26831[/ATTACH]
This is the screenshot of the "Network Connections" window, in the "Control Panel". "Casa" is the Ethernet connection between me and SIMONE, and Velox is the shared Internet connection in SIMONE.

[ATTACH]26833[/ATTACH]
This is the screenshot of "Casa"'s properties. I've edited so that all the protocols fit in. It sais:
"Microsoft network client"
"Virtual machine Network Services" (It is used by the Microsoft VM, nothing to do with the external network)
"File and printers sharing for networks"
"QoS packets 'agendador'" I don't quite know what 'agendador' means in this context, but the only thing I can think of is "scheduler"; does it makes sense?
"TCP/IP Protocol"

[ATTACH]26834[/ATTACH]
This is the screenshot of when I select the item "TCP/IP Protocol" and click in "Properties". The selected options are "Obtain an IP address automaticly" and "Obtain the address of the DNS servers"

[ATTACH]26832[/ATTACH]
And, last but not least: the window on the left is "Status of Casa". It sais:
"Kind of address: Atributed by DHCP"
"IP Address: 192.168.0.87" (This address changes sometimes, I think everytime I restart or so, but it also keeps the '192.168.0' beginning, I think it's standart, not sure...)
"Subnet mask: 255.255.255.0"
"Default Gateway: 192.168.0.1"
The text below sais "Windows hasn't detected any problems with this connection. If you cannot connect, click Repair"

The window on the right is what happens when I click in "Detalhes" (Details). It sais:
"Physical address: <The MAC address>"
"IP address: 192.168.0.87"
"Subnet mask: 255.255.255.0"
"Default Gateway: 192.168.0.1"
"DHCP Server: 192.168.0.1"
"Lease Obtained: <Time stamp>"
"Lease Expires: <Time stamp>"
"DNS Server: 192.168.0.1"
"WINS Server: <Empty>"

OK, I guess it's just that. Many thanks in advance!

---

### Post by adelgado on 2007-03-08
Up!

---

### Post by adelgado on 2007-03-09
Up!

---

### Post by adelgado on 2007-03-09
Up!

---

### Post by adelgado on 2007-03-10
Up! Last bit of information's on page 2, post 18...

After some googling and some file looking I've reached the conclusion that the problem is that Ubuntu tries to etablish an IPv6 connection to Simone, but Simone only understands IPv4...

Thanks for the help...

---

### Post by adelgado on 2007-03-11
Up!

---

### Post by adelgado on 2007-03-12
Up!
Come cn, guys, I'm not asking anything tough, I just wanna kno how to connect two computers over a network... We can deal with the Internets problems later...

Thanks a lot in advance...

---

### Post by adelgado on 2007-03-13
Up!

---

### Post by adelgado on 2007-03-15
Up!

---

