---
title: "[HELP!] 8.04 as VM on Windows DNS issue"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by paulsjv on 2008-05-21
I'm running 8.04 as a vm on my work windows box.  My problem is when I try to get to any internal web sites or servers (i.e. [http://server1](http://server1) or ssh username@server1 ) doesn't work.  My guess is that it is an DNS issue and for some reason the route to internal servers on the company network are not being found.  Any ideas to how to get around this?

---

### Post by Fire_Chief on 2008-05-21
It depends on what you set for the nameservers in your /etc/resolv.conf file in Ubuntu (also configurable via the network control panel). You should be able to specify the DNS servers you wish to query against. Also, you may need to specify the FQDN of the server you are trying to reach so Ubuntu will query the DNS properly.

Cheers!

---

### Post by paulsjv on 2008-05-21
FQDN?  You lost me there. ;)

Below is what my /etc/resolv.conf looks like:

search localdomain
nameserver 192.168.254.2
nameserver 10.34.22.18

I'm not sure if this is right or not (I'm assuming it isn't since things still don't work).  On my windows box I did ipconfig /all to get the DNS server.  What else should I do? 

(Sorry I'm a noob at all this networking stuff so thanks for the help!)

---

### Post by superprash2003 on 2008-05-21
does it work when you do [http://x.x.x.x](http://x.x.x.x) where x.x.x.x is the local ip of the internal website?

---

### Post by Fire_Chief on 2008-05-21
> **paulsjv said:**
> FQDN?  You lost me there. ;)

Below is what my /etc/resolv.conf looks like:

search localdomain
nameserver 192.168.254.2
nameserver 10.34.22.18

I'm not sure if this is right or not (I'm assuming it isn't since things still don't work).  On my windows box I did ipconfig /all to get the DNS server.  What else should I do? 

(Sorry I'm a noob at all this networking stuff so thanks for the help!)

FQDN is Fully Qualified Domain Name and looks like server1.mywindowsdomain.local versus just server1

Do the DNS servers from Windows match the ones in your resolv.conf?

Oh, just to cover all the bases, can you get to the Internet from Ubuntu (inside the VM)?

Cheers!

---

### Post by paulsjv on 2008-05-21
yep works perfectly if I put in the ip address like [http://x.x.x.x](http://x.x.x.x)

---

### Post by paulsjv on 2008-05-21
> **Fire_Chief said:**
> FQDN is Fully Qualified Domain Name and looks like server1.mywindowsdomain.local versus just server1

Do the DNS servers from Windows match the ones in your resolv.conf?

Oh, just to cover all the bases, can you get to the Internet from Ubuntu (inside the VM)?

Cheers!

From what I can tell when I run ipconfig /all on my windows box I get 2 DNS servers: 

10.34.22.18
192.168.1.215

On my Ubuntu vm my /etc/resolv.conf looks like:

search localdomain
nameserver 192.168.254.2
nameserver 10.34.22.18

Do I need to restart or something after I make the change to the file?

I can get to the internet just fine through my Ubuntu vm just not on local sites at my company without the FQDN, which is really annoying since I don't know what the FQDN is (it's my 2nd week on the job).

---

### Post by paulsjv on 2008-05-21
Side note.

It seems that every time I edit the /etc/resolv.conf something is removing my dns entry of 10.34.22.18. hm.

---

### Post by Fire_Chief on 2008-05-21
> **paulsjv said:**
> Side note.

It seems that every time I edit the /etc/resolv.conf something is removing my dns entry of 10.34.22.18. hm.

Probably NetworkManager making changes. Try changing/adding the DNS server through the administrative tool in the System menu. You can also add the local domain name there if you like.

The domain name can be found from your ipconfig /all on Windows. It should show the **connection specific DNS suffix**. That is the domain name you want to use.

Cheers!

---

### Post by paulsjv on 2008-05-21
This is pretty weird but when I add the settings through Network Manager and restart the Ubuntu VM it clears out the settings I put in.  Any thoughts?

---

### Post by Fire_Chief on 2008-05-21
Are you using DHCP or did you assign a static IP for your network connection? NetworkManager with DHCP will probably overwrite your resolv.conf every time the network changes.

---

### Post by superprash2003 on 2008-05-21
try changing those DNS servers in resolv.conf to opendns servers and then try accessing your local website

---

### Post by paulsjv on 2008-05-22
> **Fire_Chief said:**
> Are you using DHCP or did you assign a static IP for your network connection? NetworkManager with DHCP will probably overwrite your resolv.conf every time the network changes.

It's DHCP.  I tried to set up a static ip but I can't figure out what the default gateway is.  Is there anything else I should do to get this to work?

---

### Post by paulsjv on 2008-05-22
> **superprash2003 said:**
> try changing those DNS servers in resolv.conf to opendns servers and then try accessing your local website

opendns servers?

---

### Post by paulsjv on 2008-05-22
*bump*

---

### Post by superprash2003 on 2008-05-22
[http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Fire_Chief on 2008-05-23
Superprash, you missed the objective of this thread. Paulsjv is trying to connect to servers by name on his local Windows network...not connect to Internet websites. Using OpenDNS servers would not help meet this goal.

Paulsjv, what VM software are you running Ubuntu in? There may be settings adjustments you can make there to help correct the problem.

---

