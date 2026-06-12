---
title: "ethernt connection"
date: 2005-07-21
forum: Networking &amp; Wireless
---

### Post by newbie_ubuntu on 2005-07-21
Hi,

having recently installed ubuntu, I really like the version a lot. But once in a while I run into problems and always I have found that this forum clears it up for me.

Here is one more...

My wireless is working fine, but I am unable to connect to the Wired Ethernet LAN in my office ( I use my laptop in the office). 

This is what I am doing right now. I deactivate the wireless from the network connections console. I then configure the ethernet connection to DHCP and activate it. I then choose the default as eth0 and click OK.
Everything goes fine.
But when i try to connect to the internet, I get the error "www.abc.com" cannot be found. Please check name and try again" in firefox.

Can someone tell me what to do? Is there anything I need to know from my office nework administration?

Thanks


When I try to connect to the LAN, the message "activa

---

### Post by rmjokers on 2005-07-21
There are a few things you might try to fix this problem.  You can run

ifconfig -a

to see if you are getting an IP address from your DHCP server.  If this is the case, then you should be able to ping your local gateway and other machines on your local network using their IP address.  If you can do this, then the problem is likely that DHCP server not getting you information about DNS servers.  This information is usually placed in

/etc/resolv.conf

If the ping fails, then there may be something wrong with your ethernet card configuration, port, or cable.  You might want to make sure the light is on and that the port is active.  Also look at log files for warnings or errors.

---

### Post by luca_linux on 2005-07-21
Also remember to set the gateway as well as DNS.

---

### Post by odin on 2005-07-22
Are you sure there's no proxy server in the place you are for accesing the internet?

If there is you have to configure it in tools->preferences->general->Lan conexions(dont trust me a lot with this but I think it is there,just look for preferences and then conexions or Lan conexions).

Ask your administrator for the proxy ip and port if you dont know them

---

