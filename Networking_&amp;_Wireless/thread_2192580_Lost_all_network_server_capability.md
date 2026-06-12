---
title: "Lost all network server capability"
date: 2013-12-08
forum: Networking &amp; Wireless
---

### Post by grizdog on 2013-12-08
Hi,

Recently I got a new computer and upgraded to 13.10 - my old computer didn't have a video card that was good enough for Ubuntu 13, so I bought a new System76 with 13.10 preinstalled.

Generally, everything works quite well.  But now my network servers (mail and Apache, especially) don't work.  I can get ssh to work, so something is getting through, but as far as Apache is concerned, I can't even get anything like a failed attempt to show up in the error log, or the access log.  Nothing.  The computer appears to have no idea that anyone outside requested a service.  

Incidentally, Apache does work on my local LAN - both from the computer running the server, and from a laptop using wifi.  But nothing comes in from the outside.

I'm not at all convinced that Ubuntu is the problem, but I don't really have a better forum to post to.

So the things that sit between my LAN and the outside world are a Netgear WNR3500L router and a Motorola SB5101U Surfboard cable modem.  Both appeared to be working fine prior to the changeover to the new computer, but I can't be sure that everything was good to the last minute.

The router is configurable.  I have it set for port forwarding for ports 22, 80, 443, and 8080.  Everything looks fine, and as I said above, ssh (port 22) works, but Apache appears to get stopped completely.  Anyway, if I am doing something wrong there, I don't see it.  All I have found in the configuration that might be relevant is the port forwarding/triggering and NAT filtering, which I have turned off.  There are some other WAN-type settings, but I don't see where they would be a problem.  

The cable modem does not appear to be configurable.  Does anyone know how to configure one of these things?  I didn't find anything on the Web.

My line provider/ISP swears up and down they haven't changed anything.

Any ideas?  Other plcaes to look?

Thanks.

---

### Post by Iowan on 2013-12-08
I presume the machine plugs into the router - rather than the modem. Modems can "lock onto" a MAC Address and might need to be restarted. 
Are the servers on the new machine - or are they separate/different boxes?

---

### Post by grizdog on 2013-12-08
Yes, the router plugs into the modem, and that is all that plugs into the modem.  All the servers run on one computer, the new one running Ubuntu 13.10.  That computer is a direct connection to the router, the laptop I have used to see if it works on the LAN uses the wifi provided by the router.

I did upgrade the firmware on the router, but that was after this problem first surfaced.

Thanks for the reply.

---

### Post by 7182818 on 2013-12-10
Can you run tcpdump on your server and see whether the web traffic is making in there?  If it is, maybe check the iptables settings?  If it isn't, I would think that the problem is with the port forwarding on the wireless router.  It's weird that your SSH traffic is getting through but the web traffic is not :(

---

### Post by grizdog on 2013-12-11
tcpdump doesn't return anything on port 80, but I'll have to try that with someone hitting it from the outside.  But there is nothing - nothing- on port 80 in any logfile unless I access it from the LAN, and then everything works fine.

I called the cable company again (my internet provider), and they swear up and down it isn't them, or the modem.  I'm inclined to believe them, at least on the modem: It's a Motorola SB5101, and near as I can tell dumb as a post.  I can't imagine it getting in the way.

I am getting more and more suspicious of my router, a Netgear WNR3500L.  One thing I don't like is that every few days it assigns a new address in the 192.168.1 subnet.  That could be a pain in the long run, and I don't see a good reason for it, but for the moment, I don't think it's the problem.  I have NAT filtering turned off.

I wonder if buying a new router will solve everything.

Thanks.

---

### Post by 7182818 on 2013-12-11
Yea, you'll probably want to statically configure your server IP address instead of having it get an address via DHCP.  That way your port forwarding configuration will always match up with the IP and port that your server is running on.  Assuming those two things line up, though, I don't see why it wouldn't work.  I agree with you - I wouldn't think that the cable modem would give you any problems.

---

### Post by grizdog on 2013-12-14
OK, I went through everything again, from the beginning.  As recommended, the computer that runs the servers and has a wired connection to the router now has 192.168.1.2 as a static address.  

My computer is named foo.org -  the nameservice is fine.

In my /etc/hosts file, I have 127.0.0.1   foo.org foo

In my /etc/hostname file, all it has is foo.org

I had /etc/hostname with foo  in it, no ".org", but I changed it to see if it would help.

I can now telnet into port 80.  I get a response, telling me what the escape character is.  When I try to telnet to a port I don't have forwarded, it just hangs.  So that is a good sign, I suppose.

But I still can't get a web page served through the a browser unless I am on my lan, and then it works fine.  Now here is the odd thing:

Everywhere I can, I have referred to my computer as "foo.org", rather than foo.  There is that one entry in /etc/hosts, but when I type `hostname' at the prompt, it returns foo.org.  When I set up the static route on the router, I used the name foo.org, and that is the name it comes up with on that screen, but on the port forwarding screen, where you cannot set the name but just use the internal IP address, it shows up with the name "foo".  Is it possible that foo vs. foo.org is the problem?  THe fact that telnet seems to connect would suggest that is not true, although I don't know what the telnet is really connecting to - I didn't execute any commands that worked.  It could be "connecting" to some ghost of a machine that is no longer there.

I am stumped.  Any help would be greatly appreciated.

---

