---
title: "What does &quot;Trusted LAN&quot; mean?"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by mikodo on 2009-04-28
In response to one of my threads around security in Hardy, this was stated:
 
"For a desktop computer with Ubuntu in a trusted LAN there is no need for all this imho" (ie. Firewall managers, Apparmor, Netfilter etc.)

 I do not know what a "trusted LAN" means? All I have is one computer connected to the modem provided by my Internet Provider using just a wired Internet Connection.

Trusted LAN??? Is there some more Hardware that needs to be attached to make my end user computer more secure?

I need to go to bed, so, thank you, for any and all responses. I am sorry I will not be available for any immediate responses to any questions.

Good Night!!

---

### Post by lisati on 2009-04-28
Based on the quote you've given, I'd guess that the obvious meaning is most likely: a trusted LAN is one you trust to be safe. An example would be your own home network, where you have control over who gets access to it.

---

### Post by wizard10000 on 2009-04-28
> **lisati said:**
> Based on the quote you've given, I'd guess that the obvious meaning is most likely: a trusted LAN is one you trust to be safe. An example would be your own home network, where you have control over who gets access to it.

Yup.

In professional geek terms trusted network = a network you control.  Every other network is untrusted.

---

### Post by mikodo on 2009-04-28
You guys are fast!!

Yes, I am the only person on my computer. You have answered my question.

Thank you,

Mikodo

---

### Post by Peter09 on 2009-04-28
Note that if you are connected only by a modem to your ISP then you are on an 'Untrusted LAN' as there is no firewall that you control between you and you ISP. You will need Ubuntu's firewall to be configured.

---

### Post by mikodo on 2009-04-28
Well I am still up and one more question to Peter 09. I do have Firestarter running as it is mentioned in Beginning Ubuntu Linux by Keir Thomas. Really anything else is beyond my capabilities for now. Would this be enough with sensible internet usage?

---

### Post by Peter09 on 2009-04-28
Firestarter is a GUI for your firewall. So keep all your incoming ports closed and you will be OK. I've never used firestarter as I have a NAT firewall on my router, so I am a bit hazy about its functionality.

What is interesting is to keep an eye on your log files, use System->Admin->Log File Viewer.

Syslog and auth.log will show any break in attempts.

---

### Post by lisati on 2009-04-28
> **Peter09 said:**
> Note that if you are connected only by a modem to your ISP then you are on an 'Untrusted LAN' as there is no firewall that you control between you and you ISP. You will need Ubuntu's firewall to be configured.

I agree that a direct connection to an ISP *can* be considered a connection to an "Untrusted LAN". 

Thankfully there are options: as well as using Ubuntu's firewall (the one I know of is called iptables, I'd suggest checking out a "front end" such as firestarter or ufw to help with the settings, as setting iptables directly can be tricky) many routers have firewall capabilities.

---

### Post by mikodo on 2009-04-28
Thank you,

These responses have answered nagging questions of mine for a while.

Mike

---

### Post by mikodo on 2009-04-28
Say, would enabling an external firewall through use of a router, offer me more security than just using firestarter to configure the Linux kernel on my computer, which is directly wired now to my ISP's modem?

Second question: Can both firestarter and a configured external firewall in a router, be used to increase security of an end user computer like mine? 

Thank you,

mikodo

---

### Post by wizard10000 on 2009-04-28
The router will definitely help as you can put your machine on private address space so that it can't be seen from the internet.  That alone will take care of the inbound nasties unless you make some ports available to the internet which is generally a lousy idea unless you've got a solid need to do it.

For the *outbound* nasties - the ones that originate from your PC - you'd use a firewall.

---

