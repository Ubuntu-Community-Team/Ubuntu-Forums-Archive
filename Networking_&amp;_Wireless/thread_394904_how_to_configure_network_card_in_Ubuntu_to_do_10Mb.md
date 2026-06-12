---
title: "how to configure network card in Ubuntu to do 10Mbps/Full Duplex?"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by F for Fragging on 2007-03-27
I had some problems getting my network connection to work. The helpdesk for my internet service provider unfortunately doesn't support Linux, so I was forced to install Windows XP again to get support from their helpdesk.

The problem is that something is wrong with the cabling of my ISP. After consulting the helpdesk, I was told that the solution for this is to configure my network card at **10Mbps/Full Duplex** instead of using the default setting **Auto Negotiation**. This solution works for me, and without doing so my network connection won't work.

This can be done in Windows XP by going to the Control Center -> Network- and Internet-connections -> Network Connections -> right click LAN-connection -> Properties -> Configure... -> Advanced -> Link Speed/Duplex Mode -> change the value from Auto Negotation to 10Mbps/Full Duplex here (not sure if I'm using the correct terms which are actually used in an English version of Windows XP, I'm using a Dutch version so I had to translate).

So currently I can only use my network connection with Windows XP installed on my notebook. Naturally I'm missing Ubuntu badly, so I want to install that and wipe Windows XP from my hard disk. However, of course I want to be able to use my network connection under Linux.

So my question is, does anybody know how to configure my network card on Ubuntu to do 10Mbps/Full Duplex?

---

### Post by Mr. C. on 2007-03-27
```
man ethtool
man mii-tool
```

MrC

---

### Post by netztier on 2007-03-27
> **F for Fragging said:**
> The helpdesk for my internet service provider unfortunately doesn't support Linux, so I was forced to install Windows XP again to get support from their helpdesk. 

<RANT>
Get another ISP. A real ISP provides TCP/IP connectivity and adheres to standards by IEEE and IETF. That's what their business should be. "not supporting Linux" is AOLing and lame.
</RANT>

Sorry, please don't take it as a personal attack to you. Can't help it, I alway set off on things like that.

> **F for Fragging said:**
> 
After consulting the helpdesk, I was told that the solution for this is to configure my network card at **10Mbps/Full Duplex** instead of using the default setting **Auto Negotiation**. This solution works for me, and without doing so my network connection won't work. 

Yet another reason to dump that ISP (again, sorry... of course I know that it isn't *that* easy). The only place where I ever saw the real need to force 10Mbps FDX ist with the Ethernet-over-SDH service we get from Colt Telecom or Verizon at my employer's. Anywhere else I ever saw someone wanting to use 10Mbps FDX, his network had a big "in deep trouble" sticker on it. The thing with FDX on 10Mbps FDX is this: It's a very uncommon ethernet mode, and you might so easily run into trouble because there is a lot of (old) hardware out there that will have a hard time supporting it. 

Ask the helpdesk if their end of the link is also configured for 10Mbps FDX. If it isn't then ask why you should configure 10Mbps FDX on *your* end of the cable, since configuring only one end of the link can (an most of the time does) easily result in a duplex mismatch.

Another indication that something is wrong might be this: If the length of the (Cat5) cabling is beyond the limit (100m), downgrading the speed form 100 to 10Mbps can help to get reliable service. We've seen it go 130m and more with 10mbps where 100Mbps already failed. "Something wrong with the cabling" sounds very much like that. 

> **F for Fragging said:**
> So my question is, does anybody know how to configure my network card on Ubuntu to do 10Mbps/Full Duplex?

MrC pointed you to **ethtool** and **miitool**. Some ethernet driver modules also accept parameters upon loading that will let you set duplex and speed modes. Check witch **lspci** and **lsmod** which ethernet driver is loaded for the NIC in your system, and then with **modinfo <module name>** if and which parameters it accepts.

best regards

Marc

---

### Post by F for Fragging on 2007-03-29
Mr. C and netztier, thank you very much. *sudo mii-tool -F 10baseT-FD* fixed my problem.

Netztier: it's not so that their helpdesk refuses to support Linux explicitly, I just assumed so since their guides for setting up a connection only take Windows into account. I don't see it as a problem, I can figure out things by myself mostly anyway. I don't know how supportive your ISP is, but would you really expect a helpdesk employee to inform me about how I should have fixed it with ethtool or mii-tool? I certainly don't take your opinion as a personal attack.

My current provider certainly isn't that great, but they do offer 10Mbps connections for 4,50 Euro. And for students it's free. For comparison, at my parents' place I use a 2Mbps ADSL connection which is 40 Euro a month. Besides that, my housing corporation made a deal with this provider for providing the connectivity, so it's pretty much take it or leave it for me. But so far I think their service is reasonable, except for having to force 10Mbps/FD (it took me and their helpdesk quite some time to figure out that was the problem preventing me from getting any connection at all). Today I gave the helpdesk a call and they said that's necessary because of a problem in their switch, apparently they configured their switch that way because it's more reliable or something, didn't get the whole story. They said they intend to fix their switch.

---

### Post by didijeeeke on 2007-03-29
> **F for Fragging said:**
> Mr. C and netztier, thank you very much. *sudo mii-tool -F 10baseT-FD* fixed my problem.

Netztier: it's not so that their helpdesk refuses to support Linux explicitly, I just assumed so since their guides for setting up a connection only take Windows into account. I don't see it as a problem, I can figure out things by myself mostly anyway. I don't know how supportive your ISP is, but would you really expect a helpdesk employee to inform me about how I should have fixed it with ethtool or mii-tool? I certainly don't take your opinion as a personal attack.

My current provider certainly isn't that great, but they do offer 10Mbps connections for 4,50 Euro. And for students it's free. For comparison, at my parents' place I use a 2Mbps ADSL connection which is 40 Euro a month. Besides that, my housing corporation made a deal with this provider for providing the connectivity, so it's pretty much take it or leave it for me. But so far I think their service is reasonable, except for having to force 10Mbps/FD (it took me and their helpdesk quite some time to figure out that was the problem preventing me from getting any connection at all). Today I gave the helpdesk a call and they said that's necessary because of a problem in their switch, apparently they configured their switch that way because it's more reliable or something, didn't get the whole story. They said they intend to fix their switch.
Very nice here in Belgium i pay 35 € for a 6mbps down connection !!!

---

### Post by Mr. C. on 2007-03-29
> **F for Fragging said:**
> Mr. C and netztier, thank you very much. *sudo mii-tool -F 10baseT-FD* fixed my problem.

You're welcome.

As you've noticed, most first-tier techs essentially have scripts they go through for problem resolution.  As soon as your problem forks from the script, the respond with the "we don't support ...".

Glad it's all working out,
MrC

---

