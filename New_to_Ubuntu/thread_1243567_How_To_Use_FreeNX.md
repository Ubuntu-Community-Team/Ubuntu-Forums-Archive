---
title: "How To Use FreeNX"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by mapes12 on 2009-08-18
I've managed to _install_ FreeNX. I've got that part figured out by following [this]("https://help.ubuntu.com/community/FreeNX"). The Server and client packages are installed on the respective Ubu boxes which are some miles away from each other. I need to connect over the internet but what do I enter in all the configuration boxes. All the guides I can find via Google are about installing the server and client applications, then...........stop!

What goes in the configuration boxes please??

TIA.

Mark

---

### Post by cgb on 2009-08-18
If you are talking about the configuration boxes for the client, then basically all you really need to specify is the Host name or IP address of the server you are connecting to and what Desktop environment which I would assume for you would be Unix and Gnome.  Everything else the default setting should be fine.

---

### Post by mapes12 on 2009-08-18
> **cgb said:**
> If you are talking about the configuration boxes for the client, then basically all you really need to specify is the Host name or IP address of the server you are connecting to and what Desktop environment which I would assume for you would be Unix and Gnome.  Everything else the default setting should be fine.Thank you. 

How does the host name or IP address (which is a private LAN address behind a router) manage to get from the client to the server over the internet and where private IP addresses (class C starting 192 in my case) of the same number will be everywhere behind other network LAN's?

I also found this on the forum: [http://ubuntuforums.org/showthread.php?t=467219](http://ubuntuforums.org/showthread.php?t=467219) but I would need to be a CL wizard to understand it (which I'm not).

---

### Post by cgb on 2009-08-18
Well you would enter your WAN IP address or WAN hostname if you have one.  Configuration will need to be made on the Router to forward port 22 to your appropriate internal IP address or you could setup a VPN connection to connect to your private network and use your internal address with the NX client.

---

### Post by Baneblade on 2009-08-18
> **mapes12 said:**
> Thank you. 

How does the host name or IP address (which is a private LAN address behind a router) manage to get from the client to the server over the internet and where private IP addresses (class C starting 192 in my case) of the same number will be everywhere behind other network LAN's?

FreeNX runs on a custom version of SSH, so you will need to **forward TCP port 22** from your router to the machines you wish to access remotely.

Please see [this thread]("http://ubuntuforums.org/showthread.php?t=839048") about logging into an already running session as i know i had trouble finding that to begin with too.

Hope that helps?

---

### Post by mapes12 on 2009-08-18
> **cgb said:**
> Well you would enter your WAN IP address or WAN hostname if you have one.  Configuration will need to be made on the Router to forward port 22 to your appropriate internal IP address or you could setup a VPN connection to connect to your private network and use your internal address with the NX client.Thank you.

I can find out my WAN i.e. ISP assigned address here: [http://whatismyipaddress.com/](http://whatismyipaddress.com/)

You mention > Configuration will need to be made on the RouterDoes that mean I have to go into the admin section of my router with my browser and change some of the settings please? And which router, client or server?

---

### Post by cgb on 2009-08-18
Yes, you will need to go into the admin mode by logging into the Router via the IP address entered into your browser locally.  This change would need to be made on the Servers router and not the clients.

---

### Post by mapes12 on 2009-08-18
> FreeNX runs on a custom version of SSH, so you will need to forward TCP port 22 from your router to the machines you wish to access remotely.Thank you.

How do you do this please?

---

### Post by Baneblade on 2009-08-18
Mapes just log into your router via a web browser and under the Port Forwarding section enter your internal IP (you may need to assign your server a static IP if your router doesnt support doing it by MAC address).

If you are not sure how to do anything above, find out the make and model of your router and go to [portforward.com]("http://portforward.com/")

---

### Post by cgb on 2009-08-18
This depends on your Router.  Once logged into your Servers Router you will need to look for a section called Port Forwarding and create a new entry with the nxServer's IP address and port 22 listed.

---

### Post by mapes12 on 2009-08-18
Thanks Guys. I think I'm getting some of this.

So, I login to the admin section of the servers router, find the port forwarding menu, enter the internal IP of the server machine and make sure port 22 is forwarded by TCP. Right? (The FreeNX guide made no mention of reconfiguring routers :confused:)

Then what do I enter in the client machine configuration boxes to connect to the server machine please? Sorry to appear to be a numbskull #-o

---

### Post by Baneblade on 2009-08-18
> **mapes12 said:**
> Thanks Guys. I think I'm getting some of this.

So, I login to the admin section of the servers router, find the port forwarding menu, enter the internal IP of the server machine and make sure port 22 is forwarded by TCP. Right? (The FreeNX guide made no mention of reconfiguring routers :confused:)

Then what do I enter in the client machine configuration boxes to connect to the server machine please? Sorry to appear to be a numbskull #-o

Yeah mate, just make sure that TCP port 22 (SSH default) is forwarded to your server. Then to connect to your server from outside your local network (ie: over the internet) you would just enter your external IP address (the one assigned by your ISP - google "what is my IP" if you dont know it) followed by " :22 " (indicates port 22)

So an eg. would be: 123.123.123.123:22
That will allow you to connect now.
In future though your ISP will rotate your external IP on a regular basis (unless you are with BeThere or paid extra for a static IP?) so you will need to use a service such as DynDNS to update your IP, otherwise you will have to check it everyday to ensure that you still have the correct value.

---

### Post by mapes12 on 2009-08-18
Thank you.

> just make sure that TCP port 22 (SSH default) is forwarded to your serverOn the servers router, right?

> Then to connect to your server from outside your local network (ie: over the internet) you would just enter your external IP address (the one assigned by your ISP - google "what is my IP" if you dont know it) followed by " :22 " (indicates port 22)

So an eg. would be: 123.123.123.123:22So, this is the IP address assigned to the servers LAN by the servers ISP that I enter into the client configuration, right?

---

### Post by Baneblade on 2009-08-18
Yes and yes.
Give it a go, and let me know if you run into any problems ;)

---

### Post by mapes12 on 2009-08-18
> **Baneblade said:**
> Yes and yes.
Give it a go, and let me know if you run into any problems ;)Thank you.

> In future though your ISP will rotate your external IP on a regular basis (unless you are with BeThere or paid extra for a static IP?) so you will need to use a service such as DynDNS to update your IP, otherwise you will have to check it everyday to ensure that you still have the correct value.Yep, I think my ISP rotates the external address so I would need the DynDNS service. I've been to the site and had a read through the intro stuff. I guess that it would need to be the server side assigned to the DynDNS account for the DynDNS alias? and if so would I have to enter into the client something like "mydns.ath.cx:22" or would the port already be recognised?

---

### Post by cgb on 2009-08-18
yes, setup the DynDNS account on the server side.  Then you will enter the DynDNS name instead of IP address in the Host Name field and port 22 is the default so most likely wont be required to be entered.  Atleast the Nomachine NX client I use does not require it.

---

### Post by Baneblade on 2009-08-18
Its just the same as you would have done before i believe. Simply replace the IP with the DynDNS Alias. 
(Making sure that you have the update-client running on the server side to keep the IP current for DynDNS to work)

So        123.123.123.123:22
becomes:  DNYDNSALIAS:22

---

### Post by mapes12 on 2009-08-18
Thank you very much Guys.

I have registered my DynDNS account and got myself a DNS address to manage the assignment of class B addresses from my ISP.

I'll need to give all this a go once I can get to the server machine in a few days. 

Just to come back to the original point of my thread i.e. mountains of info on the web/forums to install FreeNX but then the uninitiated hasn't a clue what to do next. Once I get this working I can feel a HowTo coming on.............

Best wishes for now and thanks again.

Mark :guitar:

---

