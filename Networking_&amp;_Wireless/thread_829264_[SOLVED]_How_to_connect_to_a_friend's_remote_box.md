---
title: "[SOLVED] How to connect to a friend's remote box"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by IanB2 on 2008-06-14
I've been using Remote Desktop Viewer successfully on my local LAN but now would like to be able to connect to a friend's Ubuntu box so I can provide them with help when they get stuck. They are using a Netgear router (which I configured) and have a dynamic IP address which makes things interesting!

I've been Googling for some time trying to find a 'how to' create a remote connection as I'm unfamiliar with how to do this and some of the terminology I'm stuggling with!

Can anyone help please? GUI tools would be nice as I'm relatively new to Linux. Thanks!

---

### Post by lswb on 2008-06-14
How is the netgear router connected to the internet? If through a DSL modem, the provider generally will have available 1 or 2 global, statically assigned IP addresses that the DSL modem uses to connect to the local network to the internet. The router and 1 computer on the local net are then configured so that the global IP address is used by the computer. This will generally required accessing the configuration settings of both the modem and the router. THe details of doing so will vary with the service provider and make and model of the modem and router.

If the ISP does not make a static global IP address available for your friends local network, it will have to be determined by other means. There are some ways of doing this. 

By global here, I mean an the IP address that the DSL modem or router is using to connect to the internet at large. This will NOT be an address in the 192.168.xxx.xxx range that are reserved for local network use only and are usually assigned by the dhcp server built into the router.

---

### Post by superprash2003 on 2008-06-14
something similar to what you wanted [http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html](http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html)

---

### Post by IanB2 on 2008-06-15
> **superprash2003 said:**
> something similar to what you wanted [http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html](http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html)

Thanks ..... looks fairly simple so I'll give this a try.

Just out of curiosity, how secure is a connection of this type? How much data could a malicious person intercept?

---

### Post by IanB2 on 2008-06-16
> **IanB2 said:**
> Thanks ..... looks fairly simple so I'll give this a try.

Just out of curiosity, how secure is a connection of this type? How much data could a malicious person intercept?

Once I'd figured out how to set up my router all was plain sailing ..... fantastic.

The Remote Desktop Preferences tool in the Preferences menu in Ubuntu allows you to select encryption on the advanced tab. Plus you can change the default port number and if you specify a single IP address in your router then I guess you have a pretty secure connection.

---

