---
title: "set hostname from DHCP"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by dkronst on 2008-08-10
Hi all,

I've been trying to figure out how to make my Ubuntu machine get its hostname from DHCP on boot. This is the standard in several other distributions, e.g. SuSE.
I tried to find some clue in the documentation of the dhcp3-client but to no avail. I later tried to install 'dhcpcd' and even though the SET_HOSTNAME='yes' it still doesn't do it. It seems as if it ignores the hostname from the DHCP. 'pump' didn't work either.

Oh, and one more thing. The same machine on a fresh install gets the correct hostname from DHCP, but the thing is that this hostname changes from time to time and the machine has to keep-up...

If anyone has any idea on how to fix it, it would be greatly appreciated.

Dror

---

### Post by Iowan on 2008-08-11
I know there's an option in **/etc/dhcp3/dhclient.conf** , but I'll have to check it when I get home in a couple of hours.

[This thread]("http://ubuntuforums.org/showthread.php?t=876777") was trying to go the other way.

Update: The default dhclient.conf file contains a line/section:```
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, [COLOR="Red"]host-name[/COLOR],
        netbios-name-servers, netbios-scope;
```

---

### Post by dkronst on 2008-08-12
Thanks for your reply!
I tried it, but it didn't seem to work. I suppose I might have a problem with the DHCP server :(
Thanks anyways :)

Dror

---

