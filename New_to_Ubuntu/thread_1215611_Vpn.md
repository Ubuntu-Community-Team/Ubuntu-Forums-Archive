---
title: "Vpn"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by Hoom@n on 2009-07-17
Hello.
How can I make a VPN connection in Ubuntu/Kubuntu with configurations like following picture in Windows?
[IMG]http://i31.tinypic.com/sn00ih.jpg[/IMG]
Thanks.

---

### Post by jonobr on 2009-07-17
Hello


Recommend you install vpnc with the kvpnc gui front end,
it will walk you through the settings for setting up a vpn.


The screen cap you gave, is the preferred authentication mechanisms used to connect with a VPN server (pptp or l2tp etc)

In other words when it calls in, it says  can I do PAP, SPAP , CHAP or MSCHAP

The server will respond with what it wants the client to do, so depending on your connection, some of these algorithms may be not required.

PAP is a basis password offering and authentication mechanism\
SPAP is an enhanced version of PAP developed by Shiva systems (not sure if its used much)
CHAP is a more secure form of authentication
MSCHAP was developed by Micoshaft


So you may be able to go to your admin and ask which is in use.
If he says chap, you could disable the others and the thing should work fine.

Im saying all this as when you use KVPNC I notice you can select either PAP or chap, not both.
Im also thinking you could set up two seperate connections.

Attached is a screen cap of what you should see.

In kvpnc it looks as if SPAP is not supported.
I have seen other posts indicating problems with MSCHAPv2 so Im not sure if that was fixed maybe you could check the launchpad

---

### Post by Hoom@n on 2009-07-22
> **jonobr said:**
> Hello


Recommend you install vpnc with the kvpnc gui front end,
it will walk you through the settings for setting up a vpn.


The screen cap you gave, is the preferred authentication mechanisms used to connect with a VPN server (pptp or l2tp etc)

In other words when it calls in, it says  can I do PAP, SPAP , CHAP or MSCHAP

The server will respond with what it wants the client to do, so depending on your connection, some of these algorithms may be not required.

PAP is a basis password offering and authentication mechanism\
SPAP is an enhanced version of PAP developed by Shiva systems (not sure if its used much)
CHAP is a more secure form of authentication
MSCHAP was developed by Micoshaft


So you may be able to go to your admin and ask which is in use.
If he says chap, you could disable the others and the thing should work fine.

Im saying all this as when you use KVPNC I notice you can select either PAP or chap, not both.
Im also thinking you could set up two seperate connections.

Attached is a screen cap of what you should see.

In kvpnc it looks as if SPAP is not supported.
I have seen other posts indicating problems with MSCHAPv2 so Im not sure if that was fixed maybe you could check the launchpad

Thank you, I try to check it soon.

---

### Post by Hoom@n on 2009-07-26
1-Why can't I make a VPN connection in Ubuntu?! I can make every other types of connections, but VPN is inactive!
2-How can I install kvpnc and how can I use it?

---

### Post by markharding557 on 2009-07-26
if you are on ubuntu(gnome)then you can install network-manager-pptp
i have had no problems with this at all but it is for gnome

---

### Post by Hoom@n on 2009-07-28
> **markharding557 said:**
> if you are on ubuntu(gnome)then you can install network-manager-pptp
i have had no problems with this at all but it is for gnome
You mean to enable the "Add" button in "Network Connections", I should install "network-manager-pptp"?
+I may connect to a L2TP VPN, will network-manager-_pptp_ work in that way?
Thanks.

---

### Post by The Cog on 2009-07-28
> **Hoom@n said:**
> You mean to enable the "Add" button in "Network Connections", I should install "network-manager-pptp"?
+I may connect to a L2TP VPN, will network-manager-_pptp_ work in that way?
Thanks.

I am sure that is what he means. 

I am not really familiar with those terms, and I'm not certain that network-manager-pptp is the correct package for L2TP VPNs. It is certainly worth a try.

---

### Post by Hoom@n on 2009-07-28
> **The Cog said:**
> I am sure that is what he means. 

I am not really familiar with those terms, and I'm not certain that network-manager-pptp is the correct package for L2TP VPNs. It is certainly worth a try.
**PPTP:**
I got network-manager-pptp and the add button activated. It's just for PPTP VPNs. I crated a pptp connection, but I don't know how to connect to it! When I click on my VPN connection name, nothing happens! Even no error message! How can I connect?
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=122699&stc=1&d=1248769249[/IMG]
**L2TP:**
I found [this]("http://www.jacco2.dds.nl/networking/linux-l2tp.html"), is it safe? Or, is there any other way to make a L2TP connection?

---

### Post by Hoom@n on 2009-07-28
For the fist time I got something by clicking on the VPN connection name! I got "**vpn connecting failed because the vpn service failed to start**" or something like that in a black pop-op(or maybe it's called something else) in top right corner. Now when I click it again, I get nothing! Just like before(previous post)
How can I connect?

---

### Post by jonobr on 2009-07-29
Hello

Just to clarify,

PPTP and L2Tp are two different things 

PPTP was a tunnel;ing protocol developed between (I believe ) microshaft and US Robotics/3com.

It was an extension and used part of the point to point protocol (PPP)

L2TP was a protocol developed between microshaft and Cisco and built on PPTP and used some protocol from Cisco I cant remember.

The PPTP tunnel is terminated at a PNS (PPTP Netwrok Server)
and the L2TP tunnel is termnated at a LNS (L2TP network server.)


Long story short though, they are different technologies and you can use one with the other.

---

### Post by Hoom@n on 2009-07-29
> **jonobr said:**
> Hello

Just to clarify,

PPTP and L2Tp are two different things 

PPTP was a tunnel;ing protocol developed between (I believe ) microshaft and US Robotics/3com.

It was an extension and used part of the point to point protocol (PPP)

L2TP was a protocol developed between microshaft and Cisco and built on PPTP and used some protocol from Cisco I cant remember.

The PPTP tunnel is terminated at a PNS (PPTP Netwrok Server)
and the L2TP tunnel is termnated at a LNS (L2TP network server.)


Long story short though, they are different technologies and you can use one with the other.
Thank you for information, but they don't solve the problem!
I can connect to my VPN server using PPTP or L2TP(with a pre-shared key) in my Windows, but I can't connect to it anyway in Ubuntu! What can I do?!

---

### Post by jonobr on 2009-07-29
if you go to /var/log

there should be some .log file relating to the protocol your using.
i.e. pptp.log etc

If tail -f the file try to connect and see if there are any error messages, that may help.

---

