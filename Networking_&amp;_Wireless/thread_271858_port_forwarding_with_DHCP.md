---
title: "port forwarding with DHCP"
date: 2006-10-05
forum: Networking &amp; Wireless
---

### Post by neumeka on 2006-10-05
I have a home computer (running Dapper) behind a Lynksis wrt54g router.  I have set up some simple port forwards on it, like port 22 for ssh.  
APPLICATION     FIRST     LAST     IP
ssh              22        22      192.168.1.0

The problem is that because I use DHCP, my home computer may grab a new ip sometimes.  When it does, it breaks my port forwards.  Is there a way I can specifiy port forwarding based on MAC addresses?  Or is there another solution to this problem?

thanks,
Kyle

---

### Post by wieman01 on 2006-10-05
> **neumeka said:**
> Is there a way I can specifiy port forwarding based on MAC addresses?  Or is there another solution to this problem?
Yes, you can do that. But you need to configure your router, this has nothing to do with the Linux settings. Your router should let you bind MAC addresses to IP addresses when using DHCP. At least my router does... Linksys.

---

### Post by Wicca on 2006-10-05
Although there might be a workaround for this, this is exactly the reason why I don't use DHCP on my tiny little LAN. I don't know how many machines you've got behind the linksys, I've got 3 machines behind a router with a lot of port forwards to all of them. I find it easier to administrate with DHCP disabled.

---

### Post by ohgod on 2006-10-05
I agree with wicca.  Static IPs will make your life easier.  

Or, if you don't want to go that route, you might be able to configure your router to always give out the same ip to dhcp requests from the same machine (by mac address).  Look for 'static dhcp' in the router config.

---

### Post by wieman01 on 2006-10-05
> **ohgod said:**
> I agree with wicca.  Static IPs will make your life easier.  

Or, if you don't want to go that route, you might be able to configure your router to always give out the same ip to dhcp requests from the same machine (by mac address).  Look for 'static dhcp' in the router config.
That said, some people require DHCP simply because they run NetworkManager that does not work with Static Leases.

---

### Post by CatKiller on 2006-10-05
> **neumeka said:**
> The problem is that because I use DHCP, my home computer may grab a new ip sometimes.  When it does, it breaks my port forwards.  Is there a way I can specifiy port forwarding based on MAC addresses?  Or is there another solution to this problem?

I just set up some port forwarding today, actually, for BitTorrent. My router is set to use DHCP to connect to the Internet, and it does whatever voodoo it needs with the cable modem for that. It's also set up to give out IP addresses using DHCP for my LAN, but the starting address is 192.168.1.10. My computers all have static IP addresses that are lower than this, and the default gateway for all of them is the IP address of the router, 192.168.1.1.

This means that I definitely know what the IP addresses of my computers are for port-forwarding and aliases and the like, but if anyone wants to connect their computer to my LAN, they can still get an IP address by magic.

---

### Post by neumeka on 2006-10-05
Thanks for the help.  I like you solution, catkiller.  I have a desktop and a laptop behind the router, but I'd like to keep the DHCP on incase friends come over.  That is going to work well.

---

### Post by Iowan on 2006-10-06
> **wieman01 said:**
> Yes, you can do that. But you need to configure your router, this has nothing to do with the Linux settings. Your router should let you bind MAC addresses to IP addresses when using DHCP. At least my router does... Linksys.
Check the router docs for info about static leases.

---

### Post by wieman01 on 2006-10-06
> **Iowan said:**
> Check the router docs for info about static leases.
??

---

### Post by CeeDub on 2006-10-08
> **CatKiller said:**
> I just set up some port forwarding today, actually, for BitTorrent. My router is set to use DHCP to connect to the Internet, and it does whatever voodoo it needs with the cable modem for that. It's also set up to give out IP addresses using DHCP for my LAN, but the starting address is 192.168.1.10. My computers all have static IP addresses that are lower than this, and the default gateway for all of them is the IP address of the router, 192.168.1.1.

This means that I definitely know what the IP addresses of my computers are for port-forwarding and aliases and the like, but if anyone wants to connect their computer to my LAN, they can still get an IP address by magic.

That method sounds like that's just what I need, but how do I go about doing it?  How do I assign my few computers with a certain address?

---

### Post by wieman01 on 2006-10-08
> **CeeDub said:**
> That method sounds like that's just what I need, but how do I go about doing it?  How do I assign my few computers with a certain address?
Your router should have such a function. My router let's me enable DHCP but then assign IP addresses to certain computers via MAC address (that's the unique name of you network adapter). Check out the manual or browse through the router settings.

---

### Post by CeeDub on 2006-10-08
> **wieman01 said:**
> Your router should have such a function. My router let's me enable DHCP but then assign IP addresses to certain computers via MAC address (that's the unique name of you network adapter). Check out the manual or browse through the router settings.

I hava a Belkin Wireless G router.  I've been looking in router setting, or what I assume are the router settings (I point my web browser to 192.168.2.1) and I haven't seen an option of assigning IP addresses to certain MAC addresses.  Am I looking in the wrong place?  What should I be looking for?

---

### Post by wieman01 on 2006-10-08
Yes, the web interface is certainly the right place to look for it. I would consult Belkin's customer service or check the manual if this option is available.

I've got Linksys and there it's no problem.

---

### Post by CeeDub on 2006-10-08
> **wieman01 said:**
> Yes, the web interface is certainly the right place to look for it. I would consult Belkin's customer service or check the manual if this option is available.

I've got Linksys and there it's no problem.

I've checked the manual and I don't see anything.  Website isn't much help.

Here's a screenshot of the web interface.  Where do I look?  What exactly am I looking for?

---

### Post by wieman01 on 2006-10-08
> Specify the Starting and Ending IP Pool Address...
That's a start. Make sure you have DHCP enabled and check out this option. Perhaps it's listed there.

---

### Post by CeeDub on 2006-10-08
> **wieman01 said:**
> That's a start. Make sure you have DHCP enabled and check out this option. Perhaps it's listed there.

Anything else?  I just don't know where else to look.

---

### Post by wieman01 on 2006-10-08
What's in "DHCP Client List"?

---

### Post by blackened on 2006-10-08
Honestly I don't see why you're fussing around with the router settings. Just leave dhcp enabled on the router, set your ips to static on each machine, then forward the appropriate ports to their respective machines. This way any machine that is plugged into your network that doesn't have a static ip will aquire one from your router. Problem solved.

---

### Post by wieman01 on 2006-10-08
> **blackened said:**
> Honestly I don't see why you're fussing around with the router settings. Just leave dhcp enabled on the router, set your ips to static on each machine, then forward the appropriate ports to their respective machines. This way any machine that is plugged into your network that doesn't have a static ip will aquire one from your router. Problem solved.
Some people need DHCP. Apparenly this is the case here as well. In particular for laptop users that do a bit of traveling DHCP is convenient. 

I prefer Static Leases as well but this is not the point as far as this thread is concerned.

---

### Post by CeeDub on 2006-10-08
> **blackened said:**
> Honestly I don't see why you're fussing around with the router settings. Just leave dhcp enabled on the router, set your ips to static on each machine, then forward the appropriate ports to their respective machines. This way any machine that is plugged into your network that doesn't have a static ip will aquire one from your router. Problem solved.

That's exactly what I need, but I'm not sure how to do it.  I would like DHCP enable, but I also need ports forwarded to one address without my router changing assigning that address to another computer.  If you have any suggestions for me setting static ip's on a DHCP router, I would appreciate them.

---

### Post by wieman01 on 2006-10-08
Ok, this thread it taking a different turn then. Setting up static ip is fairly simple. **Disable DHCP in the router and enable static leases.** Your router's IP address is:
> 192.168.2.1
I assume your wireless adapter is **"eth1"**? If not simply replace is with your one.

Run this command from a terminal window:
> sudo gedit /etc/network/interfaces
Replace the wireless section with this:
> auto **[COLOR="Red"]eth1[/COLOR]**
iface **[COLOR="Red"]eth1[/COLOR]** inet static
address 192.168.2.[COLOR="Red"]**xxx**[/COLOR]
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1
dns-nameservers 192.168.2.1
[COLOR="Red"]**xxx**[/COLOR] stands for your PC's IP address. Then save the file and restart the network:
> sudo /etc/init.d/networking restart

---

### Post by NoTiG on 2006-10-08
> **CatKiller said:**
> I just set up some port forwarding today, actually, for BitTorrent. My router is set to use DHCP to connect to the Internet, and it does whatever voodoo it needs with the cable modem for that. It's also set up to give out IP addresses using DHCP for my LAN, but the starting address is 192.168.1.10. My computers all have static IP addresses that are lower than this, and the default gateway for all of them is the IP address of the router, 192.168.1.1.

This means that I definitely know what the IP addresses of my computers are for port-forwarding and aliases and the like, but if anyone wants to connect their computer to my LAN, they can still get an IP address by magic.

nice trick man

---

### Post by CeeDub on 2006-10-09
Thanks wieman.  That did the trick. Thanks for all the help

---

### Post by wieman01 on 2006-10-09
> **CeeDub said:**
> Thanks wieman.  That did the trick. Thanks for all the help
No problem. I think the **Blackened's** point was that you don't even have to disable DHCP in the router for this to work. That's correct actually. Glad this works for you.

---

### Post by blackened on 2006-10-09
That was exactly my point. I apologize for the ambiguity.

---

### Post by CatKiller on 2006-10-10
> **neumeka said:**
> Thanks for the help.  I like you solution, catkiller.  I have a desktop and a laptop behind the router, but I'd like to keep the DHCP on incase friends come over.  That is going to work well.

Excellent.

> **NoTiG said:**
> nice trick man

Thanks. It's probably not very original, but I hadn't read that it was possible before I tried it.

> **CeeDub said:**
> That method sounds like that's just what I need, but how do I go about doing it?  How do I assign my few computers with a certain address?

Wieman is more experienced than I, and likes to get his hands dirtier :) I used the graphical tool at System -> Administration -> Networking to do my configuration.

> **blackened said:**
> Honestly I don't see why you're fussing around with the router settings. Just leave dhcp enabled on the router, set your ips to static on each machine, then forward the appropriate ports to their respective machines. This way any machine that is plugged into your network that doesn't have a static ip will aquire one from your router. Problem solved.

Indeed. And it works for those, like me, that don't have the option in their router to assign IP numbers based on MAC address.

---

### Post by wieman01 on 2006-10-10
> **CatKiller said:**
> Indeed. And it works for those, like me, that don't have the option in their router to assign IP numbers based on MAC address.
My router (WRT54G) does not support that, either. Just realized last night... In general I am in favor of Static IP simply because port forwarding is simpler, plus it adds to the entire security setup of your network. People would have to "guess" the IP range in the first place before they can do anything to connect to it. That's a weak point, though. Of course proper encryption (WPA2 / AES) & MAC filtering are a much better approach.

Nice talking to you!

Nakata

---

