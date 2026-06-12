---
title: "Dansguardian - Forcing internet traffic through proxy"
date: 2015-03-19
forum: Networking &amp; Wireless
---

### Post by heebiejeebies2 on 2015-03-19
Hi all, I've almost got Dansguardian working on Ubuntu 14.04.   It  filters everything correctly as long as I force Mozilla to use the   proxy using Mozilla's own connection settings.  However, all the user  has to do is  disable the proxy in Mozilla and Internet access becomes  unfiltered.  So I  need a way to apply a system wide proxy that actually  works (the network  control panel proxy is ignored by Mozilla), or I  need to be able to  disable all HTTP & HTTPS traffic that does not  go through the proxy, thus forcing the user to use the proxy or get no  internet connection.   Any suggestions? Thanks

---

### Post by TheFu on 2015-03-19
Don't allow a default route to the internet from any client workstations.  Only the DG server should have a route to the internet.
Next, you want to setup the proxy as a "transparent proxy" ... [http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html](http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html)

Basically, the server becomes the router for all client workstations and they don't connect to the real router directly.

I'd block internet DNS from the client workstations too - there are reasons.

---

### Post by heebiejeebies2 on 2015-03-19
Thanks - maybe I should have explained better: this is only one computer.  The DG server and the Tinyproxy server are on the same computer.  I considered transparent mode but various tutorials tell me that stops HTTPS from working or something.

---

### Post by TheFu on 2015-03-19
a) I don't know anything about trying this on a single computer.
b) if you don't want to force a proxy setting to be required, then a transparent proxy is the only method. Well ....  or you could try making a PAC file that browsers should see and use on a webserver provided with the DHCP stuff. It has been 8 yrs since I set anything like this up.

---

### Post by heebiejeebies2 on 2015-03-19
Various tutorials that I've read have suggested port redirection in IPtables, to force all web traffic to redirect to the DG port.  But so far none of them have worked; they've just caused all sites to stop loading.  I was hoping someone could suggest a simple IPtables command that works.

---

### Post by heebiejeebies2 on 2015-03-19
> **TheFu said:**
> 
b) if you don't want to force a proxy setting to be required, then a transparent proxy is the only method. 

Also, in response to this: I don't mind if I do have to force a proxy setting to be required.  Just as long as there's no way out of the filter.

---

### Post by TheFu on 2015-03-19
Don't know how to do it on a single machine. Could you use a virtual machine as the proxy? Just thinking out loud.

---

