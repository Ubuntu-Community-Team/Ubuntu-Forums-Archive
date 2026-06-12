---
title: "Wireless Router and DansGuardian"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by kvapster on 2011-03-17
Hi,

My school has new internet coming via DSL currently with a wireless router. It cannot be used unless until there is a filter to comply with the Federal CIPA. So, I have acquainted myself with Ubuntu and DansGuardian! So far, I have a 9.04 Ubuntu machine with DG, tinyproxy, and firehol working filtering all browsers. Very Nice. 

How do I set up the network so that all the web request from the wireless computers go through the filter on the Ubuntu machine? I have a Belkin wireless, router, dhcp all in one. 

I will continue to scour the forums, but so far I am struggling...so any direction or assistance will be useful!

---

### Post by dryicebomb on 2011-03-17
You might want to try and change the default gateway in the dchp scope to point to your filtering machine. It might not be possible on that router, if not then you might want to setup your filter machine to also handle dchp on your network using dhcp3-server.

---

### Post by kvapster on 2011-03-17
On my Belkin wireless router-How about Fire wall> Virtual Servers? Supposedly it will "route external internet calls for services or other applications through your router to your internal network."

I think this can function as port forwarding...

I need to provide a private IP address(IP of the Ubuntu Box?) and private port(3328 or 8080?) and inbound port(Not sure...the same as the private port?) 

> **dryicebomb said:**
> You might want to try and change the default gateway in the dchp scope to point to your filtering machine. It might not be possible on that router, if not then you might want to setup your filter machine to also handle dchp on your network using dhcp3-server.

---

### Post by dryicebomb on 2011-03-17
Port forwarding allows devices outside of the network to access devices on the private network. If I understand your question correctly all of the computers that you want to connect to the proxy/filter are going to be on the same private network. There are a couple of ways that you can solve this. 
1. You can change the default gateway of all the pcs on the lan (either through DHCP if the network uses DHCP, or by manually configuring them) and setup iptables rules to intercept all web traffic and redirect it to the proxy. Check this link for a little more information. [http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html](http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html)
2. you can go into the browser preferances and manually set the proxy information on each computer. On internet explorer these settings are under tools, internet options, lan settings. Just put in the local ip of the filter and the port that it is listening on. One potential problem with this easy solution is that kids are pretty smart and some might figure out how to go into the settings and turn this off.

Also check out this link
[http://www.howtoforge.com/dansguardian-content-filtering-with-transparent-proxy-on-ubuntu-9.10-karmic](http://www.howtoforge.com/dansguardian-content-filtering-with-transparent-proxy-on-ubuntu-9.10-karmic)

I hope this helps.

---

### Post by kvapster on 2011-03-18
> **dryicebomb said:**
> Port forwarding allows devices outside of the network to access devices on the private network. If I understand your question correctly all of the computers that you want to connect to the proxy/filter are going to be on the same private network. There are a couple of ways that you can solve this. 
1. You can change the default gateway of all the pcs on the lan (either through DHCP if the network uses DHCP, or by manually configuring them) and setup iptables rules to intercept all web traffic and redirect it to the proxy. Check this link for a little more information. [http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html](http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html)
2. you can go into the browser preferances and manually set the proxy information on each computer. On internet explorer these settings are under tools, internet options, lan settings. Just put in the local ip of the filter and the port that it is listening on. One potential problem with this easy solution is that kids are pretty smart and some might figure out how to go into the settings and turn this off.

Also check out this link
[http://www.howtoforge.com/dansguardian-content-filtering-with-transparent-proxy-on-ubuntu-9.10-karmic](http://www.howtoforge.com/dansguardian-content-filtering-with-transparent-proxy-on-ubuntu-9.10-karmic)

I hope this helps.


Does the physical setup need to be changed? Current setup is:

Modem->Wless DHCP Rtr(192.168.2.1)->U-Box(192.168.2.9)

Yes. I would like wireless devices(iPads and Windows XP/7) to get filtered internet from the router on a private network. I am setting up another U-Box according to your second link provided.
I can add another ethernet card if needed...

---

