---
title: "SecureClient VPN"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by scamper_22 on 2008-01-09
HI,

I'm trying to connect to a VPN server for work.
It uses checkpoint secureclient vpn, which does not have a modern linux client.

I am running ubuntu Gutsy

I've searched everywhere and there's lots of tidbits, but I'm just confused at this point.  Supposedly, I can use openswan or vpnc.  Butt I have no idea how to configure these correctly.

I've installed kpvnc as well.

Has anyone successfully done this?
I've got the following information to work withThe certificate is pending for the user (CN=XXXX ,CN=YYYYY,DC=AAAAAA,DC=com).
Registration Key: 12345-abcde

cerificate site:  1.2.3.4 (if i go to this site [https://1.2.3.4](https://1.2.3.4) it takes me to SSL Network Extender page.)

I tried doing snx_install, which installed fine....but when i run snx, it says snx: error while loading shared libraries: libcpc++-libc6.1-2.so.3: cannot open shared object file: No such file or directory
and i can't find the libs in a repository.

If anyone can help with this, it will be greatly appreciated.
please try and be as specific as possible as I have no clue about vpn.

Thanks

Y

---

### Post by scamper_22 on 2008-01-10
Okay, I'm making progress with vpnc.

Now, I need to create a certificate.

I was reading the supplied documentation for windows and it looks like the windows program allows you to enter the ip address of the CA and the registration key (as above) and you get a certificate.

Does anyone know if a certificate is somehow tied to the local computer.  Could I for example, do this step at work and save the certificate file and then use it at home?
Or would the certificate somehow be tried to my hardware?

Thanks,

Y

---

