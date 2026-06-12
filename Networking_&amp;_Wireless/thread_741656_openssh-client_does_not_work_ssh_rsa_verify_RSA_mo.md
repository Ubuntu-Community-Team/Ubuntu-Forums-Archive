---
title: "openssh-client does not work: ssh_rsa_verify: RSA modulus too small"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by SlavKv on 2008-03-31
I have to use ssh to manage Cisco devices with ssh version 2.
When I trying it I get an error:

*host$ ssh CiscoDevice*
[B]ssh_rsa_verify: RSA modulus too small: 512 < minimum 768 bits
key_verify failed for server_host_key[/B]

I've read that I have to recompile this program to fix this problem.

Can I download sources of openssh-client using APT ?
or maybe there is any already fixed deb packet ?

---

### Post by SlavKv on 2008-04-01
It seems to me only I'm so lucky or noone works with Cisco from Ubuntu

---

### Post by iamfromit on 2008-05-13
Use the PuTTY ssh client. It's in the repos. You can enable a "bug" mode that allows you to ignore the invalid modulus length. 

Consequently, SSH Version 2 specifies a key modulus size of 768 or higher, so it's actually Cisco that has a problem. 

Alternatively, you could make a stronger RSA key ( on a router, I think you would enter
```
crypto key generate rsa modulus <len>
```
where <len> could be arbitrarily defined (1024 is good and strong...)
OR,
specify and use SSH version 1 by typing 
```
ssh -1 user@CiscoDevice
``` instead of just ```
ssh CiscoDevice
```

Good luck,

-j

---

### Post by Truxpin on 2008-07-22
Just to make sure the solution is easier to find on the WEB: 

ssh -1 [email]user@CiscoSwitch.IP[/email]  

WORKS! Make sure you type a "one" and NOT a "l" - as said below the solution is to tell your ssh client to work with RSA version 1. 

Have a nice holiday! Fabrizio.

---

