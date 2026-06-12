---
title: "OpenVPN - Key Issues with openssl/vpn-vulnkey"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by jconerly on 2008-10-01
Howdy,

I'm  having trouble getting my ubuntu lappy (8.04) connected to the VPN here at work. My OS X machine worked just fine with the same key-set, but I'm having issues with linux.

Here is the error message I am getting:

```
Wed Oct  1 16:03:06 2008 OpenVPN 2.1_rc7 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on Jun 11 2008
Wed Oct  1 16:03:12 2008 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Wed Oct  1 16:03:12 2008 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Wed Oct  1 16:03:13 2008 ERROR: 'key.key' is a known vulnerable key. See 'man openssl-vulnkey' for details.
Wed Oct  1 16:03:13 2008 Exiting
```

However, when I run 'key.key' through openssl-vulnkey directly it passes:

```
foo@bar:~/vpn$ openssl-vulnkey -b 1024 -m key.key 
Not blacklisted: ### 
```

Also (and this just might be me confusing the purpose of the two utilities) my TLS key shows different results depending on what tool I use:

```
foo@bar:~/vpn$ openssl-vulnkey -b 1024 -m tls.key 
Not blacklisted: ### 
foo@bar:~/vpn$ openvpn-vulnkey tls.key 
COMPROMISED: ### tls.key
```

At the moment I'm mostly concerned with the first issue as that is what's making openvpn halt. 

Any thoughts?

---

### Post by jconerly on 2008-10-01
bump.

---

### Post by anthro398 on 2008-10-22
I'm having the same issue.  I'm configuring OpenVPN server on my desktop and the server won't start and complains about the server key being vulnerable.  I'm running Hardy and my OpenSSL version is 0.9.8g 19 Oct 2007.  The Ubuntu package version is 0.9.8g-4ubuntu3.3.  This is supposed to have been fixed since 3.1 per [Canonical]("http://www.ubuntu.com/usn/USN-612-1").  I've seen that some people are recommending disabling the vuln-key check, but that doesn't sound right.

I just noticed that the same OpenSSL version is installed in Intrepid.  It seems pretty unlikely that this version is generating vulnerable keys.

Edit: Just realized that my configuration file was pointing at an old key.

---

