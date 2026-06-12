---
title: "Any Luck with VPN Hosting?"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by SuperMike on 2006-12-28
Anyone got Zebedee (apt-get install zebedee) configured and working to tunnel two Ubuntu systems together securely and reliably over the Internet? I'm looking for an easy FAQ that I can try out. I was thinking about trying out this poor man's VPN. Might make a nice way to run an office of developers if I ever get my startup company off the ground.

---

### Post by dbott67 on 2006-12-28
Never used it, but what about SSH?

SSH has support for tunnels, so you can end other types of data through the encrypted tunnel, such as VNC, RDP and other applications in addition to just terminal access.

If you can provide more details as to how the 2 computers are connected to the internet (cable/DSL/dialup, router/NAT/Firewall, etc.) we can provide you with all the details.

-Dave

---

### Post by SuperMike on 2006-12-28
Well, it was really an experiment, actually. Sometimes to motivate myself in my moonlight software startup I daydream of success. I wonder what the company will be like, how efficient it will be, and so on. Right now at my day job during this Christmas break, it's slow and boring (thank goodness) and I have a lot of free time to think about stuff. I started to wonder about a hypothetical company that's really tiny and doesn't want to spend a lot of money on a fancy VPN solution. Instead, the guy has an office PC and a home PC. He does something on his office PC that exposes it on the Internet (even through a NAT router), and then goes home and accesses it from his home PC on DSL high speed Internet. His access, of course, would have to be encrypted and would have to be sort of fast. So I don't care, actually, what tool is used as long as the procedure works well.

Meanwhile, I think a lot of people would like to find out how this is done so that they could try it.

---

### Post by dbott67 on 2006-12-28
SSH sounds like it would do the trick.

Most NAT routers now have support for dynamic DNS (dyndns.org) so that you can have a fully qualified domain name for each router (i.e. supermike.dyndns.org & someotherguy.dyndns.org).

Setup port-forwarding on each router (port 22 to the desktop's internal IP) and you've now created a nice secure SSH tunnel to move data through.  Just by itself, you would have command-line access to the PC and you can even tunnel VNC through it if you want graphical access:
[http://www.linuxplanet.com/linuxplanet/tutorials/6155/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6155/1/)
-Dave

---

### Post by SuperMike on 2006-12-28
Thanks a lot! I'll give it a try and let you know. It might not work with my hyper-restrictive, oppressive, domineering, evil darklord, global employer that I work for, but I'll give it a try. If that won't work, I'll try between two Ubuntu PCs in my house (going over the Internet separately) to simulate this. I think it's good experience. I'll let you know how it goes.

Question: How does the dyndns.org thing get kicked off?

---

### Post by SuperMike on 2007-01-01
> **dbott67 said:**
> SSH sounds like it would do the trick.

Most NAT routers now have support for dynamic DNS (dyndns.org) so that you can have a fully qualified domain name for each router (i.e. supermike.dyndns.org & someotherguy.dyndns.org).

Setup port-forwarding on each router (port 22 to the desktop's internal IP) and you've now created a nice secure SSH tunnel to move data through.  Just by itself, you would have command-line access to the PC and you can even tunnel VNC through it if you want graphical access:
[http://www.linuxplanet.com/linuxplanet/tutorials/6155/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6155/1/)
-Dave

Thanks for the link. I think the technique for a poor businessman's VPN works like the following. Please confirm if you can -- after a bit of testing at my home on this I think it might work in the Ubuntu Document Storage Facility.

FROM THE OFFICE

1. In this hypothetical example, first, the business man takes all the Linux PCs for the developers and ensures they are configured properly with ClamAV virus scanning (and set to scan properly and notify properly), automatic Ubuntu updates, and has installed a local iptables firewall that blocks all ports except 22, (perhaps 80 and 443), 5900 for the local LAN, and an alternate port (designated from step # 2) for the outside world.

2. The business man copies his SSH daemon file in /etc/init.d as "pmvpnd" and edits it so that it comes up not on port 22 but on an alternate port like 16022. If the businessman had a team of developers, each would do this and use a different port like 16023, ..24, ..25, etc. They then fire up this daemon with:

```
/etc/init.d/pmvpnd start
```

...and if he wanted to, the businessman could stop it with:

```
/etc/init.d/pmvpnd stop
```

3. The business man connects to the web interface of his router and turns on port forwarding so that incoming traffic on a certain port gets directed to another workstation on the local LAN on that same very port. On a USR Broadband Router web interface, for instance, he clicks on Security Setting, Schedule Rule, and clicks Enable on Rule # 0 (the "Always On Rule") to always allow this rule all 24 hours. (Note, if he wants it different, he can create another schedule rule such as # 1 and assign a certain hours -- all from the web interface of the USR Broadband Router, for example.) Then, he clicks on Forwarding Rules, Virtual Server, and redirects each port number specified in step # 2 to their designated workstation. He also checks Enable to use Rule #0. This opens up that user's ssh, served up by a daemon/service called pmvpnd, to the outside world. Yep, there's a bit of risk here, but we've tried to alleviate that risk a little on step # 1 and we don't have to do step # 2 until the developer decides to leave the office for the night. 

4. The businessman then takes each developer's workstation and redirects the VNC traffic through the alternate port set up on # 2. Let's say one of the developer's was enabled on 16022. His command on his workstation would be:

```
# x11vnc (to enable his remote VNC for his current desktop)
# ssh FIREWALL -o Compression=yes -o CompressionLevel=1 -o Port=16022 -L 5900:localhost:5900
```

...where you've switched FIREWALL to the IP address of the firewall.

5. Now in some small business office networks, the IP address the broadband router uses to get on the internet is often not static, but dynamic. Therefore, remote connections from the Internet could not be guessable and that presents a problem. The best way is to go to dyndns.org, register the IP addresses for free, and then download this tool that runs repeatedly every hour on a cron schedule:

[http://www.dyndns.com/support/clients/]("http://www.dyndns.com/support/clients/")            (look for ddclient)

...in order to update the DynDNS website with your latest firewall's IP address.

The catch to dyndns.org is that it only gives you 5 free addresses. For more, you have to purchase them -- pricing is available on the website.

Dyndns.org gives you a name like "businessman.dyndns.org", but the full list of domains it provides hosting in are here:

[http://www.dyndns.com/services/dns/dyndns/domains.html](http://www.dyndns.com/services/dns/dyndns/domains.html)

...for purposes here, let's assume that developer1's workstation is registered as:

bm_dev1.dynalias.org

...and that completes the hosting.


FROM THE HOME NETWORK

1. No change is necessary on the home network's broadband firewall router, usually, but if so, you need to permit outbound port connections for the port specified in step # 2 of the office hosting configuration (above).

2. Next, we need to run this command to enable port connection to the remote location:

```
ssh bm_dev1.dynalias.org -o Port=16022 -o Compression=yes -o CompressionLevel=1 -R 5900:localhost:5900
```

3. And then the developer can connect to his Office PC with:

```
vncviewer localhost:0
```

This provides a full GUI interface to their desktop. Now, VNC is not the most efficient protocol in the world, so one could purchase licenses to NoMachine VNC or use XForwarding. For XForwarding, the technique is to enable it on the computer in /etc/ssh/sshd_config with:

```
X11Forwarding   yes
```

and then switch 5900 with 6000 and add a -X option parameter for the ssh command run on the home network's PC. The downside on X forwarding, although it would be fairly fast, is that it doesn't prompt for a password in the GUI and is a little less secure than the VNC option.


**Please confirm that this is specified correctly, if you could.** I'm doing my testing of this now.

---

### Post by ihristov on 2007-01-23
I use OpenVPN. It works great. [http://openvpn.net/](http://openvpn.net/)
I even have a Linksys WRT54GL running an openvpn client that connects my whole wired network at home to the office network.

> **SuperMike said:**
> Well, it was really an experiment, actually. Sometimes to motivate myself in my moonlight software startup I daydream of success. I wonder what the company will be like, how efficient it will be, and so on. Right now at my day job during this Christmas break, it's slow and boring (thank goodness) and I have a lot of free time to think about stuff. I started to wonder about a hypothetical company that's really tiny and doesn't want to spend a lot of money on a fancy VPN solution. Instead, the guy has an office PC and a home PC. He does something on his office PC that exposes it on the Internet (even through a NAT router), and then goes home and accesses it from his home PC on DSL high speed Internet. His access, of course, would have to be encrypted and would have to be sort of fast. So I don't care, actually, what tool is used as long as the procedure works well.

Meanwhile, I think a lot of people would like to find out how this is done so that they could try it.

---

