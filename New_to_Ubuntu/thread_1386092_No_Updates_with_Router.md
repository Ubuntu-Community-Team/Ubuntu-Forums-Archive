---
title: "No Updates with Router"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by Joe Moren on 2010-01-20
UpDate problem- Update Manager won't connect with router in use. Must remove Router to get updates.

Computer> Router> DSL Modem> (wired) No Updates but can browse "most" url's. Laptop (Ubuntu)connected via wireless works OK for Updates & all url's. Could 'not' post this new thread!

Computer> DSL Modem> Updates OK & can browse all url's I've tried.
Same conditions with previous Ubuntu versions.

Ubuntu 9.10
emachine T3990, 2.8 Ghz
DI-524, Wireless Router 
2Wire Modem, Juno DSL
Google & Forums have not helped toward a solution, grateful for any help! Joe

---

### Post by Grenage on 2010-01-20
I would check the router's config.  It sounds like it might have DNS issues, so try manually specifying some different addresses.

Google's for testing should be fine (think they might be 8.8.8.8 + 8.8.4.4)

---

### Post by caravel on 2010-01-20
In the OS set the IP address of your router as the primary DNS server.

---

### Post by lyall on 2010-01-20
how you reboot your router and DSL modem lately.
It can be a problem sometimes.
it is a place to start

are you using DHCP on your router?

I am and my ip address for the router is 192.168.2.1
all computers, network printer, etc on your network should use 192.168.2.x
I also have to hubs one 8 port and one 4 port
and all are using the 192.168.2.x

I hope this helps a little

good luck and have fun learning

---

### Post by Joe Moren on 2010-01-20
Thanks for the replies. Networking has always been "smoke & mirrors" for me! caravel, I'm not sure how to set the IP address of my router as the primary DNS server. Thanks, Joe

---

### Post by Grenage on 2010-01-20
Most common setting is for a computer to get it's settings from the router via DHCP, that includes IP, DNS and Gateway.  Rather than setting things manually on the computers, just log into the router via it's web interface and look for DNS settings.  Try Google's DNS addresses in there, see if it helps.

---

### Post by synapsys on 2010-01-20
> **Grenage said:**
> 
Google's for testing should be fine (think they might be 8.8.8.8 + 8.8.4.4)

Just remember, Google likes to keep records of EVERYTHING.....

And they have no problem handing over those records to law enforcement.

---

### Post by lyall on 2010-01-20
you can reset the router to factory defaults
by pushing the the reset button on the router.
it should set the router back to DHCP

you can also go to the manufactory's web site and they should a manual that you can download for your router.

by doing this you will have to redo the Security for your wireless
You also want set the Security back for your wireless by setting a password for it.  To got your wireless laptop back on you will prompted for the password.

I friend of mine do not, and somebody download some movies or some thing illegally thru their wireless and got cought and blamed for it.  Now they can not got internet services (black listed). 

read the following link about wireless Security
[http://compnetworking.about.com/od/wirelesssecurity/tp/wifisecurity.htm]("http://compnetworking.about.com/od/wirelesssecurity/tp/wifisecurity.htm")

also see the following link for networking
[http://ubuntuguide.org/wiki/Ubuntu:Karmic]("http://ubuntuguide.org/wiki/Ubuntu:Karmic")

good luck and have fun learning

---

### Post by Grenage on 2010-01-20
> **synapsys said:**
> Just remember, Google likes to keep records of EVERYTHING.....

And they have no problem handing over those records to law enforcement.

Aye, but then again so do pretty much all ISPs; still, I will restate:

Unless you're a bomb-building paedophile, test your DNS by using Google's DNS addresses.

---

### Post by synapsys on 2010-01-20
> **Grenage said:**
> 
Unless you're a bomb-building paedophile, test your DNS by using Google's DNS addresses.

Wow so everybody that doesn't want big brother watching their every move is a bomb-building pedophile? News to me....

Anyways, you should all be using OpenDNS [http://www.opendns.com]("http://www.opendns.com/") 

@OP All of your computers connected to a router will have a default DNS of the router's IP address. Your DNS addresses are set in the router's configuration page. You will need to open up a web browser and log in to your router to change DNS settings. 

The way to do this varies from router to router, so **google** your routers model number for further instructions.

If you're worried about privacy, use **scroogle** [https://ssl.scroogle.org]("https://ssl.scroogle.org/")

---

### Post by Grenage on 2010-01-21
> Wow so everybody that doesn't want big brother watching their every move is a bomb-building pedophile? News to me....

I was being sarcastic.

---

### Post by Joe Moren on 2010-01-31
Hi, Solved! Finally got access to another D-Link router which helped to solve the problem!
The older router failed & would not connect, ie. 'status light stayed unlit'. Cables may have been 'Hot' plugged too many times! Thanks for all the responses, Joe

---

