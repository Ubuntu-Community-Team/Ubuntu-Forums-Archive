---
title: "Hostname resolution"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by gerasmus on 2006-10-11
Problem, remote machine not able to connect to my ubuntu machine.

Example, from internet connected machine  I will enter [http://mydomain.dyndns.info:10000/](http://mydomain.dyndns.info:10000/) to get to webmin.

[I]Then get the following is returned,
Error - Bad Request:

This web server is running in SSL mode. Try the URL [https://bediener.local:10000/](https://bediener.local:10000/) instead.

From an internet connected connected, or any other machine for that matter, the address [https://bediener.local:10000/](https://bediener.local:10000/)  will defenitely not work. 

Where/what do I change so that I'll be presented with [https://mydomain.dyndns.info:10000/](https://mydomain.dyndns.info:10000/), and for all other services hosted on this machine.

[FONT="Verdana"][SIZE="2"]My output from /etc/hosts.allow: 

List of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5), hosts_options(5)
#                   and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8), rpc.mountd(8) and
# /usr/share/doc/portmap/portmapper.txt.gz for further information.
#
ALL
om /etc/hosts,
[/SIZE][/FONT]

and from /etc/hosts
[FONT="Verdana"][SIZE="2"]
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8), rpc.mountd(8) and
# /usr/share/doc/portmap/portmapper.txt.gz for further information.
#
ALL
gerasmus@bediener:~$ more /etc/host
/etc/host: Onbekend bestand of map
gerasmus@bediener:~$ more /etc/hosts
127.0.0.1 localhost bediener.gerasmus.dyndns.info
127.0.1.1 bediener

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
[/SIZE][/FONT]:confused:

---

