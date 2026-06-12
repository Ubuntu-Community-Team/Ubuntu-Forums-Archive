---
title: "[SOLVED] LDAP in Evolution"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by borobudur on 2008-02-14
Hi, I'm trying to open a unique address book in evoluion with an LDAP server. 

I have 3 records added and one of it is a contact called *Sam Smith*. 

If I do this command over the internet: 
```
ldapsearch -LLL -x -b 'dc=subdomain,dc=domain,dc=org' -H ldap://subdomain.domain.org
```I get this:
```
dn: dc=subdomain,dc=domain,dc=org
objectClass: top
objectClass: dcObject
objectClass: organizationalUnit
dc:: Ym9yb2J1ZHVyIA==
ou: Kewl LDAP Server HomeDNS

dn: ou=personal,dc=subdomain,dc=domain,dc=org
objectClass: top
objectClass: organizationalUnit
ou: personal
description: Personal Addressbook

dn: cn=Sam Smith,ou=personal,dc=subdomain,dc=domain,dc=org
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: inetOrgPerson
objectClass: evolutionPerson
givenName: Sam
sn: Smith
cn: Sam Smith
mail: email@here.com
homePhone: .
telephoneNumber: .
facsimileTelephoneNumber: .
pager: .
mobile: .
title: JobTitle
ou: BusinessDept
o: BusinessOrganization
street: BusinessStreet
l: BusinessCity
st: BusinessState
postalCode: BusinessZip
primaryPhone: .
carPhone: .
homeFacsimileTelephoneNumber: .
otherPhone: .
businessRole: .
managerName: .
assistantName: .
spouseName: .
otherPostalAddress: .
mailer: .
birthDate: .
anniversary: .
note: .
fileAs: .
assistantPhone: .
companyPhone: .
callbackPhone: .
otherFacsimileTelephoneNumber: .
radio: .
telex: .
tty: .
categories: .
calendarURI: .
freeBusyURI:: LiA=
category: .

```It looks to me the LDAP server is working fine. Now I open the new address book in evolution but I can't search for *Sam*.

I have set the server with it's port, user secure connection no encryption, login method anonymously.

Why is it not working??

---

### Post by borobudur on 2008-02-17
I found out that it's necessary to chose the search scope sub under details. 
Like this it works fine!

---

