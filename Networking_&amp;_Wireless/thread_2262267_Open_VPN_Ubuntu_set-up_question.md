---
title: "Open VPN Ubuntu set-up question"
date: 2015-01-23
forum: Networking &amp; Wireless
---

### Post by Stan_1936 on 2015-01-23
I am trying to set up Open VPN using the guide here:
[https://help.ubuntu.com/lts/serverguide/openvpn.html](https://help.ubuntu.com/lts/serverguide/openvpn.html)

The keys and certificates are provided to me so I simply need to set up the client Ubuntu 14.04.1 (32-bit) machines. In the Simple Client Configuration section of this guide, we start by installing openvn and copying over the *.conf file - I have the .conf file that I am required to use so I have copied it. I have questions about the steps after this one:

1. Next, after copying the client keys and the certificate of the CA to /etc/openvpn/, we are required to edit the client.conf file to enusre that 3 lines are pointing to the names of the copied files ca, crt and key.
Then, 2 steps below, we are to specify the keyfile names that wwe copied from the server. Again, these are 3 files ca, crt and key. And, I assume that these are also client files.
_Question_: In both these steps, 3 files are referred to. Aren't these all the same 3 files? If so, why is the second step required? i.e. **if I have copied the client keys and certificate to /etc/openvpn and then enusred that 3 lines are pointing to the names of the copied files ca, crt and key, then I should be done right?**

2. Also, separate .conf files are recommended for each client (see 7th last section, named SSL/TLS parms, from here): [https://openvpn.net/index.php/open-source/documentation/howto.html#examples](https://openvpn.net/index.php/open-source/documentation/howto.html#examples)
_Question_: Shouldn't these separate client files just differ in filename, with everything else being identical?

EDIT: If this is not the right sub-forum for this post, then please move this thread to the appropriate forum. Thank you.

---

### Post by TheFu on 2015-01-24
openvpn has many, many, many different configurations for many, many, many different needs.  

Should separate client files have different names?  Maybe not.  If you are deploying openvpn to 1000 clients, having different names will get confusing. I find it much easier to use the same name for the same level of access and create the client certs to be provided as needed.  The certs here are per-client machine, so we can disable each individually from the server.

---

