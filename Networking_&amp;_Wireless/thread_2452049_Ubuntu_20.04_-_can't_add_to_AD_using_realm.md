---
title: "Ubuntu 20.04 - can't add to AD using realm"
date: 2020-10-15
forum: Networking &amp; Wireless
---

### Post by shupike on 2020-10-15
Hello! Need some help with sssd - tried to add my new machine ecologyubuntu to AD - unsuccessfully:

sudo realm join --verbose --user=administrator dc.mydomain.ru
 * Resolving: _ldap._tcp.dc.mydomain.ru
 * Resolving: dc.mydomain.ru
 * Performing LDAP DSE lookup on: 192.168.0.10
 * Successfully discovered: mydomain.ru
Password for administrator:
 * Unconditionally checking packages
 * Resolving required packages
 * LANG=C /usr/sbin/adcli join --verbose --domain mydomain.ru --domain-realm MYDOMAIN.RU --domain-controller 192.168.0.10 --login-type user --login-user administrator --stdin-password
 * Using domain name: mydomain.ru
 * Calculated computer account name from fqdn: ECOLOGYUBUNTU
 * Using domain realm: mydomain.ru
 * Sending NetLogon ping to domain controller: 192.168.0.10
 * Received NetLogon info from: dc.mydomain.ru
 * Wrote out krb5.conf snippet to /var/cache/realmd/adcli-krb5-Tqn6cK/krb5.d/adcli-krb5-conf-xkL8EJ
 * Authenticated as user: [EMAIL="administrator@MYDOMAIN.RU"]administrator@MYDOMAIN.RU[/EMAIL]
 ! Couldn't authenticate to active directory: SASL(-1): generic failure: GSSAPI Error: Unspecified GSS failure.  Minor code may provide more information (Server not found in Kerberos database)
adcli: couldn't connect to mydomain.ru domain: Couldn't authenticate to active directory: SASL(-1): generic failure: GSSAPI Error: Unspecified GSS failure.  Minor code may provide more information (Server not found in Kerberos database)
 ! Insufficient permissions to join the domain
realm: Couldn't join realm: Insufficient permissions to join the domain


When I tried this:

kinit [EMAIL="administrator@MYDOMAIN.RU"]administrator@MYDOMAIN.RU[/EMAIL]
Password for [EMAIL="administrator@MYDOMAIN.RU"]administrator@MYDOMAIN.RU[/EMAIL]:
garett@ecologyubuntu:~$ klist
Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: [EMAIL="administrator@MYDOMAIN.RU"]administrator@MYDOMAIN.RU[/EMAIL]

Valid starting     Expires            Service principal
10/15/20 18:24:32  10/16/20 04:24:32  krbtgt/MYDOMAIN.RU@MYDOMAIN.RU
        renew until 10/16/20 18:24:27

Also I disabled ipv6 but no effect. Here is /etc/hosts:

 cat /etc/hosts
127.0.0.1 localhost
192.168.0.171 ecologyubuntu ecologyubuntu.mydomain.ru

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

Password for [EMAIL="administrator@mydomain.ru"]administrator@mydomain.ru[/EMAIL] is 100% correct - what is wrong with my conf? Please help.

---

