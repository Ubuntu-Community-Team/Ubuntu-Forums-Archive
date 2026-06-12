---
title: "Edubuntu LTSP Thin Client Hangs on Bootup"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by corngeek on 2007-07-01
Hello.

Well, right now I'm working on getting a LTSP setup in my basement lab, which I hope to be able to migrate to a nearby private school. I finally configured the server, router, and DHCP, and I booted up a laptop from the network using PXE. It worked fine. Then, I disconnected it. When I booted it back up again, it would take me to the Edubuntu loading screen with the bar, stay at the beginning for a few moments, then stop at a black screen with a blinking cursor, like it's expecting input. However, no keypresses are registered, not even attempts to go into a virtual console.

So, I turned it off, and booted up Windoze (did I mention it's not my laptop? ;)) There I discovered the network wasn't working. While I can access the internet from the server, I can't do it from another computer under that subnet. 

Here's my network topology:
Main Router/Gateway: 192.168.1.1
My Main Computer, hooked directly to the router (which the internet works): 192.168.1.2
Another router, connected to the main router: 192.168.10.1
LTSP Server: 192.168.10.100
Client: 192.168.10.???

Here's my /etc/ltsp/dhcp.conf:
```

authoritative;

subnet 192.168.10.0 netmask 255.255.255.0 {
  range 192.168.10.101 192.168.10.250;
  #option domain-name "example.com"; don't have an official domain name that I'm aware of
  option domain-name-servers 192.168.1.1;
  option broadcast-address 192.168.10.255;
  option routers 192.168.1.1;
  option subnet-mask 255.255.255.0;
  if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
    filename "/ltsp/i386/pxelinux.0";
  }
  else{
    filename "/ltsp/i386/nbi.img";
  }
  option root-path "/opt/ltsp/i386";
}

```

I also have a DCHP server running on the router, however it is only 192.168.10.2-192.168.10.50.

I am running Edubuntu Feisty on the server.

So, I have two problems. The client appearing to freeze when it boots up, and the lack of internet access on the Windows machine. I think they must be related, because I had internet on the laptop until I booted it from the network.

I need to get this done by the end of the summer, or they'll just turn back on Windows (*gasp*), so any help would be much appreciated! And remember: I'm not a complete Linux newb, but I'm certainly not adept at it by any means.

Thanks!

---

### Post by corngeek on 2007-07-02
Okay, I've discovered another piece of information that might help.

When I have the laptop (thin client 0) in the blank screen, flashing cursor mode, the other thin client (thin client 1) will boot up fine. Same thing if thin client 1 is in the blank screen--0 will boot up fine.

This makes me think it's something with the DHCP IP assignment. But, both seem to be alloted an IP when they boot--they only freeze after unpacking the kernel.

Can anyone shed any more light on the situation?

---

### Post by dbott67 on 2007-07-02
I had a similar problem when I was testing it out on my home LAN as well.  It turns out that although the PXE client was getting an IP from the Edubuntu server (192.168.1.249), when the kernel loaded on the client, it grabbed another IP (192.168.1.111) from my router.  During my troubleshooting, I disabled the router's DHCP server and the client's booted properly.

In a nutshell, I blacklisted the MAC address of the PXE-client machines on my router and let the Edubuntu DHCP server do the work.

Read my post & solution here:
[http://ubuntuforums.org/showthread.php?p=2945775](http://ubuntuforums.org/showthread.php?p=2945775)



-Dave

---

### Post by corngeek on 2007-07-02
Thanks for pointing me in the right direction! I found the Gentoo and LTSP wiki most informative.

However, I can't blacklist MACs on my router. So, I have to whitelist the MACs that will be used as thin clients on the server side of things. I'm still a little confused about the syntax of the dhcpd.conf file, though. Can you point me in the right direction?

Thanks again!

---

### Post by dbott67 on 2007-07-02
Here's my /etc/ltsp/dhcpd.conf file:
```
sysadmin@edubuntu:~$ cat /etc/ltsp/dhcpd.conf 
authoritative;

subnet 192.168.[COLOR=Red]1[/COLOR].0 netmask 255.255.255.0 {
  range 192.168.[COLOR=Red]1[/COLOR].201 192.168.[COLOR=Red]1[/COLOR].250;
  option domain-name "example.com";
  option domain-name-servers 192.168.1.1;  [COLOR=Purple]*#<--this is the IP of my D-Link router which has DNS-forwarding built-in*[/COLOR]
  option broadcast-address 192.168.1.255;
  option routers 192.168.1.1;   [COLOR=Purple]*#<--this is the IP of my D-Link router*[/COLOR]
  option subnet-mask 255.255.255.0;
  if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
    filename "/ltsp/i386/pxelinux.0";
  }
  else{
    filename "/ltsp/i386/nbi.img";
  }
  option root-path "/opt/ltsp/i386";
}

```

The only thing I changed was the 192.168.[COLOR=Red]**0**[/COLOR].xxx to 192.168.[COLOR=Red]**1**[/COLOR].xxx.

I would have just turned off the DHCP server in my router and strictly used the Edubuntu server, but I've got my router configured with some port-forwarding rules and other stuff, so I took the easy way out & just blacklisted the MAC addresses.  Besides, it's only for testing.

If you have any more questions or just need someone to bounce ideas off of, just let me know.

-Dave

---

### Post by corngeek on 2007-07-02
I've turned the DCHP on the router off for now.  But, my situation is just like the one on the [LTSP Wiki]("http://wiki.ltsp.org/twiki/bin/view/Ltsp/DHCP#Multiple_DHCP_servers_on_the_sam"): > It is possible to have a DHCP server together with a second DHCP server for LTSP on the same network segment. I use this to boot PC's as 'standalone' workstations or LSTP terminals depending on whether they boot from their hard disk or with etherboot/PXE. The second DHCP server is not always running.

It goes on to say that if you're not using Etherboot (which I am not) and cannot change the port it operates from, to >    1.  On the second DHCP server (for LTSP), do not include a 'range' option that overlaps with that from the first DHCP server (you should not do that anyway). **Only serve known MAC addresses**.
   2. On the second DHCP server, give out the same information for DNS, Gateway, Netmask etc as the first DHCP server for the case where a computer with known MAC address requests information (However, the IP adress given by the first or second DHCP server will be different).


I'm confused about how to only serve the MAC addresses. I haven't thoroughly Googled it yet, so I can probably figure it out, given enough time. But if anyone wants to help me out with this aspect...;)

---

### Post by dbott67 on 2007-07-02
I don't know how to do it either, however, it appears as though it's all spelled out in:
```
man dhcpd.conf
```

All sorts of examples for known and unknown clients.  Look under ADDRESS POOLS (allowing/denying, etc.).

-Dave

---

### Post by corngeek on 2007-07-06
/forehead-smack

Yeah...I just got a little too Google-happy there for a little bit. 

Actually, the only way I found to do this was to whitelist every thin client on the network. Now, with only 1 thin client (two with the laptop) it's not a big deal, but it won't be very pretty if this works and we start getting lots of computers on the network.

So, I finally realized that on the final network, there won't be any standalone/thin client hybrid machines, so there was no need to account for this. 

Just out of curiosity...can a Windows box use a dhcp server running under Linux? The laptop didn't seem to, but I was probably doing something wrong. If it did, I could just always leave the server on.

If anyone else is having this issue and needs a quick and dirty (not to mention very inconvenient) hack, here's the one I used temporarily: Just shut down the server when you want to boot a standalone, so the IP will be assigned by the router. Then, you can boot up the server and still have internet on your standalone. Like I said, inconvenient, but for a testing situation, it works.

Thanks again for all the help!

---

### Post by dbott67 on 2007-07-07
Yes, your Edubuntu box should be able to function as a DHCP server for all clients (Windows, Linux, OSX, printers, etc.).  In fact, most home-based NAT routers just run some sort of *nix-based variant to provide NAT, DHCP, etc.

So, if you want to let your Edubuntu server do all the DHCP work, just disable the DHCP server in your router and everything should work properly.

-Dave

---

