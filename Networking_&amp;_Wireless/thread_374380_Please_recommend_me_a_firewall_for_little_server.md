---
title: "Please recommend me a firewall for little server"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by jordi_rc on 2007-03-02
Hello mates,

I would like to know if you can recommend me a good firewall for my server (that uses Xubuntu).
I know some people use shorewall, and others like to use iptables by hand, coding all.
But my server is small and is just 1 pc.

So if you know some tool that may be useful for a server like mine,
that consist in  just one machine, running Xubuntu, with a router with hardware firewall, please tell me.
 For many months, maybe years, there will be no more servers nor dsl lines,
just 1 with 1 static ip.
So I just want software for THIS situation. In next months or years, I
will learn by the way, as I grow.
But just wanted to know a good solution for this little server: 1 dsl
line, 1 ip, 1 machine. No more.
And better: I can use this server directly, with the keyboard, as I
access to it with a KVM Switch. So don't need to manipulate it through
ssh for now,

Having this in mind, do you know a good and simple solution? I will
have much time to learn for future, it is just to have a start point.

I saw there is firestarter, that says it is secure and defends against ddos. 
I wonder if shorewall is for me like using a cannon to kill a flea.
Do you know if there is something as easy as shorewall, and as strong as it?

Thanks for replying

Jordi

---

### Post by dannyboy79 on 2007-03-02
i would say either use Firestarter (simply a gui frontend for iptables) or you could use this thread to configure iptables yourself. This is what I use for my file server at home.

[http://www.ubuntuforums.org/showthread.php?t=57111](http://www.ubuntuforums.org/showthread.php?t=57111)

plus, if you have a router with a firewall, a software firewall isn't much better than the hardware firewall you already have.

---

### Post by techamed on 2007-03-02
Anything that uses IPtables would work well... iptables comes with the linux kernel.  Like the above post said, firestarter works really nice.

---

### Post by jordi_rc on 2007-03-02
Thanks techamed and dannyboy79

People in Debian forum recommended me Shorewall, but I think I will use Firestarter, as it is easier, and I am not masochist, and have tons of work to do.

I think for my needs Firewall will do the work.

This arises 2 questions:

How can I combine the hardware firewall with the software firewall? Can I ?

And I saw that in the firewall that my router has I see the logs and read things like these:
> 
FIREWALL exact tcp state check (1 of 6): Protocol: TCP Src ip: 128.242.99.117 Src port: 80 Dst ip: 85.48.166.19 Dst port: 56875


What does that info mean?

Thanks friends for replying.

Jordi

---

### Post by dannyboy79 on 2007-03-02
you can't combine your hardware firewall (most routers firewall capabilities built in-SPI and NAT) and software firewall. you can either run 1 or the other or both. 

I don't know what this is: FIREWALL exact tcp state check (1 of 6): Protocol: TCP 

but I can tell you that the end of it is telling you the IP address of the source (128.242.99.117, this may be your router's ip it gets from your isp) and it's port it's using which is 80 (that's the port internet surfing is done on) and the Destination was gong to IP (85.48.166.19 ) on it's 56875 port.

---

### Post by jordi_rc on 2007-03-02
Thanks dannyboy79

Nice to see a simple answer.

So now I know that I can't use software and hardware firewall at the same time.

So I will just leave the hardware firewall, as it is safer.

So iptables is a software firewall?

Thanks.

Jordi

---

### Post by dannyboy79 on 2007-03-02
> **jordi_rc said:**
> Thanks dannyboy79

Nice to see a simple answer.

So now I know that I can't use software and hardware firewall at the same time.

So I will just leave the hardware firewall, as it is safer.

So iptables is a software firewall?

Thanks.

Jordi

um no, that's not what I said at all. I specifically stated this and I quote, "you can either run 1 or the other or both". Yes, iptables is a software firewall.

---

### Post by jordi_rc on 2007-03-03
Thanks

And what do you think about this router that has firewall:

[http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_USA&pid=1588](http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_USA&pid=1588)

The text says:

> 
SMC7904WBRA2
ADSL2/2+ Barricade™ g

54Mbps Wireless 4-port Annex A ADSL2/2+ Modem Router

Overview
The SMC7904WBRA2 combines an ADSL2/2+ modem, router, 4-port 10/100 LAN switch, 802.11g wireless access point & robust SPI firewall making it the complete solution for securely connecting & sharing your high speed ADSL connection, wired or wirelessly. It gives you instant always on internet connectivity with download speeds up to 24Mbps – ideal for streaming multimedia content to the home. The EZ Installation Wizard with on-screen help configures your ADSL connection & wireless network in 5 easy to follow steps. Quality-of-Service gives priority to real-time, delay sensitive applications like Voice-over-IP and video-on-demand to improve the user experience. The NAT firewall with Stateful Packet Inspection (SPI), Intrusion Detection System (IDS) & Denial-of-Service (DoS) provides robust security from hackers. VPN pass-through is also provided for securely connecting to your office or corporate network. 


It is made by SMC Networks. Is that trademark a good one? What do you think of the device description? It is only 79 euros here in my country.

Jordi

---

### Post by dannyboy79 on 2007-03-03
yes, that router is good. Well it will get the job done!  i think smc is a branch of some major company but I can't think of it right now.  what about the linksys wrt54g router ([http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1149562300349&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1149562300349&pagename=Linksys%2FCommon%2FVisitorWrapper)) that you can install a form of linux on and make it way better than it is. [http://www.dd-wrt.com/wiki/index.php?title=Installation](http://www.dd-wrt.com/wiki/index.php?title=Installation)

but I think you need to get a certain version so that the linux version firmware is most compatible. i just have a netgear similar to this 1:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=541910&Sku=N100-1472](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=541910&Sku=N100-1472)

---

### Post by jordi_rc on 2007-03-03
I will consider the different options.

Thanks!

Jordi

---

### Post by Bram77 on 2007-03-03
In case you like to make it real easy for yourself to manage te server, and the server is dedicated, I would use ClarkConnect. I've been using it for three years now. It's real easy to set up and is rocksolid. It's based om redhat and uses apt. So it isn't difficult to use for a Ubuntu user :)

[www.clarkconnect.com](www.clarkconnect.com)

---

### Post by jordi_rc on 2007-10-12
Thanks Bram77

Sorry for not replying soon, my excuse is that the notifications don't seems to work well for me, and I didn't received the notify that you had replied.

I suppose you talk about the Community edition of ClarkConnect, isn't it? I will also test it.
Thanks

Jordi

---

