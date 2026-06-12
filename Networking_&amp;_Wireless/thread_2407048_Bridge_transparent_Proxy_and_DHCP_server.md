---
title: "Bridge transparent Proxy and DHCP server"
date: 2018-11-29
forum: Networking &amp; Wireless
---

### Post by niazwali on 2018-11-29
Hello Everyone,
I have a general type of question. I have DHCP server on the router and want to install a proxy server in the middle as shown in the diagram below. I want to know either my client will be able to get IPs from the router in this case. thanks in advance
[IMG]http://iamsrijit.files.wordpress.com/2012/11/netdiag.jpg?w=1024[/IMG]
Source: [http://srijit.com/how-to-setup-transparent-proxy-using-squid-and-ubuntu-server-12-04-in-bridged-mode/](http://srijit.com/how-to-setup-transparent-proxy-using-squid-and-ubuntu-server-12-04-in-bridged-mode/)

---

### Post by SeijiSensei on 2018-11-29
[http://manpages.ubuntu.com/manpages/xenial/man8/dhcp-helper.8.html](http://manpages.ubuntu.com/manpages/xenial/man8/dhcp-helper.8.html)

---

### Post by mitesh.agrwl on 2018-11-29
> **niazwali said:**
> Hello Everyone,
I have a general type of question. I have DHCP server on the router and want to install a proxy server in the middle as shown in the diagram below. I want to know either my client will be able to get IPs from the router in this case. thanks in advance


Yes, it will work with the correct configuration. In transparent mode, the IP address assigned to server is used for management purpose, it does not participate in routing, hence, there is no need of dhcp-helper (DHCP relay) as suggested in previous reply. DHCP relay is used to  acquire IP address when DHCP server is not in same network. In transparent mode, the network does not change, it remains same. 

With transparent proxy servers, there is no need to provide proxy configurations to browser/applications, users are not aware of its presence! The configuration from the image source are old but the method is same.

---

### Post by niazwali on 2018-11-30
Thanks **[mitesh.agrwl]("https://ubuntuforums.org/member.php?u=2111225"), **I think, I should try it first virtually. I am using mikrotik with multiple pools and I am assigning QOS to the clients based on the specific pool. As you know mikrotik lack the capabilities to generate web surfing reports like **squid** or '**Web Safety**' can do, so I want the DHCP, Load-balancing and QOS part to be performed by the Mikrotik and for proxy purpose I want to install squid in the middle as was shown previously.

---

### Post by mitesh.agrwl on 2018-11-30
> I am using mikrotik with multiple pools

As you are using multiple pools and the proxy will be there to serve all the pools, using proxy in transparent mode is not a good idea. Proxy should be used in routed mode and in that situation the DHCP relay (dhcp-helper) as suggested by [**[COLOR=#000000]SeijiSensei[/COLOR]**[COLOR=#000000][/COLOR]]("https://ubuntuforums.org/member.php?u=698195") is the right way to implement it, considering there are multiple VLANs to support multiple pools. 

If your main concern is security along with monitoring, an [open source firewall ]("https://geekflare.com/best-open-source-firewall/")is another option you might want to explore.

---

