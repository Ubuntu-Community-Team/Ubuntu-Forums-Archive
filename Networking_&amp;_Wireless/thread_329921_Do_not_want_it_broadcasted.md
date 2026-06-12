---
title: "Do not want it broadcasted"
date: 2007-01-02
forum: Networking &amp; Wireless
---

### Post by wireddad on 2007-01-02
I would like to disable the wireless router broadcasting.  Where do I configure this in Ubuntu?  I know that I need to put the router name somewhere but do not know where.  Thanks.

---

### Post by jr.gotti on 2007-01-02
You have do this this from within the router...

Open up firefox and put in the IP address of the router. In my case it is 192.168.1.1.

From there enter your password and then disable wireless broadcasting.

---

### Post by wireddad on 2007-01-02
Yes.  But where within Ubuntu do I configure to connect to the router by name?

---

### Post by psycho78 on 2007-01-02
?? you have to know the ip adress, or the router must have a kind of nameserver build in. E.g. my fritz box can be reached from every machine that it is connected to via web browser just by typing in:  fritz.box
alternatively you can use the routers ip adress (if it's a new one or you never changed it, you can look it up in your handbook or on the website of the manufacturer.... and if you know how to use nmap you could also make a pingscan to find out which ip's are online in your net.... one of them must be the router... :)

---

### Post by bgoody on 2007-01-02
Hi.  Use your web browser to talk to the router.  Enter [http://192.168.1.1](http://192.168.1.1). in the location bar at the top (where website names are usually displayed).

It will probably ask you for a username and password.  As you haven't done that before the username is probably blank(empty) and the password for Linksys routers is usually "admin" without the quotes.

Brian

---

### Post by wireddad on 2007-01-02
Apparently I have not been very clear, once I have turned off the SSID broadcasting, where in the Ubuntu network configuration do I input either the IP address or the router name?  I will have to tell the wireless card where to connect since it will not be broadcasted anymore.  As in windows this can be done for further security. 
Hope I have made it a little clearer of what I am trying to do.  Thanks for helping.

---

### Post by wireddad on 2007-01-14
Just trying to see...

---

### Post by katabatic on 2007-01-14
You need to put in the SSID in the program that is managing your wifi.

---

### Post by wireddad on 2007-01-14
By default in Kubuntu, what program manages wifi?

---

