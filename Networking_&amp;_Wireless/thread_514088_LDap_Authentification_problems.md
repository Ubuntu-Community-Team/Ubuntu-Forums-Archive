---
title: "LDap Authentification problems"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by Peque on 2007-07-31
Hey Forum.

I have some problems about setting op an OPENLDAP - I have followed this guide [https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29?highlight=%28LDAP%29#head-483bc131ba652643f467ff7753a1fad3bab33793]("https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29?highlight=%28LDAP%29#head-483bc131ba652643f467ff7753a1fad3bab33793")
But there's a link to LDAPservertools.tar.gz  which isn't working ??? 
Do I need that so much ? or is it just a easier way to the configurationsfiles??? 

And the server are working fine. I have choose to use Dapper 6.06 LTS for the LDAP server - would something change if I upgrade iot to feisty

But I want to be able to control some server management using LDAP for users/groups etc.  BUT only as a server - not with GUI.

The problems is like this: 
After installing using the guide - I have rebooted my client. During the bootscreen - the following apears:
* Starting kernel event manager...
udevd[2038]: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server 
**I wonder here - caurse in the LDAPserver log I can see it tries to authenticate the login...**

While trying to login into to the server(client) I set the username and passwd - and the message comes : 
User not known to the underlying authentication module..
And then it fails.

In the LDAP server Logfile I'll get these lines: 
```
Jul 31 15:25:04 quark slapd[3620]: connection_get(10)
Jul 31 15:25:04 quark slapd[3620]: connection_get(10): got connid=134
Jul 31 15:25:04 quark slapd[3620]: connection_read(10): checking for input on id=134
Jul 31 15:25:04 quark slapd[3620]: ber_get_next on fd 10 failed errno=11 (Resource temporarily unavailable)
Jul 31 15:25:04 quark slapd[3620]: do_bind
Jul 31 15:25:04 quark slapd[3620]: >>> dnPrettyNormal: <>
Jul 31 15:25:04 quark slapd[3620]: <<< dnPrettyNormal: <>, <>
Jul 31 15:25:04 quark slapd[3620]: do_bind: version=3 dn="" method=128
Jul 31 15:25:04 quark slapd[3620]: send_ldap_result: conn=134 op=0 p=3
Jul 31 15:25:04 quark slapd[3620]: send_ldap_result: err=49 matched="" text=""
Jul 31 15:25:04 quark slapd[3620]: send_ldap_response: msgid=1 tag=97 err=49
Jul 31 15:25:04 quark slapd[3620]: do_bind: v3 anonymous bind
Jul 31 15:25:04 quark slapd[3620]: connection_get(10)
Jul 31 15:25:04 quark slapd[3620]: connection_get(10): got connid=134
Jul 31 15:25:04 quark slapd[3620]: connection_read(10): checking for input on id=134
Jul 31 15:25:04 quark slapd[3620]: ber_get_next on fd 10 failed errno=0 (Success)
Jul 31 15:25:04 quark slapd[3620]: connection_read(10): input error=-2 id=134, closing.
Jul 31 15:25:04 quark slapd[3620]: connection_closing: readying conn=134 sd=10 for close
Jul 31 15:25:04 quark slapd[3620]: connection_close: deferring conn=134 sd=10
Jul 31 15:25:04 quark slapd[3620]: do_unbind
Jul 31 15:25:04 quark slapd[3620]: connection_resched: attempting closing conn=134 sd=10
Jul 31 15:25:04 quark slapd[3620]: connection_close: conn=134 sd=10
Jul 31 15:25:04 quark slapd[3620]: connection_get(11)
Jul 31 15:25:04 quark slapd[3620]: connection_get(11): got connid=135
Jul 31 15:25:04 quark slapd[3620]: connection_read(11): checking for input on id=135
Jul 31 15:25:04 quark slapd[3620]: ber_get_next on fd 11 failed errno=11 (Resource temporarily unavailable)
Jul 31 15:25:04 quark slapd[3620]: do_bind
Jul 31 15:25:04 quark slapd[3620]: >>> dnPrettyNormal: <>
Jul 31 15:25:04 quark slapd[3620]: <<< dnPrettyNormal: <>, <>
Jul 31 15:25:04 quark slapd[3620]: do_bind: version=3 dn="" method=128
Jul 31 15:25:04 quark slapd[3620]: send_ldap_result: conn=135 op=0 p=3
Jul 31 15:25:04 quark slapd[3620]: send_ldap_result: err=49 matched="" text=""
Jul 31 15:25:04 quark slapd[3620]: send_ldap_response: msgid=1 tag=97 err=49
Jul 31 15:25:04 quark slapd[3620]: do_bind: v3 anonymous bind
Jul 31 15:25:04 quark slapd[3620]: connection_get(11)
Jul 31 15:25:04 quark slapd[3620]: connection_get(11): got connid=135
Jul 31 15:25:04 quark slapd[3620]: connection_read(11): checking for input on id=135
Jul 31 15:25:04 quark slapd[3620]: ber_get_next on fd 11 failed errno=0 (Success)
Jul 31 15:25:04 quark slapd[3620]: connection_read(11): input error=-2 id=135, closing.
Jul 31 15:25:04 quark slapd[3620]: connection_closing: readying conn=135 sd=11 for close
Jul 31 15:25:04 quark slapd[3620]: connection_close: deferring conn=135 sd=11
Jul 31 15:25:04 quark slapd[3620]: do_unbind
Jul 31 15:25:04 quark slapd[3620]: connection_resched: attempting closing conn=135 sd=11
Jul 31 15:25:04 quark slapd[3620]: connection_close: conn=135 sd=11
Jul 31 15:25:05 quark slapd[3620]: connection_get(10)
Jul 31 15:25:05 quark slapd[3620]: connection_get(10): got connid=136
Jul 31 15:25:05 quark slapd[3620]: connection_read(10): checking for input on id=136
Jul 31 15:25:05 quark slapd[3620]: ber_get_next on fd 10 failed errno=11 (Resource temporarily unavailable)
Jul 31 15:25:05 quark slapd[3620]: do_bind
Jul 31 15:25:05 quark slapd[3620]: >>> dnPrettyNormal: <>
Jul 31 15:25:05 quark slapd[3620]: <<< dnPrettyNormal: <>, <>
Jul 31 15:25:05 quark slapd[3620]: do_bind: version=3 dn="" method=128
Jul 31 15:25:05 quark slapd[3620]: send_ldap_result: conn=136 op=0 p=3
Jul 31 15:25:05 quark slapd[3620]: send_ldap_result: err=49 matched="" text=""
Jul 31 15:25:05 quark slapd[3620]: send_ldap_response: msgid=1 tag=97 err=49
Jul 31 15:25:05 quark slapd[3620]: do_bind: v3 anonymous bind
Jul 31 15:25:05 quark slapd[3620]: connection_get(10)
Jul 31 15:25:05 quark slapd[3620]: connection_get(10): got connid=136
Jul 31 15:25:05 quark slapd[3620]: connection_read(10): checking for input on id=136
Jul 31 15:25:05 quark slapd[3620]: ber_get_next on fd 10 failed errno=0 (Success)
Jul 31 15:25:05 quark slapd[3620]: connection_read(10): input error=-2 id=136, closing.
Jul 31 15:25:05 quark slapd[3620]: connection_closing: readying conn=136 sd=10 for close
Jul 31 15:25:05 quark slapd[3620]: connection_close: deferring conn=136 sd=10
Jul 31 15:25:05 quark slapd[3620]: connection_get(11)
Jul 31 15:25:05 quark slapd[3620]: connection_get(11): got connid=137
Jul 31 15:25:05 quark slapd[3620]: connection_read(11): checking for input on id=137
Jul 31 15:25:05 quark slapd[3620]: ber_get_next on fd 11 failed errno=11 (Resource temporarily unavailable)
Jul 31 15:25:05 quark slapd[3620]: do_unbind
Jul 31 15:25:05 quark slapd[3620]: connection_resched: attempting closing conn=136 sd=10
Jul 31 15:25:05 quark slapd[3620]: connection_close: conn=136 sd=10
Jul 31 15:25:05 quark slapd[3620]: do_bind
Jul 31 15:25:05 quark slapd[3620]: >>> dnPrettyNormal: <cn=manager,dc=insatech,dc=com>
Jul 31 15:25:05 quark slapd[3620]: <<< dnPrettyNormal: <cn=manager,dc=insatech,dc=com>, <cn=manager,dc=insatech,dc=com>
Jul 31 15:25:05 quark slapd[3620]: do_bind: version=3 dn="cn=manager,dc=insatech,dc=com" method=128
Jul 31 15:25:05 quark slapd[3620]: ==> bdb_bind: dn: cn=manager,dc=insatech,dc=com
Jul 31 15:25:05 quark slapd[3620]: do_bind: v3 bind: "cn=manager,dc=insatech,dc=com" to "cn=manager,dc=insatech,dc=com"
Jul 31 15:25:05 quark slapd[3620]: send_ldap_result: conn=137 op=0 p=3
Jul 31 15:25:05 quark slapd[3620]: send_ldap_result: err=0 matched="" text=""
Jul 31 15:25:05 quark slapd[3620]: send_ldap_response: msgid=1 tag=97 err=0
Jul 31 15:25:05 quark slapd[3620]: connection_get(11)
Jul 31 15:25:05 quark slapd[3620]: connection_get(11): got connid=137
Jul 31 15:25:05 quark slapd[3620]: connection_read(11): checking for input on id=137
Jul 31 15:25:05 quark slapd[3620]: ber_get_next on fd 11 failed errno=11 (Resource temporarily unavailable)
Jul 31 15:25:05 quark slapd[3620]: do_search
Jul 31 15:25:05 quark slapd[3620]: >>> dnPrettyNormal: <dc=insatech,dc=com>
Jul 31 15:25:05 quark slapd[3620]: <<< dnPrettyNormal: <dc=insatech,dc=com>, <dc=insatech,dc=com>
Jul 31 15:25:05 quark slapd[3620]: SRCH "dc=insatech,dc=com" 2 0
Jul 31 15:25:05 quark slapd[3620]:     1 0 0
Jul 31 15:25:05 quark slapd[3620]:     filter: (uid=pbj)
Jul 31 15:25:05 quark slapd[3620]:     attrs:
Jul 31 15:25:05 quark slapd[3620]:
Jul 31 15:25:05 quark slapd[3620]: => bdb_search
Jul 31 15:25:05 quark slapd[3620]: bdb_dn2entry("dc=insatech,dc=com")
Jul 31 15:25:05 quark slapd[3620]: search_candidates: base="dc=insatech,dc=com" (0x00000003) scope=2
Jul 31 15:25:05 quark slapd[3620]: => bdb_dn2idl( "dc=insatech,dc=com" )
Jul 31 15:25:05 quark slapd[3620]: => bdb_equality_candidates (objectClass)
Jul 31 15:25:05 quark slapd[3620]: => key_read
Jul 31 15:25:05 quark slapd[3620]: bdb_idl_fetch_key: [b49d1940]
Jul 31 15:25:05 quark slapd[3620]: <= bdb_index_read: failed (-30990)
Jul 31 15:25:05 quark slapd[3620]: <= bdb_equality_candidates: id=0, first=0, last=0
Jul 31 15:25:05 quark slapd[3620]: => bdb_equality_candidates (uid)
Jul 31 15:25:05 quark slapd[3620]: => key_read
Jul 31 15:25:05 quark slapd[3620]: bdb_idl_fetch_key: [8b09fbb9]
Jul 31 15:25:05 quark slapd[3620]: <= bdb_index_read 1 candidates
Jul 31 15:25:05 quark slapd[3620]: <= bdb_equality_candidates: id=1, first=53, last=53
Jul 31 15:25:05 quark slapd[3620]: bdb_search_candidates: id=1 first=53 last=53
Jul 31 15:25:05 quark slapd[3620]: => send_search_entry: dn="cn=Per JÃ¸rgensen,ou=Users,dc=insatech,dc=com"
Jul 31 15:25:05 quark slapd[3620]: <= send_search_entry
Jul 31 15:25:05 quark slapd[3620]: send_ldap_result: conn=137 op=1 p=3
Jul 31 15:25:05 quark slapd[3620]: send_ldap_result: err=0 matched="" text=""
Jul 31 15:25:05 quark slapd[3620]: send_ldap_response: msgid=2 tag=101 err=0
Jul 31 15:25:05 quark slapd[3620]: connection_get(11)
Jul 31 15:25:05 quark slapd[3620]: connection_get(11): got connid=137
Jul 31 15:25:05 quark slapd[3620]: connection_read(11): checking for input on id=137
Jul 31 15:25:05 quark slapd[3620]: ber_get_next on fd 11 failed errno=11 (Resource temporarily unavailable)
Jul 31 15:25:05 quark slapd[3620]: do_bind
Jul 31 15:25:05 quark slapd[3620]: => get_ctrls
Jul 31 15:25:05 quark slapd[3620]: => get_ctrls: oid="1.3.6.1.4.1.42.2.27.8.5.1" (noncritical)
Jul 31 15:25:05 quark slapd[3620]: <= get_ctrls: n=1 rc=0 err=""
Jul 31 15:25:05 quark slapd[3620]: >>> dnPrettyNormal: <cn=Per JÃ¸rgensen,ou=Users,dc=insatech,dc=com>
Jul 31 15:25:05 quark slapd[3620]: <<< dnPrettyNormal: <cn=Per JÃ¸rgensen,ou=Users,dc=insatech,dc=com>, <cn=per jÃ¸rgensen,ou=users,dc=insatech,dc=com>
Jul 31 15:25:05 quark slapd[3620]: do_bind: version=3 dn="cn=Per JÃ¸rgensen,ou=Users,dc=insatech,dc=com" method=128
Jul 31 15:25:05 quark slapd[3620]: ==> bdb_bind: dn: cn=Per JÃ¸rgensen,ou=Users,dc=insatech,dc=com
Jul 31 15:25:05 quark slapd[3620]: bdb_dn2entry("cn=per jÃ¸rgensen,ou=users,dc=insatech,dc=com")
Jul 31 15:25:05 quark slapd[3620]: do_bind: v3 bind: "cn=Per JÃ¸rgensen,ou=Users,dc=insatech,dc=com" to "cn=Per JÃ¸rgensen,ou=Users,dc=insatech,dc=com"
Jul 31 15:25:05 quark slapd[3620]: send_ldap_result: conn=137 op=2 p=3
Jul 31 15:25:05 quark slapd[3620]: send_ldap_result: err=0 matched="" text=""
Jul 31 15:25:05 quark slapd[3620]: send_ldap_response: msgid=3 tag=97 err=0
Jul 31 15:25:05 quark slapd[3620]: connection_get(11)
Jul 31 15:25:05 quark slapd[3620]: connection_get(11): got connid=137
Jul 31 15:25:05 quark slapd[3620]: connection_read(11): checking for input on id=137
Jul 31 15:25:05 quark slapd[3620]: ber_get_next on fd 11 failed errno=11 (Resource temporarily unavailable)
Jul 31 15:25:05 quark slapd[3620]: do_bind
Jul 31 15:25:05 quark slapd[3620]: >>> dnPrettyNormal: <cn=manager,dc=insatech,dc=com>
Jul 31 15:25:05 quark slapd[3620]: <<< dnPrettyNormal: <cn=manager,dc=insatech,dc=com>, <cn=manager,dc=insatech,dc=com>
Jul 31 15:25:05 quark slapd[3620]: do_bind: version=3 dn="cn=manager,dc=insatech,dc=com" method=128
Jul 31 15:25:05 quark slapd[3620]: ==> bdb_bind: dn: cn=manager,dc=insatech,dc=com
Jul 31 15:25:05 quark slapd[3620]: do_bind: v3 bind: "cn=manager,dc=insatech,dc=com" to "cn=manager,dc=insatech,dc=com"
Jul 31 15:25:05 quark slapd[3620]: send_ldap_result: conn=137 op=3 p=3
Jul 31 15:25:05 quark slapd[3620]: send_ldap_result: err=0 matched="" text=""
Jul 31 15:25:05 quark slapd[3620]: send_ldap_response: msgid=4 tag=97 err=0
Jul 31 15:25:05 quark slapd[3620]: connection_get(10)
Jul 31 15:25:05 quark slapd[3620]: connection_get(10): got connid=138
Jul 31 15:25:05 quark slapd[3620]: connection_read(10): checking for input on id=138
Jul 31 15:25:05 quark slapd[3620]: ber_get_next on fd 10 failed errno=11 (Resource temporarily unavailable)
Jul 31 15:25:05 quark slapd[3620]: do_bind
Jul 31 15:25:05 quark slapd[3620]: >>> dnPrettyNormal: <>
Jul 31 15:25:05 quark slapd[3620]: <<< dnPrettyNormal: <>, <>
Jul 31 15:25:05 quark slapd[3620]: do_bind: version=3 dn="" method=128
Jul 31 15:25:05 quark slapd[3620]: send_ldap_result: conn=138 op=0 p=3
Jul 31 15:25:05 quark slapd[3620]: send_ldap_result: err=49 matched="" text=""
Jul 31 15:25:05 quark slapd[3620]: send_ldap_response: msgid=1 tag=97 err=49
Jul 31 15:25:05 quark slapd[3620]: do_bind: v3 anonymous bind
Jul 31 15:25:05 quark slapd[3620]: connection_get(10)
Jul 31 15:25:05 quark slapd[3620]: connection_get(10): got connid=138
Jul 31 15:25:05 quark slapd[3620]: connection_read(10): checking for input on id=138
Jul 31 15:25:05 quark slapd[3620]: ber_get_next on fd 10 failed errno=0 (Success)
Jul 31 15:25:05 quark slapd[3620]: connection_read(10): input error=-2 id=138, closing.
Jul 31 15:25:05 quark slapd[3620]: connection_closing: readying conn=138 sd=10 for close
Jul 31 15:25:05 quark slapd[3620]: connection_close: deferring conn=138 sd=10
Jul 31 15:25:05 quark slapd[3620]: connection_get(15)
Jul 31 15:25:05 quark slapd[3620]: connection_get(15): got connid=139
Jul 31 15:25:05 quark slapd[3620]: connection_read(15): checking for input on id=139
Jul 31 15:25:05 quark slapd[3620]: ber_get_next on fd 15 failed errno=11 (Resource temporarily unavailable)
Jul 31 15:25:05 quark slapd[3620]: do_unbind
Jul 31 15:25:05 quark slapd[3620]: connection_resched: attempting closing conn=138 sd=10
Jul 31 15:25:05 quark slapd[3620]: connection_close: conn=138 sd=10
Jul 31 15:25:05 quark slapd[3620]: do_bind
Jul 31 15:25:05 quark slapd[3620]: >>> dnPrettyNormal: <>
Jul 31 15:25:05 quark slapd[3620]: <<< dnPrettyNormal: <>, <>
Jul 31 15:25:05 quark slapd[3620]: do_bind: version=3 dn="" method=128
Jul 31 15:25:05 quark slapd[3620]: send_ldap_result: conn=139 op=0 p=3
Jul 31 15:25:05 quark slapd[3620]: send_ldap_result: err=49 matched="" text=""
Jul 31 15:25:05 quark slapd[3620]: send_ldap_response: msgid=1 tag=97 err=49
Jul 31 15:25:05 quark slapd[3620]: do_bind: v3 anonymous bind
Jul 31 15:25:05 quark slapd[3620]: connection_get(15)
Jul 31 15:25:05 quark slapd[3620]: connection_get(15): got connid=139
Jul 31 15:25:05 quark slapd[3620]: connection_read(15): checking for input on id=139
Jul 31 15:25:05 quark slapd[3620]: ber_get_next on fd 15 failed errno=0 (Success)
Jul 31 15:25:05 quark slapd[3620]: connection_read(15): input error=-2 id=139, closing.
Jul 31 15:25:05 quark slapd[3620]: connection_closing: readying conn=139 sd=15 for close
Jul 31 15:25:05 quark slapd[3620]: connection_close: deferring conn=139 sd=15
Jul 31 15:25:05 quark slapd[3620]: do_unbind
Jul 31 15:25:05 quark slapd[3620]: connection_resched: attempting closing conn=139 sd=15
Jul 31 15:25:05 quark slapd[3620]: connection_close: conn=139 sd=15
Jul 31 15:25:05 quark slapd[3620]: connection_get(11)
Jul 31 15:25:05 quark slapd[3620]: connection_get(11): got connid=137
Jul 31 15:25:05 quark slapd[3620]: connection_read(11): checking for input on id=137
Jul 31 15:25:05 quark slapd[3620]: ber_get_next on fd 11 failed errno=0 (Success)
Jul 31 15:25:05 quark slapd[3620]: connection_read(11): input error=-2 id=137, closing.
Jul 31 15:25:05 quark slapd[3620]: do_unbind
Jul 31 15:25:05 quark slapd[3620]: connection_closing: readying conn=137 sd=11 for close
Jul 31 15:25:05 quark slapd[3620]: connection_close: deferring conn=137 sd=11
Jul 31 15:25:05 quark slapd[3620]: connection_resched: attempting closing conn=137 sd=11
Jul 31 15:25:05 quark slapd[3620]: connection_close: conn=137 sd=11

```

So nowhere I seems to find the solution for this - or perhaps I'm looking the totally wrong places.

Do someone have aq clue or an idea of what I should do??? 

Thanks 
Per

---

