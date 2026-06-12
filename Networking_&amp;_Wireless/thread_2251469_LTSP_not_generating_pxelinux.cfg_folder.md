---
title: "LTSP not generating pxelinux.cfg folder"
date: 2014-11-04
forum: Networking &amp; Wireless
---

### Post by sydcul2 on 2014-11-04
Hello,

I have successfully installed LTSP on my Ubuntu 14.04.1 dev machine before, and now I wanted to get it into a production environment.
So I have set up a server PC with Lubuntu 14.10 and tried to install LTSP w/ proxy DHCP using [this]("http://ubuntuforums.org/showthread.php?t=2173749") guide (which was the same I used on my dev PC).
The proxy DHCP and TFTP server seemed to work, but when trying to apply the proxy DHCP fix to the /var/lib/tftpboot/ltsp/i386/pxeboot.cfg/default file I discovered it did not exist, in fact, the entire pxeboot.cfg directory did not exist, and pxeboot.0 and lts.conf also do not exist. All other files seemed fine.
I have not tried copying this file over from my dev pc because this is not a real solution to the problem (and I don't have access to my dev pc anyway). I have already tried to delete and recreate the client image, but to no avail.

Does anyone know what the problem is? Is this a bug in 14.10?

-Sydcul

---

### Post by sydcul2 on 2014-11-05
Well, installing 14.04.1 did solve my problem, although I feel it isn't a real solution. I'll file a bug report later on.

---

