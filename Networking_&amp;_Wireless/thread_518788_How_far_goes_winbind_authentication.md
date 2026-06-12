---
title: "How far goes winbind authentication?"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by muddymind on 2007-08-06
Hi!

after a week of frustrations I managed to make authentications with a M$ windows server 2003 with AD \\:D/

Now there are just 2 matters to solve before we start to create linux workstations in this company:

1.There is a Isa proxy that not only is working as a proxy but it is also working as an internet filter... It checks what group a specific user is from and then it applies the policy specific to that group.
I made a temporary workaround with ntlmaps to manually authenticate as the administrator... Unfortunately it doesn't work the way I want cuz I can't control internet policy for each user remotely  with ISA server...
Even If I authenticate with winbind at login and have a kerberos ticket it simply doesn't work If I just put the proxy address without any user or password (tested in firefox...). How can I make the isa proxy to recognize that a user belongs to a domain group?

2.I got kerberos working but I don't know how to make him get a ticket automatically with the user log-in... I saw somewhere that I need to make a login script but I don't know how to do that... I want a user to get a ticket with it's login information without typing the password twice... is that possible? and if it is, how? and if it is not, how can I make it?

[]

---

### Post by muddymind on 2007-08-06
anyone? :(

---

### Post by muddymind on 2007-08-07
~~bump~~

Plz Help!!! :(

---

### Post by muddymind on 2007-08-07
ok... I managed to get automatic kerberos TGT by using pam-krb5. I had problems to put it working but I solved them by putting pam-krb5 as the 1st authentication in /etc/pam.d/common-auth

Now I only need to solve the damn proxy problem... I still can't make it work... suggestions are welcome :)
I want to be able to use the ISA proxy without making the ntl authentication cuz I'm already authenticated against an AD and it should detect what group I belong to...

[]

---

### Post by muddymind on 2007-08-07
~~bump~~

---

