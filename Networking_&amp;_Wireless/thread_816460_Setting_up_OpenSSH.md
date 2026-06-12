---
title: "Setting up OpenSSH"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by the_real_fourthdimension on 2008-06-02
I have a question related more to port forwarding than Ubuntu itself, but I thought I'd post it here anyway.  I installed OpenSSH from the Ubuntu repositories.  I can login through it without any trouble when I use "ssh localhost", however, it doesn't respond when I use my local IP address:  "ssh 192.168.254.2".  I want to be able to access SSH from a PC outside my LAN, so I've tried to set up port forwarding for it on my seimens gigaset SE567 router, but I seem to be doing something wrong.  My inbound traffic rules table shows me that I have forwarded incoming TCP and UDP traffic on port 22 to my local IP address, 192.168.254.2.  However, after applying the changes and rebooting the router, nothing has changed.  I still get "connection refused" messages when trying to SSH into my PC using my public IP address and no response when I try to SSH into my PC using my local IP address.  ...I still can only use SSH with this command: "ssh localhost".  Can anyone tell me what I'm doing wrong  or what settings to change on my router?
Thanks.

---

### Post by SpaceTeddy on 2008-06-03
from where are you trying to log in ? are you still inside your network, or are you at a friends place and are trying it from there.

The reason i am asking this is because port-forwarding on these hardware router ONLY applies for requests that acctually are comming on the internet line. So, if you are still at home, you would be trying to ssh into your router, as it will not forward your request. 
The reason they do that is so people cannot lock themselves out. (imagine someone forwarding port 80 by accident. they'll never be able to load the configuration website again - ever)

hope it helps :)

---

### Post by the_real_fourthdimension on 2008-07-07
Thanks for the reply.  I tried accessing my machine from an outside network and got the same error message.  Everything seems to be configured correctly, though...  I've heard people say that they just couldn't port forward on this router.  Is that the case?

---

