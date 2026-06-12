---
title: "Add to AD on Windows Server with Ubuntu 18.04"
date: 2020-04-14
forum: Networking &amp; Wireless
---

### Post by strigoff on 2020-04-14
Hello!
I try add server with Ubuntu Server 18.04.04 in our domain domen.ru, but don't work. Who know what problem?

> 
[LIST=1]
[*]root@vld_pbx:~# realm join -U [EMAIL="admin@domen.ru"]admin@domen.ru[/EMAIL] domen.ru --verbose
[*] * Resolving: _ldap._tcp.domen.ru
[*] * Performing LDAP DSE lookup on: 172.26.167.12
[*] * Performing LDAP DSE lookup on: 172.26.7.12
[*] * Performing LDAP DSE lookup on: 172.26.39.12
[*] * Successfully discovered: domen.ru
[*]Password for [EMAIL="admin@domen.ru"]admin@domen.ru[/EMAIL]:
[*] * Unconditionally checking packages
[*] * Resolving required packages
[*] * LANG=C /usr/sbin/adcli join --verbose --domain domen.ru --domain-realm DOMEN.RU --domain-controller 172.26.39.12 --login-type user --login-user [EMAIL="admin@domen.ru"]admin@domen.ru[/EMAIL] --stdin-password
[*] * Using domain name: domen.ru
[*] * Calculated computer account name from fqdn: VLD_PBX
[*] * Using domain realm: domen.ru
[*] * Sending netlogon pings to domain controller: cldap://172.26.39.12
[*] * Received NetLogon info from: AFUKDC01.domen.ru
[*] * Wrote out krb5.conf snippet to /var/cache/realmd/adcli-krb5-OYoEg7/krb5.d/adcli-krb5-conf-CPfYbk
[*] ! Couldn't get kerberos ticket for: [EMAIL="admin@pdomen.ru"]admin@domen.ru[/EMAIL]: KDC reply did not match expectations
[*]adcli: couldn't connect to domen.ru domain: Couldn't get kerberos ticket for: [EMAIL="admin@domen.ru"]admin@domen.ru[/EMAIL]: KDC reply did not match expectations
[*] ! Failed to join the domain
[*]realm: Couldn't join realm: Failed to join the domain
[*]root@vld_pbx:~#
[/LIST]


---

