---
title: "How To Share DNS On Internet Gateway"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by Dempsey on 2008-07-04
We've setup Ubuntu as an Internet Gateway running Squid and DansGuardian which works fine (when we use the proxy ports etc but thats another prob)

What I'm trying to do now if figure out how I can get the Ubuntu machine to work as a DNS server for the clients?  At the moment the clients can browse fine if I hard-code the ISP DNS in the clients, but I want to set the DNS the same as the Gateway IP, how can I do this?

The clients currently actually have internet access thru the gateway, as I can browse the internet via IP address' but not domain names.

The clients all have statuc IP address' and all the stuff I've read seems to say about setting DHCP on the gateway to dish out IP Address' and the DNS info, but is it possible to just dsitrbiute the DNS and leave the IP's set as static?

Any help would be greatly appreciated :)

---

### Post by SpaceTeddy on 2008-07-04
to answer the last question first - no. You can distribute IP's without a dns server, but you cannot distribute dns servers alone (at least not via dhcp). If a client has an ip address it will not query for a dhcp unless manually forced to give up it's ip configuration. 

As for the dns server in general - there are two ways to do this.

1.) use dnsmasq. This is a small tool which will only forward queries send to the server to it's own dns server. It cannot handle any dns-requests itself. So if you only need the forward, then use this tool.

2.) use bind. Ok, this is a full blown dns server which can do all the usual things... but if you need dns records for your own internal domain, want ddns in cooperation with your dhcp server or want a caching dns server (not sure if dnsmasq does that), you'll need to configure bind... 

hope it helps :)

---

### Post by Dempsey on 2008-07-04
Thanks SpaceTeddy, I'll try out dnsmasq, is there any certain config I'll need to setup or will it work as-is ?

---

### Post by SpaceTeddy on 2008-07-04
this was written on the top of my head. I haven't run dnsmasq myself yet (always used the full blown bind to do the job, as i usually need internal dns-resolution aswell. So, i can't really tell you the specifics on how to configure it. But by how i understand it, it should work with minimal to no configuration at all.

---

