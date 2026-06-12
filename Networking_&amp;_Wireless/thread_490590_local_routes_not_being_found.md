---
title: "local routes not being found"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by dhaus111 on 2007-07-02
Greetings,

I've experience a strange happening with my network lately.  All of the sudden I cannot ssh (on 22) or use rkdc/vino to connect to my gentoo box located in the living room using the ip address.  I did notice that I cannot connect to my linksys router either (192.168.1.1).  I can use the internet flawlessly (no DNS problems at all).  Using my roomates windows box I can VNC into the same Gentoo box without a problem at all.  Why would I be able to resolve internet names but not local ones with my Kubuntu machine?  It was working a few days ago...


Any Ideas?

?

---

### Post by WhimpyPeon on 2007-07-02
You should check your kubuntu box and make sure you have the proper entries in your /etc/hosts file so that the name can be resolved.  If you have a local DNS server on your network you don't need the /etc/hosts entries, however your /etc/resolv.conf file needs an entry for your local DNS server.

I am guessing that your Linksys router is acting as a DNS caching server to the Internet but not your local network.

You also might want to check that your kubuntu box is getting the right DHCP setup from the Linksys router.

ifconfig will tell you about your network settings.  If they don't look right you may have to reconfigure your networking to receive the information over DHCP.

---

### Post by dhaus111 on 2007-07-02
I can't look right now, cause I'm at work, but in my hosts file i have

XXX 192.168.1.10
or 
192.168.1.10 XXX

I've got no idea what my router is doing pertaining to DNS I'm not sure of how that works, I just know the basics of what a DNS server does.  It is functioning at its defaults as far as all DNS settings are concerned.  The Kubuntu box is set to static 192.168.1.2 or something similar.  As far as the resolv.conf, I'm pretty sure I had a look at it today and it had my ISP's DNS servers listed in there, as I belive is should.  In my attempts to figure out what was wrong I did come across an avahi error, return code 2 i believe, and it listed something at the front of the whole error code, I want to say something like RXXLINK or something similar.  sorry I can't provide exact details right now.

---

### Post by WhimpyPeon on 2007-07-05
Many of your home routers can do some networking tasks for you.  They can forward DNS request to your ISP DNS servers for Internet requests.  Some can also handle DNS requests for your local network once you enter information on local network static addresses.  One very nice feature is that they can pass on network settings through DNS.

What I would suggest is that you try to get into your router's configuration interface and see if that is available.  Leave your server(s) as a static setup and enter their addresses into your router's host list.  Then make sure it is setup to hand out DHCP addresses/information in a range that excludes your server(s).  Then change your desktop/laptop machines to obtain their ip information from DHCP.

Then, try to connect to your gentoo machine through either host name or IP address. If you are unable to connect to the gentoo machine, I would check the log files on the gentoo machine to see if it is blocking the requests for some reason.  You may get a hint there.

The nice benefit of using you router for DHCP is that you should be able to plug a computer in to the network and it is up and running without any problems or configuration.  It will almost guarantee that you don't run into address conflicts (especially if you assign any static addresses outside of the dynamic range).

If your router isn't capable of decent DHCP service you may want to consider using your gentoo box as a DHCP/DNS server.  There is a nice little program called dnsmasq that is lightweight, pretty easy to set up and very flexible.

Based on what you are saying about your problems I am pretty sure that there is a problem in your network settings of the kubuntu system.  If you are trying to connect to the server/router using ip address and you can connect with another computer, then something is wrong with your kubuntu local network settings.

---

### Post by WhimpyPeon on 2007-07-05
Whoops I meant to say:

One very nice feature is that they can pass on network settings through DHCP.

---

