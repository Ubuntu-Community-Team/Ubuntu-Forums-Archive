---
title: "Port Forwarding Issues... Can't Seem to get it to Work."
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by SendDerek on 2006-11-14
Hey All Again!

Alright, so I'm trying to setup VNC so that I can remote desktop into my PC from any location.

I have the VNC Viewer and Server installed and setup correctly (as far as I know) on both my Windows PC's with disabled firewalls and static IP addy's (sorry, no ubuntu yet).

I have a linksys router (WRT54G v3) and I have followed [this guide]("http://www.portforward.com/english/routers/port_f") to get port forwarding setup.  I also have my firewall disabled for now just until I know I can get this setup.

I have an [Actiontec® GT701-wg Modem]("http://www.qwest.com/internethelp/modems/gt701-wg/index.html") that is loaned from Qwest HSI service with default settings.  The firewall setting is on Basic and after speaking with Qwest tech support, this should allow all ports to go through.  I would like to note that this modem is a router/gateway as well and it does have a port forwarding option.

This modem is connected to the router, and then to the computer.

I'm pretty sure I have port forwarding setup correctly, but whenever I try and test the 'openness' with [http://www.canyouseeme.org]("http://www.canyouseeme.org") port tester, it times out and says it cannot connect.

I have also tried to port forward with Bittorrent, but with no success either.  

I have NOT tried to plug-in directly to the modem and setup port fowarding on that yet.

What do you guys think?  Am I missing something easy?  Something that has his me was, do I need to forward the port from my modem to my router and then to my PC, or should it only be necissary to port forward from my router to my PC addy?  Something similar to this setup would be the double-router port forwarding.  A guide is seen [here at portforward.com]("http://www.portforward.com/help/doublerouterportforwarding.htm")

Sorry this was so long.  Any help or thoughts are appreciated!!

Thanks.

---

### Post by mayonaise15 on 2006-11-14
I think your situation sounds unnecessarily complex.  If your Actiontech is setup to let all traffic through, I'm not sure how it would translate traffic.  I suppose that it would just put out a broadcast to the VNC port, which might or might not be picked up by your Linksys router and forwarded to the right PC.  

What I would suggest is to turn the firewall settings back to full on the Actiontech.  Then I would just run the patch cable from the Actiontech port to another switch port on the Linksys, instead of the internet port.  That way you won't have a segmented network and it will be much easier on the brain.  Just make sure you change the static IP, Gateway, Subnet, and DNS settings to match your Actiontech

Best of luck :)

---

### Post by SendDerek on 2006-11-14
Thank you very much for the quick responce.  I am going to try that as soon as I can.

This thread isn't closed yet... if you have any other suggestions, I would like to hear 'em.

Thanks again!

---

### Post by dbott67 on 2006-11-14
It seems to me as though your computers are behind 2 NAT routers (the Linksys & the ActionTec).

To test this theory do the following:

1. Connect 1 PC directly to the Actiontec (do not use the Linksys at all) and try connecting to the internet.

2. Check the IP address assigned to the computer:
   - For Windows XP: **START > RUN > ipconfig /all**
   - For Ubuntu: **ifconfig -a**

If the IP address is 192.168.x.y or 10.x.y.z, then the Actiontec is functioning as a NAT router, which means that you don't really need the NAT-part of the Linksys.

If you purchased the Linksys to provide wireless capabilities to your network then do the following:

1. Connect one PC to the Linksys router & login to the management console.

2. Look for the section on DHCP server and DISABLE it.  Your Actiontec router will provide the DHCP service.

3. From the Actiontec modem/router LAN port connect an ethernet cable to one of the 4 LAN ports on the Linksys (do NOT use the WAN port --- the Linksys is only going to function as a wired/wireless switch).

4. Connect a PC to one of the 3 remaining LAN ports on the Linksys router.

5. Renew your IP address and verify that it is on the same network segment that was assigned by the Actiontec router.

6. In the Actiontec management console setup port forwarding to the desired IP address of the internal computer.  For VNC, the ports are 5800 (java), 5900 (VNC), 5500 (listening agent).

If you need more clarification on setup, just ask.  Also, post the following information about the various devices:

- Actiontec internal IP address
- Linksys Internal IP address
- the output of 'traceroute www.google.com' (depends on OS as to the actual command.  Windows = 'tracert www.google.com' or 'pathping www.google.com'.  Ubuntu uses 'tracepath www.google.com' and 'traceroute www.google.com').

-Dave

---

### Post by jpkotta on 2006-11-16
I have the same ActionTec gateway, and I too have had trouble getting port forwarding to work with it.  Specifically, I want to forward a port to my desktop so I can ssh into my machine from anywhere.  I did the obvious thing and forwarded port 22 (yes, I know I shouldn't use the default...) to my machine, which I have configured to ask for a specific IP address on the LAN.  The gateway doesn't seem to do anything about it, i.e., I run nmap on my internet IP address and it just shows the open ports for the gateway, and I can't ssh (it says "connection refused").  Then I tried to play with DMZ settings, to no avail.

I can tell you this: ActionTec is a NAT router and a wireless AP.

---

### Post by jpkotta on 2006-11-16
Ugh.  I'm pissed and happy at the same time.  On a whim, I tried sshing into my machine again.  I have disabled port forwarding and DMZ and all that because I never got it to work, and now the damn thing works.  Why?!  It doesn't make any sense.  I'll look at the settings when I get home and post back.

---

### Post by jpkotta on 2006-11-16
Remote firefox works, so I checked the settings.  Port forwarding is enabled for both udp and tcp, DMZ is off.  I turned all of that off!  I hate the way that thing doesn't like to update settings correctly.  Anyway, it still doesn't work to ssh from my machine at home back to the same machine over the internet, which is why I thought it didn't work before, but I can ssh to it from school, which was the point anyway.  

I'll tell you this: it is not enough to keep the firewall feature of the ActionTec off, you also have to forward a port.  You probably have to forward a port to the Linksys, and have the Linksys forward a port to the computer.  Or maybe there is a more elegant way that someone knows.

---

### Post by SendDerek on 2006-11-16
Wow... I'm glad I'm not the only one having problems with this stuff.  

It was already suggested that we plug the ethernet cable from the back of the modem to one of the switch ports on the router (not the internet port) so that our networks aren't segmented.  This makes a little sense, but not enough for me I'm afraid.  I tried it at home just really quick just to see if I could still get on the internet but I couldn't.

I'm going to try and play with the modem when I get the chance and see if I can't get that to port forward maybe.

I've yet to try the suggestion from dbott67 because I havn't had a moment of downtime yet.  I'm excited to try this explaination.

---

### Post by dbott67 on 2006-11-16
> **jpkotta said:**
> Remote firefox works, so I checked the settings.  Port forwarding is enabled for both udp and tcp, DMZ is off.  I turned all of that off!  I hate the way that thing doesn't like to update settings correctly.  Anyway, it still doesn't work to ssh from my machine at home back to the same machine over the internet, which is why I thought it didn't work before, but I can ssh to it from school, which was the point anyway.  

I'll tell you this: it is not enough to keep the firewall feature of the ActionTec off, you also have to forward a port.  You probably have to forward a port to the Linksys, and have the Linksys forward a port to the computer.  Or maybe there is a more elegant way that someone knows.

I have seen some of these NAT routers that have an additional layer of security... the dreaded firewall.  I was helping a patron access one of our databases that ran on a non-standard port and the built-in firewall was causing major issues.  As long as you're relatively security-conscious, you can disable that feature of the router.

As for using 2 routers, it can be done (I used to have my home network setup this way), but it does involve a little more tweaking.  I've attached a screenshot of a simple setup for SSH, but the principles apply for any port.

The second diagram elaborates on my earlier post for Derek, while the third shows another configuration for an "untrusted network".

Here's a [thread]("http://leovilletownsquare.com/fusionbb/showpost.php?post/95853/") in another forum with a similar situation that I replied to for setting up 'dual NAT'.  The poster wanted to offer wireless to friends & family, but also protect his own stuff.  This is the advantage of dual NAT.  Essentially, you can put untrusted devices on the 192.168.1.xxx network between the ActionTec and the Linksys, such as servers, friends, visitors, etc.  They will be able to get out to the internet, but they won't be able to get through the Linksys, as it would be acting as a NAT firewall.

-Dave

---

### Post by SendDerek on 2006-11-16
I'm so close... I know it.

After following the advice from dbott67, I believe I now have port forwarding setup correctly because it passes the canyouseeme.org test.

I can ping my dyndns service (myserver.dyndns.org) and it is reporting the correct IP address.

VNC Server is running correct on 192.168.0.6 and the correct ports are forwarding to that address.

However, I'm getting this error message when I type myserver.dyndns.org into the VNC Viewer dialog:

> 
unable to connect to host: Connection refused (10061)


Where should I go from here?  Is there a setting in my router that I forgot to turn on/off (I cannot access my router admin page now to check).

BTW:  I can VNC to the PC internally by typing in 192.168.0.6.  I cannot any other way though.

---

### Post by dbott67 on 2006-11-16
Hi Derek,

The reason it probably doesn't work for you is that your firewall at work may be blocking outbound traffic on port 5900.

-Dave

---

### Post by dbott67 on 2006-11-17
Is everything working now?

---

### Post by SendDerek on 2006-11-17
I think so, yeah...  I can't get to it from my home just because the campus has some pretty strict usage rights on this connection (I think they block that kind of connection, but I'm not sure).  I'm waiting to hear from my boss to see if he was able to get to it from his house.

So, for right now, it's solved.

Thanks a ton for your help on this one.  I'm still not sure how to configure the firewall to let me in from inside of work.  I don't think I have any firewall settings for outbound traffic on port 5900, but oh well I guess.

---

### Post by dbott67 on 2006-11-17
One thing you could do is to set your router to forward a port that is allowed by your campus.  For example, if your campus permits port 80, you could set your router to forward port 80 TCP to port 5900 TCP on 192.168.0.6.

Then, in order to connect, you would set VNC viewer to connect to myhost.dyndns.org:80.

You might not want to use 80, but you could use any "permitted" port (443-https, 110-pop3, 22-ssh, 21-ftp, 23-telnet, etc).  There are no rules preventing you from using the above ports for non-standard services... it just makes it a pain for other people that try to connect.  So, you could setup a webserver on port ftp port 21, but nobody would be able to connect to it unless the explicity stated the port:

[http://www.yourdomain.com:21/](http://www.yourdomain.com:21/)

In your case, you just need to tell VNC Viewer to use a different port than 5900.

I use this method at home so that I can VNC to all of my computers:
from work on port 5900 --> router --> 5900 --> desktop
from work on port 5901 --> router --> 5900 --> wife's laptop
from work on port 5902 --> router --> 5900 --> my laptop
from work on port 5903 --> router --> 5900 --> kid's computer

The VNC server still runs on port 5900 for all computers --- the router makes the conversion to the correct IP address on port 5900, even though the inbound traffic might be on a different port.

-Dave

---

### Post by burek on 2006-12-07
> **dbott67 said:**
> I have seen some of these NAT routers that have an additional layer of security... the dreaded firewall.  I was helping a patron access one of our databases that ran on a non-standard port and the built-in firewall was causing major issues.  As long as you're relatively security-conscious, you can disable that feature of the router.

As for using 2 routers, it can be done (I used to have my home network setup this way), but it does involve a little more tweaking.  I've attached a screenshot of a simple setup for SSH, but the principles apply for any port.

The second diagram elaborates on my earlier post for Derek, while the third shows another configuration for an "untrusted network".

Here's a [thread]("http://leovilletownsquare.com/fusionbb/showpost.php?post/95853/") in another forum with a similar situation that I replied to for setting up 'dual NAT'.  The poster wanted to offer wireless to friends & family, but also protect his own stuff.  This is the advantage of dual NAT.  Essentially, you can put untrusted devices on the 192.168.1.xxx network between the ActionTec and the Linksys, such as servers, friends, visitors, etc.  They will be able to get out to the internet, but they won't be able to get through the Linksys, as it would be acting as a NAT firewall.

-Dave

Just for noob in dual nat
is it common to do so?  Is thsi trick significantly security ? 
If computer wanna file sharing p2p, then double port forwarding is necessayrz. so, what can be the advantages ? 

we ll alwayas need port forward that will kick us our securitzy no ?

---

### Post by dbott67 on 2006-12-07
> **burek said:**
> Just for noob in dual nat
is it common to do so?  Is thsi trick significantly security ? 
If computer wanna file sharing p2p, then double port forwarding is necessayrz. so, what can be the advantages ? 

we ll alwayas need port forward that will kick us our securitzy no ?

Dual NAT can be overly complex for those without experience in port-forwarding and some of the other nuances of networking.

The only time I would recommend it is if you are going to share your network with untrusted computers (i.e. create your own wi-fi hotspot).  Otherwise, if it's just your personal computers on it  (or those of people you trust) then save yourself a few headaches.

-Dave

---

