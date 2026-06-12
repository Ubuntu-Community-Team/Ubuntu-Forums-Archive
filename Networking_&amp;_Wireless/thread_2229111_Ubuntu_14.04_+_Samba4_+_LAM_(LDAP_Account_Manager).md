---
title: "Ubuntu 14.04 + Samba4 + LAM (LDAP Account Manager)"
date: 2014-06-11
forum: Networking &amp; Wireless
---

### Post by Zetheroo on 2014-06-11
What I got:

- Fresh install of Ubuntu 14.04 Server x64
- Samba4 DC/AD setup as per [http://www.tiltingatlinux.com/2014/04/basic-samba4-domain-controler-on-ubuntu.html]("http://www.tiltingatlinux.com/2014/04/basic-samba4-domain-controler-on-ubuntu.html")
- LAM installed with 'apt-get install ldap-acount-manager'
- All software installed from Ubuntu Official repos

What I am trying to do:

... is get LAM to manage my Samba4 setup. 

As far as I know I need to get LAM to connect to the LDAP backup of Samba4. I have net been able to make this happen.

[IMG]http://i59.tinypic.com/2norxl.png[/IMG]

---

### Post by Uzzi on 2014-10-15
Mee too

---

### Post by tomsan68 on 2014-12-11
You have edit the security settings to administrator@<domain>, not using cn=administrator,dc=example,dc=com.
This will work

---

