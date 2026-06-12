---
title: "ldap and evolution"
date: 2006-12-31
forum: Networking &amp; Wireless
---

### Post by dninja on 2006-12-31
I'm trying to setup an ldap server to run as my global address book. I followed the instructions on this page [HTML]http://www.brennan.id.au/20-Shared_Address_Book_LDAP.html[/HTML] but I'm stumbling at getting evolution to search the db.

If I run slapd in debug mode the common error I see is:
```
ldap_read: want=8 error=Resource temporarily unavailable
```
If I allow evolution to search for the search base it sets it to just dc=example,dc=com (swapping my bits in instead) but I still get the same error.

Both times evolution comes back with 

```

Unable to perform search.

This query did not complete successfully.
```
So far I have checked that I can search from the command line with 

```
ldapsearch  -D 'uid=robin,ou=users,dc=example,dc=com' -W -x -b 'dc=example,dc=com' '(objectclass=*)'

```
which works ok.

The user login between evolution and ldap works ok, when I give it a wrong password I get an error.

Can anyone suggest anything to try?

Or, can anyone point me at any other tutorials. I ideally want one that shows how to setup ldap to handle all the evolution address book fields, not just a subset.

versions
openldap:

@(#) $OpenLDAP: slapd 2.2.26 (Nov 20 2006 22:36:34) $
        buildd@terranova:/build/buildd/openldap2.2-2.2.26/debian/build/servers/slapd

evolution:
2.8.1

---

### Post by dninja on 2007-01-01
I've fixed it thanks to php!

I found a comment on the php site which says that openldap starts in version 3 mode only. You have to explicitly enable version 2 mode in the slapd.conf file. It seems evolution wants version 2 mode because when I added 
```
allow bind_v2
```to the top of the slapd.conf file and restarted evolution it all started working.

---

