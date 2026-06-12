---
title: "I'm the victim of ISA proxy as well. Please help..."
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by Roswell on 2007-10-27
Hello All,

Please please help me

I installed Ubuntu 7.10 64 bit edition. run smoothly however I one issue pain in my ***

I'm behind Microsoft isa proxy with authentication. My computer is not on the domain however have to have the user and password for browsing. Also my computer name should be the specific provided by the network administrator anyhow

You know Synaptic ;) ... 

407 Proxy Authentication Required (ISA Server Requires authentication...)

firefox works well. can access the repositories through firefox...

have done enough searching and now i'm goin gto be freaked out by this.

I have done the acquire thingy and tried every possible combinations such as 

[http://proxyaddress:theport](http://proxyaddress:theport)
or
[http://user:pass@proxyaddress:theport](http://user:pass@proxyaddress:theport)

and have created files in 
/etc/apt/apt.conf and
/etc/apt/apt.conf.d/01proxy
/etc/apt/apt.conf.d/00proxy 

/etc/apt/apt.conf.d/proxy

but none of the above worked for me. I have also tried export command on shell but it didn't work either. 
Have done tricking with disabling and enablign proxy in System>Network proxy and in synaptic with both authentication and without authentication but it didn't work !!
I'm just freaking out please help me. 
Please do not refer me to the old posts because I have also tried ntlm but it didn't work for me either. I'm not on a domain, but on workgroup. My network card is setup on DHCP

Regards,

---

### Post by Roswell on 2007-10-27
I'm in need. please help :(:(

---

### Post by Roswell on 2007-10-27
someone refer me this one

[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)

but as I said I already treid it so it did not work for me.

anyone?

---

