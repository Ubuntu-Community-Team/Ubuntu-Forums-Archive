---
title: "PC to PC Connection or PC to Router To PC connection error"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by theyain on 2007-06-14
'Ello.  I am trying to set up a connection from my Ubuntu PC to a Windows Laptop. 

The Windows Laptop is going to be using a wireless card to connect to a wireless network and through that the internet.


I can either have it set up so that my PC is connected directly to the Laptop via a crossover cable or I could have it set up (last resort please) so that my PC is connected to a router and then from there to the Laptop.

Basically it would look kind of like this:

[IMG]http://i7.photobucket.com/albums/y263/theyain/8a1896c3.png[/IMG]


I have done the this before with these computers, but for some reason, my little network here became screwed up and I couldn't connect.  I do not remember how I set it up or what IP i used.  And as a futher note, I would rather it be a direct connection to the laptop due to that my router is hard to configure.  Its a Netgear router, model number: wgt624 v3.  Yes, its wireless.


So, any help, or am I doomed to using Windows while in this room?

---

### Post by Mr. C. on 2007-06-15
If you want a direct connection, you'll have to configure your laptop to route the traffic between the two networks (your PC-to-laptop network, and your laptop-to-wireless network).

Setup your Windows station to properly route the traffic or share its internet connection, and then configure your PC with to obtain its address dynamically.

MrC

---

### Post by theyain on 2007-06-15
> **Mr. C. said:**
> If you want a direct connection, you'll have to configure your laptop to route the traffic between the two networks (your PC-to-laptop network, and your laptop-to-wireless network).

Setup your Windows station to properly route the traffic or share its internet connection, and then configure your PC with to obtain its address dynamically.

MrC

I know that, I have said I have done this before.  But recently that short network became screwed over and no matter what I try, it won't work.


Also, for me to set up the Windows station to actually act as the router I intend it to be, its going to need its own IP address.  


But I am lost.

---

### Post by Mr. C. on 2007-06-15
Your previous success may have been pure luck, or the result of your knowledge.  I don't know what you know and don't know, so have to start somewhere with my assumptions.  It serves little purpose for me to assume you know how to configure your systems correctly, as you would not be seeking an answer otherwise!

On one had you say you know how to do it, on the other you say "you are lost".  What should I help with ?

Let's start with...

Have you  run the Windows network configuration wizard to configure your windows system to share its network connection with other computers?

MrC

---

### Post by theyain on 2007-06-19
I have.  What I had done was (and this just from my UbuBox to the Windows computer) was set up an IP, Subnet Mask, and a Gateway (I had forgotten all of that information :( ).  Then I set DHCP on the UbuBox and had Simba installed.  Everything worked fine there.  Then I had shared the wireless connection and I was able to connect to the internet from my UbuBox.


I don't know what went wrong two weeks ago, but at one point neither computer could connect.  I disconnected the wired connection from the lappy to the UbuBox, and I could connect to the internet from the Laptop.  Once I think about it, it probably was an IP address confliction between the my box/ laptop network and the rest of the network I have set up in this house.  

I think that the router had been reset (the old for it was 10.10.10.1), thus turning its IP back to  192.168.1.1.  Also, added information. I know quite a bit about networking.  Not anything at an expert level.  But I understand all of the basics and then some.


More information: My modem (for DSL) IP is 192.168.0.1  Changing the Router's IP is not possible right now.

---

### Post by Mr. C. on 2007-06-19
I'm not sure if there is a specific question in your response, or just a summary.

MrC

---

### Post by theyain on 2007-06-20
> **Mr. C. said:**
> I'm not sure if there is a specific question in yoru response, or just a summary.

MrC

It was a summary.

---

### Post by theyain on 2007-06-20
Bump due to help is needed.


Also, couldn't I set the laptops NIC card to DHCP and set a static IP on the UbuBox?

Wouldn't that work?

---

### Post by Mr. C. on 2007-06-20
Theyain,

I don't mean to make you feel bad; you're not give anywhere near enough information to solve a problem, nor a specific problem to solve.

Please state clearly what you a) are trying to accomplish, and b) show evidence of what works and doesn't work (eg. command output from terminal windows, Windows "ipconfig /all", etc.

You say you know enough about networking, but there is not enough network information here that supports that claim.  What are the network addresses of each network, interface, gateway, etc.?

TCP/IP networking works.  If it is not working for you, that means you have a misconfiguration.  Without seeing the actual data, its too difficult to guess what you have not configured correctly.

MrC

---

