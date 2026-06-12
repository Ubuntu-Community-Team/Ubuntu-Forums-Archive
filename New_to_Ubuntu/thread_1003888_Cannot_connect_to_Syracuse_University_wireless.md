---
title: "Cannot connect to Syracuse University wireless"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by tegnoto89 on 2008-12-06
I just installed ubuntu, and the help page SU internet provides says the following:

There is no official support for configuring linux ...
The latest Ubuntu and other distributions appear to work well out of the box with the exception of specifying the auth servers.
... if you get the supplicant compiled on other versions, here are the fundamental settings.

    * WPA-1 protocol (WPA).
    * TKIP session encryption.
    * PEAP authentication type.
    * MSCHAPv2 password encryption.
    * AuthServers secure1.syr.edu;secure2.syr.edu; 

These settings are NOT required for AirOrangeX and can be ignored:

    * Anonymous Identity
    * Client Certificate File
    * CA Certificate File
    * Private Key File
    * Private Key Password 

So I applied all these settings (except the authserver and TKIP session encryption, I don't know how to do those), and it starts connecting, then asks me for authentication OVER and OVER.  It's very annoying.

What do I do to fix this?  Any help would be really appreciated!  (Note: I'm a complete n00b to linux so go easy on me with the computer jargon)

---

### Post by jbrown96 on 2008-12-06
Not sure how you're going about connecting, but you should use the "connect to 802.1x network"

---

