---
title: "Help --- New Web Server - Beginner"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by sundesh on 2011-05-10
I am very new to Ubuntu. 
I have installed Ubuntu Server 10.10 with LAMP etc to setup a web server. I have installed Webmin BIND9 and ddclient to update my ip address with DynDns.  I have two addresses with DynDns pointing to the same IP (one uses ddclient and the other is configured on my router)

I have thus far configured my router to forward https (Port 443) to my server and I have enabled DMZ Host on my router. I can now access my server via Webmin from anywhere using [https://***1.dyndns.org:10000](https://***1.dyndns.org:10000) or [https://***2.dyndns.org:10000](https://***2.dyndns.org:10000)

I need help setting up BIND9 as an active DNS Server to registras. I need to supply the registra with two name server hosts.  

I also need help setting up the webserver to host websites.

All will be running on one machine. This is not for commercial use. Just for family use so i would also like to put in a nice user interface similiar to what web hosting companies use.

I have no idea where to start. Please help.:confused::confused::confused:

---

### Post by Locke_99GS on 2011-05-10
I'm not understanding why your situation requires messing with BIN, unless you're wanting to direct subdomains to different hosts for multiple family members, perhaps. Will dyndns even pass this?

Configure apache with WebMin for however you want it, since you have that installed. Since your DMZ'd the server, there shouldn't really be much to set up. It should be serving the apache test site right now. If you did want to bind subdomains to different hosts, set the virtual hosts up first in WebMin, then configure bind to direct to them.

I'd recommend using UserMin for your family to access, and keep the WebMin access to yourself.

---

### Post by sundesh on 2011-05-10
Thanks for respone

Yes correct, if i put in my dyndns address into a browser it is currently accessing the apache test site.

Please excuse my ignorance on this part

I want to be able to supply a registra with two dns address for multiple domains. do i give them the two dyndns address?
How do I configure my server to host these multiple domains?

This is the first time im using ubuntu and the the first time im setting up a webserver. I have searched the internet but i can't find a simple howto manual to setup the above. Im basically looking for step by step instructions just on the dns configuration

---

