---
title: "How to disable DHCLIENT retry-once (-1 flag) on ifup?"
date: 2015-11-12
forum: Networking &amp; Wireless
---

### Post by gerard12 on 2015-11-12
Hi,

We have a server which is using DHCP for getting the WAN ip address from the provider. The provider has made a fixed IP entry in his DHCP-server with our MAC but we have to use DHCP client to "renew" the address. Everything works fine, except...

If the provider is doing some maintenance during the night and his server is down, our dhclient is exiting because it fails renewing the IP and so the WAN interface is going down. I found already that this is because of the -1 flag which is used to start dhclient and which is setting the tryonce flag internal of the dhclient. If I'm correctly then this -1 flag is hard coded in the "ifup" binary. 

How can I suppress this  -1 flag???

The workaround of making dhclient a script and renaming the binary to dhclient-bin is working but at every ifdown/ifup you and up with an additional dhclient process. 

Thanks

---

