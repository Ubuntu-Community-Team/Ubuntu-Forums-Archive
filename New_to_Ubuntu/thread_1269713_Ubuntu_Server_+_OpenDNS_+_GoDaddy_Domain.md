---
title: "Ubuntu Server + OpenDNS + GoDaddy Domain"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by drakeo11 on 2009-09-18
I apologize in advance :).

I just had our website installed on our dedicated, remote server running ubuntu server edition.

Everything runs well.  However, server admin is gone for weekend and he forgot to associate the webserver ip with the domain name.

The domain name is hosted with GoDaddy.

I'm trying to use OpenDNS's name servers, and have made the following basic changes on the server by SSHing in:
[INDENT]sudo cp /etc/resolv.conf /etc/resolv.conf.auto
[/INDENT][INDENT]sudo gedit /etc/dhcp3/dhclient.conf
[/INDENT][INDENT] prepend domain-name-servers 208.67.222.222,208.67.220.220;
[/INDENT]I've also played around with the setup on GoDaddy...but frankly, I'm scared to change much more as I don't want to screw up the server royally.

Any advice would be greatly appreciated.

Basically: I need to know how to associate my godaddy domain with the active server IP.

Many thanks.

Drake

---

