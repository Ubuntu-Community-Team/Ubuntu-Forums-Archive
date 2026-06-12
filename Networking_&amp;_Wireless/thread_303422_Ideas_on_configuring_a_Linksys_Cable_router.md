---
title: "Ideas on configuring a Linksys Cable router"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by habtish on 2006-11-20
I am using a Linksys Cable/DSL router. (BEFSR41v4 )
I have setup an http server and also sshd on my ubuntu, just for the sake of learning.
 My problem is, my internal ip is assigned by DHCP which gets renewed frequently. For example my local ip would be 192.168.1.100 and I would go ahead and set my port forwaring to point to that IP. The next day, my IP would change to 192.168.1.101. or 102. and I have to continually keep on making changes in my port forwarding so I can get connected from outside. 
I have been looking for some answers on how to aquire a static local ip from the router to no avail. The Linksys people offered some help, but all their instructions were Windows specific and they didn't know how to set the same thing up in Linux. Any suggestion??
[keep in mind that i am pretty new to all of this and the more technical the responses, the more confused I get :) ]

Thanks in advance...

---

### Post by habtish on 2006-11-20
Nobody has any ideas or suggestions??....

---

### Post by FrodoB on 2006-11-20
Your linksys cable router should be assigned a know IP address and not use DHCP for its address. Normally one would setup the Linksys router as the DHCP server for the network.

---

### Post by NetworkGuy on 2006-11-20
If you want your web server to be seen to the outside world, there are several things you need to do.

First of all, make sure your ISP won't have a fit with you hosting a web server on their network, some ISP's will terminate your service for such.

After that you need to do things on both your router and your web server.

On your web server, you need to assign your NIC a static IP address.  TO do this you need to change your /etc/network/interfaces file so that eth0 uses the same IP address each time it boots.

After this, you need to make some changes in your Linksys router.   You need to setup port forwarding to allow anything accessing your router's public address (The one assigned from the ISP) on port 80 to the static IP address you set on your web server.

Next, you need to use a service like dyndns to setup a domain name that will follow your IP address if/when your ISP changes the address your router is assigned.

That's a 10,000 foot description on what you need to do.  Let me know if we need to divebomb on any topic for a more in-depth description.

---

### Post by tturrisi on 2006-11-20
> **habtish said:**
> I am using a Linksys Cable/DSL router. (BEFSR41v4 )
I have setup an http server and also sshd on my ubuntu, just for the sake of learning.
 My problem is, my internal ip is assigned by DHCP which gets renewed frequently. For example my local ip would be 192.168.1.100 and I would go ahead and set my port forwaring to point to that IP. The next day, my IP would change to 192.168.1.101. or 102. and I have to continually keep on making changes in my port forwarding so I can get connected from outside. 
I have been looking for some answers on how to aquire a static local ip from the router to no avail. The Linksys people offered some help, but all their instructions were Windows specific and they didn't know how to set the same thing up in Linux. Any suggestion??
[keep in mind that i am pretty new to all of this and the more technical the responses, the more confused I get :) ]

Thanks in advance...
He wants a static LOCAL ip address.
If using Gnome, go to System > Networking > Ethernet Connection ethX > Properties >  and setup a static LAN ip address.
/etc/network/interfaces should look like this for Linksys router:
```
# The primary network interface
allow-hotplug ethx  #where x = your device
iface eth0 inet static
	address 192.168.1.xx  #where xx = last octet of your desired static ip
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1
	#dns-search domain.com  #where domain.com = the domain name you used
```

---

### Post by kelbizzle on 2006-11-20
On the front page of the linksys config. Theres a field for " Maximum Number of  DHCP Users" The default should be 50 and those addresses start at 100. This means that anyone with a 192.168.1.**151**or higher Ip address will be outside of the dhcp. So what you do is specify an ip address for your computer. Anything above x.x.x.151. Then fill in the subnet 255.255.255.0, the gateway 192.168.1.1, click on the dns tab. You can find your dns address and search domain on the status page of the linksys config. After that. Everything should work. Being used to windows I restarted. haha Like a noob. I'm not sure if it was needed or not. So far it's working for me. If this is the incorrect way or not a l337 move. Can someone send me a pm telling me why. lol I just want to know it all.

---

### Post by habtish on 2006-11-21
> **kelbizzle said:**
> On the front page of the linksys config. Theres a field for " Maximum Number of  DHCP Users" The default should be 50 and those addresses start at 100. This means that anyone with a 192.168.1.**151**or higher Ip address will be outside of the dhcp. So what you do is specify an ip address for your computer. Anything above x.x.x.151. Then fill in the subnet 255.255.255.0, the gateway 192.168.1.1, click on the dns tab. .

I have followed this.. seems to be working so far, will see what happens in a day (when DCHP gets renewed) or after I reboot. Thanks for the advice

---

