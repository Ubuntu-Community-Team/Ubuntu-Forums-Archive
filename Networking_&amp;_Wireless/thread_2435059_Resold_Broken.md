---
title: "Resold Broken"
date: 2020-01-15
forum: Networking &amp; Wireless
---

### Post by lslamp on 2020-01-15
I am really sorry if this question is in the wrong place or incorrect but I have now battled for a few weeks and have made no progress.
I am pretty new to this resolvd stuff.
The only thing that I have found is that resolvd is broken after an Ubuntu update. 
After very much searching and reading I found the following link.
[https://bugs.php.net/bug.php?id=74287](https://bugs.php.net/bug.php?id=74287)
From this thread, I searched the UBUNTU forums and found the following link/case. 
[https://ubuntuforums.org/showthread.php?t=2375798&highlight=resolvd](https://ubuntuforums.org/showthread.php?t=2375798&highlight=resolvd)
I have tried all of the suggested solutions and none seem to have worked for me. There is one thing I did not understand, was the syntax of what the guys says here 
"[COLOR=#000000]I got DNS working by explicitly specifying the DNS server in /etc/systemd/resolved.conf[/COLOR]"

with this broken I cannot even do any updates at all. I have tried to add and remove packages and nothing works. 

All I have found say nothing about a resolution. I am completely stumped.
Is there anyone that can help/advise. ... Please

Thanks
Lawrence

---

### Post by rsteinmetz70112 on 2020-01-15
Most likely it's simply mis-configured. 
But to help we need more information.
What version of Ubuntu?
What is in  /etc/systemd/resolved.conf?
What have you tried to do and what were the results?

---

### Post by lslamp on 2020-01-16
Strange that you say mis-config because it was all working and then it suddenly stopped resolving. I only noticed the issue because of an installation of a package within wordpress.
below are the details.
root@heretic:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:        16.04
Codename:       xenial

root@heretic:~# cat  /etc/systemd/resolved.conf
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
#
# Entries in this file show the compile time defaults.
# You can change settings by editing this file.
# Defaults can be restored by simply deleting this file.
#
# See resolved.conf(5) for details


[Resolve]
#DNS=
#FallbackDNS=8.8.8.8 8.8.4.4 2001:4860:4860::8888 2001:4860:4860::8844
#Domains=
#LLMNR=yes
#DNSSEC=no

I tried the following.
[COLOR=#000000]*sudo systemctl disable systemd-resolved.service  -- ran successfully*[/COLOR]
[COLOR=#000000]*sudo service systemd-resolved stop -- ran successfully*[/COLOR]
[COLOR=#111111]*[FONT=Ubuntu]Put the following line in the [main] section of your /etc/NetworkManager/NetworkManager.conf:  [/FONT]*[/COLOR]
[COLOR=#000000]*dns=default   -- Inserted this into the NetworkManager.conf*[/COLOR]
[COLOR=#111111][I][FONT=Ubuntu]
## Tried to do the steps below, but network manager does not seem to be installed.
Delete the symlink /etc/resolv.conf  
[/FONT][/I][/COLOR][COLOR=#000000]*rm /etc/resolv.conf*[/COLOR]
[COLOR=#111111]*[FONT=Ubuntu]Restart network-manager[/FONT]*[/COLOR]
[COLOR=#111111]*[FONT=Consolas]sudo service network-manager restart[/FONT]*[/COLOR]


root@heretic:~# cat /etc/resolv.conf
nameserver 8.8.8.8
nameserver 4.4.4.4

If I try to do an nslookup, below is what I get.

root@heretic:~# nslookup [www.dunnsland.com](www.dunnsland.com)
../../../../lib/isc/unix/socket.c:2881: setsockopt(20, IP_RECVTOS) failed: Protocol not available
Server:         8.8.8.8
Address:        8.8.8.8#53


Non-authoritative answer:
[www.dunnsland.com](www.dunnsland.com)       canonical name = dunnsland.com.
Name:   dunnsland.com
Address: 194.40.236.10



Thanks
Lawrence

---

### Post by bobsuncle on 2020-01-16
Not sure what the protocol not available is all about, but it looks like it returned the correct answer.

  This is what I get when I do the same nslookup:

```
Non-authoritative answer:
www.dunnsland.com    canonical name = dunnsland.com.
Name:    dunnsland.com
Address: 194.40.236.10
```

---

### Post by SeijiSensei on 2020-01-16
If you edit resolv.conf manually, chances are good the edits will be lost the next time you reboot.

/etc/resolv.conf should read:
```

nameserver 127.0.0.53
options edns0

```
and it may have a "search" entry if your computers are in a domain.

In /etc/systemd/resolved.conf you can manually specify name servers with entries like
```
 
DNS=8.8.8.8
FallbackDNS=8.8.4.4

```

Then run "sudo systemctl restart systemd-resolved". This works if the nameserver entry in resolv.conf is 127.0.0.53.

If the computer gets its DNS information from DHCP during boot, then you shouldn't need to specify DNS entries in resolved.conf at all.

---

