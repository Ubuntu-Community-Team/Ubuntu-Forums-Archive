---
title: "Unable to connect remotly - port forward issue."
date: 2015-04-23
forum: Networking &amp; Wireless
---

### Post by pingaan on 2015-04-23
Hi,

I am new to opening up ports. I've been following the guides on portforward.com (direct link below). I have a bridge, provided by my internet provider, as well. I asked them about it and according to them it can't possibly have anything to do with the issue since the only thing the bridge does is channeling the information directly to my router. 
Is there anything besides "ufw" that could block the connections implemented in Ubuntu?

Router: [(http://[URL=&quot;http://)[url&quot;&quot;"]http://portforward.com/english/routers/port_forwarding/TP-Link/TL-WR1043ND]("http://[URL=&quot;[http://[URL=&quot;http://)/[COLOR=#404040][FONT=verdana]

Regards.[/FONT][/COLOR]

---

### Post by TheFu on 2015-04-23
ufw is just an interface to the Linux firewall.  iptables is the only firewall on your system. 

Run **sudo iptables -L** to see any rules.

If you are running a TL-WR1043ND - that is a router and you will need to forward ports through it.  I found that specific router to be extremely buggy - to the point that I had to remove it from my network.  Also, the firmware provided by the company has known back doors, so if you do intend to keep the hardware, please, please, please replace the firmware with some after market version - perhaps dd-wrt?  As I recall, the getting DD-WRT loaded was a multi-step process that required installing some German firmware from the vendor.

BTW, I bought the router based on specs and a quick compatibility check for DD-WRT. Turns out that isn't enough to check to get a good router. ;(

---

### Post by pingaan on 2015-04-23
Hmm.. OK. Thought that what was an actual firewall.

Output of sudo iptables -L:
```
$ sudo iptables -L
[sudo] password for tobbe: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

No idea what any of it means.
I did update the firmware some time ago, might have to do it again?

---

### Post by TheFu on 2015-04-23
All "firewalls" on linux systems (for the last 10+ yrs) have been UIs into iptables which is the only firewall. 

Soon (depends on the kernel running), iptables will be replaced by a new kernel-firewall, I don't recall the name now. You can google to read up about that, if you care.  When that happens, any "firewall" program with a UI/GUI will just be an interface to make things easier for people like you and I to access the real firewall running in the kernel.

Router firmware needs to be updated every 6 months or so. There aren't always updates, but setting a calendar reminder to check if one is available is smart.

---

### Post by pingaan on 2015-04-24
So you're suggesting updating the firnware and try again.

---

### Post by TheFu on 2015-04-24
I'm saying that I had the same model router as you and it was very flaky. I've removed it from my network.

I'm saying that the firmware provided by the company should NOT be used. 
[https://securityevaluators.com/knowledge/case_studies/routers/tp-link_wr1043n.php](https://securityevaluators.com/knowledge/case_studies/routers/tp-link_wr1043n.php)
[http://aspiregemstone.blogspot.com/2011/07/hacking-tp-link-wr1043nd-part-1.html](http://aspiregemstone.blogspot.com/2011/07/hacking-tp-link-wr1043nd-part-1.html)
[http://www.routerpwn.com/#tplink](http://www.routerpwn.com/#tplink)

I assume you know how to port forward. If you aren't certain, there are some articles that explain it at lifehacker or howtogeek.

---

### Post by pingaan on 2015-04-24
Well.. Like I said in the first post; I'm all new to opening ports, so apart from the guides foind on portforward.com I'm not really familiar with it.
I actually have two other routers setup as access points at home two. Maybe I should give those a try? Their both Asus. Can't recall the model right now.
Could you perhaps provide a link to a lifehacker/howtogeek guide? 

Cheers.

---

### Post by TheFu on 2015-04-24
Portforward.com makes it seem like you need a program to do this. You don't.
I looked at the page for the router - that list is huge.

Perhaps we need to step back - which service are you trying to make available over the internet?  A good server that does almost everything that anyone would need is ssh. [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh) has a short list of all the amazing things it can do - all by opening 1 port and it is secured without passwords by using ssh-keys. Keys are both more secure AND more convenient.

---

### Post by pingaan on 2015-04-24
Hmm.. The guide I'm following doesn't say anything about using a program aside from a web browser.
SSH actually onw if the programs I would like to use but I can't open up port 22 (default afaik), so I can't connect.

---

### Post by TheFu on 2015-04-24
> **pingaan said:**
> Hmm.. The guide I'm following doesn't say anything about using a program aside from a web browser.
SSH actually onw if the programs I would like to use but I can't open up port 22 (default afaik), so I can't connect.

If you follow the previously provided link, on that page, the very last link talks about ssh security which includes NOT running it on the default port.  If you cannot get a port forwarded on the router, then you are screwed my friend.  If you can, then use port translation, which is a best practice.

Regardless - I'll ask again - 
> Perhaps we need to step back - which service are you trying to make available over the internet?

Might be helpful if you talked about static IPs on the WAN and LAN for the server too.

---

### Post by pingaan on 2015-04-24
I just want to thank you for your fast replies, I really appreciate it! :)

I'm not sure link you are talking about, but never mind. I only tried one guide out on that site, which was the guide for VNC.
I'm going to try updating the firmware, after that swap the router out for the Asus device.

The services I want to get connected to are SSH, VNC, WOL (wake on lan), Plex.

ps. router no. 2: [Asus RT-N12](http://www.asus.com/Networking/RTN12_C1/)

---

### Post by TheFu on 2015-04-24
WoL only works on the LAN. It will not work over the internet. There may be a way to have the router send WoL packets. IME, it requires a few attempts before it works.

VNC needs a VPN to be used safely. It doesn't have any encryption. So - there is no need to open the VNC port on the router - just get ssh working and you can tunnel to VNC through an ssh tunnel.   Or, if you plan to use Windows/OSX/Linux from a remote location, you can use x2go which works over ssh and is a more efficient (i.e. 2-3x faster) AND a more secure remote desktop for Linux.  I use x2go from different countries around the world when on travel. I've used it from 3 different continents and find it the best remote desktop option for Linux.  To access Windows, I use x2go into a linux machine on the same subnet, then use RDP from the linux machine to the Windows machine (all inside an x2go).

Plex ... I use plex, but access it through an openvpn connection so no ports need to be opened for Plex to work from anywhere in the world. Plus I don't have a plex-account with their website.  I've listened to music from the plex server over x2go - forget video. The openvpn configuration is non-trivial.

The key thing in that link is "port translation."  WAN-side of the router listens on some high port - perhaps 64022 and forwards the connection to a LAN server on port 22. The LAN server must have a static IP.  If you don't understand, use wikipedia and/or google to look up the terms.

Hopefully you've patched the Asus RT-N12 too.

Good luck.

---

### Post by pingaan on 2015-04-24
I haven't yet tried any of my suggestions yet, so as for the port 22 it'll have to wait till tomorrow..

I don't worry about the unencrypted connection with VNC as I am, in fact, always connected to a VPN. However I will try x2go.

As for Plex. I haven't even looked into it. I settled with the text; 
```
Not available outside your network
Your server is signed in to Plex, but is not reachable from outside your network.
You may need to enable this to establish a direct connection from outside your network. 
 You may also need to configure your router.  Detailed instructions are available [here]("http://support.plex.tv/hc/en-us/articles/200931138-Troubleshooting-myPlex-Server-connections").
```

I have setup static ip's for most devices on my home network but for this one I'm using a DNS. I thought it would be more convenient when accessing the computer from outside.

---

### Post by TheFu on 2015-04-25
> **pingaan said:**
> I have setup static ip's for most devices on my home network but for this one I'm using a DNS. I thought it would be more convenient when accessing the computer from outside.

DNS is fine, but without a static IP, you won't be able to forward the port internally in the correct way. You can use a *DHCP reservation* for that if you like, but the LAN IP for any "server" cannot change unless you will manually modify the router telling to forward the port to a different IP every time a change to the IP happens.

---

### Post by pingaan on 2015-04-28
Didn't know that. However the IP has been set on my devices for some time now, with DNS or with out..

I found the problem. The problem is being connected to a VPN (my VPN service only?). As soon as I disconnected it worked just fine. 
Any ideas? I mean, this isn't a filesharing server, I'm not doing  anything illigal as such. I just prefere to be "protected" att all times, no matter what I do online.
Is it possible to sort out with the VPN active? 

edit: The port doesn't seem to work when trying to reach it through the DNS either.

---

### Post by TheFu on 2015-04-28
> **pingaan said:**
> Didn't know that. However the IP has been set on my devices for some time now, with DNS or with out..

I found the problem. The problem is being connected to a VPN (my VPN service only?). As soon as I disconnected it worked just fine. 
Any ideas? I mean, this isn't a filesharing server, I'm not doing  anything illigal as such. I just prefere to be "protected" att all times, no matter what I do online.
Is it possible to sort out with the VPN active? 

edit: The port doesn't seem to work when trying to reach it through the DNS either.

What do you mean by "VPN service?"  If you are running it at the same location, then you can control what works and what doesn't.  If this is some external VPN service, that may be a completely different issue and would depend on whether they allow _split tunnels_ and how the routing is setup on both their-side and yours.  I've only used VPN services that I ran or were run by a company for remote access. We don't allow _split tunnels_ for security reasons, so ... no services could be hosted on my system that was running the VPN connection.  You could use another box - however.  

So ... take a look at the routing table with and without the "VPN service" active. See any differences?

---

### Post by pingaan on 2015-04-29
By VPN service I mean a service that I pay for, no ports I have control over.
Thanks alt for the help, TheFu!

Going to mark this one as solved.

---

### Post by TheFu on 2015-04-29
I didn't mean to come across as so hopeless. I don't know, but I think VPN servers made for geo-exits outside your country probably DO allow split tunnels. Being non-secure on the client-side really isn't their worry.
If you post the routes - with and without the VPN-service active, someone may be able to help.
Also, it may be really easy to run the ssh remote access stuff inside a small virtual machine - people/companies use those as "jump boxes" between networks all the time. I say may because the router of the VM may or may not be impacted by the VPN - don't think it will actually.  However, if the VPN is running on the router devices ... I'm not sure.

---

