---
title: "Remote User Login using XDMCP"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by madhatter563 on 2007-10-31
hello, 

Im trying to enable remote user login.  I went to the login window (oh btw im using 7.10), and made the remote login same as local.  I went to the XDMCP configuration,  I changed a port for my specific setup for the UDP port.  I also forwarded that port on the router.  

I connect with my "remote desktop" in windows vista, and get to the credentials screen (which means im connected) however no matter what i put in the credential box i cant log in.  Any ideas on how to go about getting this working?

---

### Post by timcredible on 2007-10-31
you say you did some port forwarding?  for xdm, you need udp 177 from client to server, then tcp 60xx open from server to client, where xx is the screen number you're using.  any idea what screen number vista is using?

---

