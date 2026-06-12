---
title: "Remote Desktop and port forwarding"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by cartisdm on 2009-12-23
I am trying to set up an entire package that I can mail to my grandmother a few states away.  I want to be sure I can Remote Desktop in via vncviewer (or any graphical remote desktop if you know of a better one).

I know I need to set up port forwarding on port 5900 (I am mailing her this router too), but what else do I need to do?  How will I (or easily instruct her via the phone) obtain her IP address so I can connect in?


EDIT:  I've never used it before, but would it be easy to use something like Dynamic DNS from [www.no-ip.com?](www.no-ip.com?)

---

### Post by cgb on 2009-12-23
A lot of newer routers support dynamic dns in their setting so this would be ideal if you are sending a router out there.  Just setup the dynamic DNS prior to sending it out.  VNC is not very secure unless you are setting it up through SSH.  If the router supports VPN would help keep it more secure and connect via VPN and then VNC.  Otherwise you may wish to look at other options such as nxserver with private keys.

---

### Post by tenmilez on 2009-12-23
You can find your IP address by going to a place like ipchicken.com.

---

### Post by cartisdm on 2009-12-23
if I set up a Dynamic DNS on the router, will she or the technician run into any problems providing her internet?


EDIT:  > **tenmilez said:**
> You can find your IP address by going to a place like ipchicken.com.

I might just do this.  I don't have a problem pointing her to a website and having her read me her current IP address, this will be just fine.  I'm assuming that if I just set up port forwarding on this computer (port 5900) and I get her to give me the IP address, I can just get right in right?

---

### Post by HermanAB on 2009-12-23
Uhmmm, note that VNC is not secure and there are automated scripts out there that will have granny hacked in no time.  Search these forums a bit for tales of woe about VNC...

Rather use SSH.  It is easier to set up than VNC, can do more than VNC and it is secure.

---

### Post by Geoff918 on 2009-12-23
> **HermanAB said:**
> Uhmmm, note that VNC is not secure and there are automated scripts out there that will have granny hacked in no time.  Search these forums a bit for tales of woe about VNC...

Rather use SSH.  It is easier to set up than VNC, can do more than VNC and it is secure.

HermanAB is correct. You may want to follow a guide to port forward from SSH port 22 or something of the sort.

Here's a quick guide:

**[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)**

---

### Post by mapes12 on 2009-12-24
Hi

I used [Remote Help Assistant]("https://launchpad.net/remote-help-assistant") so that I could access my Dad's machine remotely. I signed up for a [DynDNS]("http://www.dyndns.com/") account (free) and configured my DynDNS URL to point to my routers dynamic IP address and set this into my router. Although my router (outside world) IP address is dynamic (it changes), my router has a set up utility within the admin area which automatically captures any new IP address assigned to it by my ISP and configures it to my DynDNS URL. Not sure if your router can do this but just mentioning it in case you can do the same.

It worked, with no need to ask my Dad for his IP address. He just needed to enter the URL I gave him into the Remote Help Assistant set up wizard and I could see and use his Desktop on my machine :P

---

### Post by terry_gardener on 2009-12-24
i would recommend gitso. 

you port forward your router set the you gitso to give support.

grandmother type in your ip address and and select get support and clicks start. 

thats it. 

you then have remote desktop to her computer. 

really easy to use and setup.

[http://code.google.com/p/gitso/]("http://code.google.com/p/gitso/")

---

