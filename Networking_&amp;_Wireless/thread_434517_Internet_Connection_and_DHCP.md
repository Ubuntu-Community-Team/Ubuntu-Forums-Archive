---
title: "Internet Connection and DHCP"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by Sulli on 2007-05-06
G'day

i have just setup and configured a Ubuntu 6.06 Server to serve DHCP. This serves its purpose by issuing leases fine to both an Ubuntu 6.10 box and XP. i have set up ranges and default gateways, pretty much most options in the dhcpd.conf file. i have also put in an option routers entry with my routers IP address

the issue is that my 6.10 box is able to use the default gateway to use the internet, however my xp machine can ping the default gateway, but wont connect to the internet

if it helps i have a dsl-g604t as my router adsl modem

Thanks 

Sulli

---

### Post by Soarer on 2007-05-06
It sounds like a DNS problem. In my experience (though I may be wrong) XP doesn't pick up the DNS server entry properly from a DHCP server on Linux.

I assume you have done "ipconfig /renew" on the XP box?

If so, try "ipconfig /all" to see what it thinks it's DNS server(s) are. If your router can do DNS forwarding (most can), you can explicitly set its IP address as the DNS server in XP and I suspect you will have to.

If your router doesn't forward DNS, you will need to put your ISP's DNS addresses in there.

HTH

---

### Post by Sulli on 2007-05-06
Thanks heaps Soarer

that fixed my issue, now the only question is do i need to use bind to make it happen automatically?

Is it even possible to make it work via DHCP? 

any other ideas regarding this would be great

Sulli

---

### Post by Soarer on 2007-05-06
I didn't get it to work - but then I didn't try too hard once I had it working. I just left it (it ain't broke...)

I am sure you could get it to work, if you wanted, and I'd be interested to know how you did it.

---

### Post by Sulli on 2007-05-08
Soarer,

Firstly when you mentioned it might be a DNS issue, i put my ISP's dns IP in to my alternate dns setting in the TCP/IP propeties of my XP machines nic. 

This made my Xp machine get the internet fine

Then i took a guess and set up BIND on my linux server by following the Ubuntu 6.06 setup guide.

Then i i just went exploring through the files in my bind folder and found a folder which i think was called "named.conf-options" in here i found a little entry called "IP Forwarding" in here i put my ISP's Primary DNS server IP.

Then renewed my ip on XP box and its all good now

Hope it helps you mate

Sulli

---

### Post by .rdg on 2007-05-08
Hi,

  as for bind (named) you should set it up to be just a caching named server. Try google for answers, but it should be something like this in your named.conf:

options {
    forwarders { Primary.DNS.IP; Secondary.DNS.IP };
}

(haven't checked bind on ubuntu yet, so ther might not be options clause in configuration file).

Hope this helps,
.rdg

---

### Post by Soarer on 2007-05-08
Thanks Sulli and .rdg.

I'll give it a try at the weekend - sounds like it should be good.

Best Regards.

---

### Post by subra on 2007-05-09
I have posted something on another thread. (Go to [http://ubuntuforums.org/showthread.php?t=437410](http://ubuntuforums.org/showthread.php?t=437410)) Might help.

---

