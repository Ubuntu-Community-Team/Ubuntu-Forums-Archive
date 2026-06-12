---
title: "Ubuntu Router Passing PPTP To Windows Server"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by Andrew Borem on 2007-09-06
I am having a terrible time trying to get my recently installed ubuntu corporate router to pass windows PPTP through to my windows VPN server.

My network looks like this:

extif  ---> intif  ---> network 192.168.2.0/24

I am trying to pass the VPN through with firestarter.  I tried the instructions at the following link to see if that would work, and it did not.  [http://www.fs-security.com/docs/vpn.php](http://www.fs-security.com/docs/vpn.php)

What am I missing?  All other port forwards work magically, but I just cannot dial into my windows server, no matter what I try.  

I really appreciate all of the help you guys give.  Thank you.

---

### Post by Andrew Borem on 2007-09-07
I have been messing with this more and more, and I just can't seem to get it.  I was going to try and use a different type of VPN, but I have 100 Windows computers using it, so that wasn't going to work out.

Any help would be VERY appreciated.

---

### Post by Synflux on 2007-09-07
Hi,

Those instructions allow protocol GRE (47) and tcp port 1723 (PPTP) through. I guess it would be worth checking that you haven't changed the port your windows server listens on? It is 1723 by default but you can change it in the registry? Might be worth installing something like wireshark on the windows box to see if you can see the packets coming in to it?

You don't mention what version windows you're running but need to check the firewall settings or the RRAS config to make sure it's not just being blocked there? Presumably it works from your internal network? But a firewall on your windows box might only be allowing connections from local subnet?

You changed the IP address of the server variable in that script to 192.168.2.x presumably?
:)

---

### Post by Andrew Borem on 2007-09-07
Yes, I did change the IP address in the script.  :D

Just to put this more clearly.  I am on a corporate network.  I have a cheap linksys router with pptp pass through enabled on it in place right now, and it works perfectly.  I am setting up this linux router on nights and weekends so I can roll it out at once and have everything work, and have a powerful router.

So, this isn't a firewall issue inside of the network.  It is using port 1723 because that is what I am forwarding with my Linksys router to make it work.  It works great right now, it just doesn't work on my linux router....

---

### Post by Synflux on 2007-09-07
Oh I see, I really don't know then. :( I'm suspicious over these IF and INTIF variables in the script, where are those defined as to which is which? Not sure as I've never tried that. 

Have you tried using wireshark to see any packets coming in to the windows box?

---

### Post by Andrew Borem on 2007-09-10
I am new to linux scripts.  How would I declare those variables?  

IF = extif
intif = intif

Right?

Thank you for your help.  I will try wireshark on the server.

---

### Post by Andrew Borem on 2007-09-10
after running wireshark on the server it appears that it is not getting any packets from the router...

---

### Post by Synflux on 2007-09-11
Hello,

It doesn't seem to mention it on the firestarter page but I found this:

```
# Set interface values
EXTIF='eth0'
INTIF='eth1'
```

on [[COLOR="DarkRed"]this page[/COLOR]]("http://ubuntuforums.org/showthread.php?t=257629")

Which might give some clues? So maybe just put:

```

IF='eth0'
INTIF='eth1'
```

At the beginning of the file, remembering you might have to swap the eth0 and eth1 values round?

:confused:

---

### Post by Andrew Borem on 2007-09-11
Okay.  I have the TCP pass through working.  My server is now getting the TCP packets.  But wireshark says that they are "resetting".  And I don't know what that means.

(I did the variable declaration.  THank you for that.)

---

### Post by Synflux on 2007-09-11
Hi,

So you can see the tcp 1723 and the GRE packets? Or just the tcp ones?

Off the top of my head I think an RST just means it's closing the socket but I'm probably wrong!

What error are you getting when you try your vpn connection?

---

### Post by Andrew Borem on 2007-09-11
It doesn't detect any GRE/protocol 47.  And I am getting Microsoft error 800.

---

### Post by Andrew Borem on 2007-09-11
I think my problem might have something to do with NAT or the way my network cards are communicating.  Let me explain.

I can make the VPN work if the following setup is employed

linksys router is left in
WAN = 10.10.10.1
lan = 192.168.2.1

Linux router is put in
WAN = 10.10.10.2
LAN = 192.168.2.2

If I then change the Default gateway of the Windows RAS server to 192.168.2.2 I can connect via VPN on 10.10.10.2.  But if I try and replace the linksys router with my linux router, and change the RAS server's gateway back to .2.1 and I reconfigure the linux router to take on all of the roles of the linksys router, the VPN stops working.

So confusing.

(I am also having massive problems with static routing.  As in.  SOmetimes it works, sometimes it doesn't sort of problems.)

---

### Post by Synflux on 2007-09-12
Eh?

So you've got the Linksys and your Ubuntu box both connected at the same time? What type of internet connection is it? xDSL? 

is it:

WAN->Linux EXT->Linux INT->LAN

or

WAN->Linksys EXT->Linksys INT->Linux EXT->Linux INT->LAN

The WAN IP addresses you've given are private ones so there must be some other gateway to the internet which you're plugging into? If so then that sounds like double NAT which is never fun.

Thanks,

---

### Post by Andrew Borem on 2007-09-12
I have a T1 with five public IPs.  I used the 10.10.10.x for the sake of simplicity.

---

### Post by Synflux on 2007-09-13
I'm afraid I really don't know. Hopefully this reply will bump the topic up and someone else might be able to help you though. Sorry. :(

---

### Post by tufkal on 2007-09-14
Im having the EXACT same problem.

I have pool of IP addresses, and just took out a linksys, and put in a ubuntu router.  Server install, with just the basics, DHCP/DNS/NAT.  I cannot find a way to get external clients to route past to 192.168.7.2 where my Windows 2003 Server is installed, running the PPTP VPN.  Local clients do work.  But outside clients dont.  I get errors in event log in Win2k3, about GRE, so i know the connection is going through but something isnt right.  

The basic rules I found are...

```


iptables -A INPUT -p tcp --dport 1723 -j ACCEPT
iptables -A INPUT -p 47 -j ACCEPT
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 1723 -j DNAT --to 192.168.7.2
iptables -t nat -A PREROUTING -i eth1 -p 47 -j DNAT --to 192.168.7.2

```

In addition to my standard firewall/nat rules.

But its not working :(

---

### Post by tufkal on 2007-09-14
OK i figured it out heh...

Here is the code that makes it work for me.

eth1 is my cable modem a.k.a. external interface
and 192.168.7.2 is my Windows 2003 box with PPTP server

```

iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 1723 -j DNAT --to 192.168.7.2
iptables -A FORWARD -i eth1 -p tcp --dport 1723 -d 192.168.7.2 -j ACCEPT
iptables -t nat -A PREROUTING -i eth1 -p 47 -j DNAT --to 192.168.7.2
iptables -A FORWARD -i eth1 -p 47 -d 192.168.7.2 -j ACCEPT

```

Now note, that this wont work for everyone trying to connected I have about 50% of ppl able to connect, because you still have the problem where some people have cheap routers that dont allow PPTP passthrough. 

But those 4 lines will setup the right forwarding for PPTP!

---

