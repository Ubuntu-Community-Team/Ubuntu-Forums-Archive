---
title: "Problem with Cisco VPN client solved..."
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by woodgdo1 on 2006-12-14
I was originally getting a strange error like this while trying to install the Cisco vpn client version 4.8.  

make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** No rule to make target `VPN/vpnclient'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

I have installed this version before on edgy and dapper, so I know to install the kernel headers(see linux-headers-`uname -a`), however, I couldn't figure out why I couldn't get it to compile...

Apparently, the build script craps out if the parent directory of the vpnclient directory from the tarball (vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz)  contains a space.

Just thought I would pass this along to those banging their head against their keyboard.](*,)

---

### Post by Dragonbite on 2007-01-30
Where did you get the vpnclient-linux tar file?  I don't find anything other than vpnc in the Ubuntu repositories.
I'm trying to get Ubuntu to connect to work and so far come up empty, but I have successfully performed it using Gentoo [vpnclient-3DES]("http://packages.gentoo.org/ebuilds/?cisco-vpnclient-3des-4.0.1a-r1").

I have the PCF files and have been trying to use KVpnc but even that is not working.

[Edit]
Nevermind.. I got it from work, who got it from Cisco.

---

