---
title: "passing username and password to firewall by command"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by laoanywhere on 2011-02-05
There is a firewall server in my organization to authorize PC with username and password to access to Internet. Unfortunately I have reinstall Ubuntu server in my laptop and cannot access to Internet to apt-get, because I's not authorized yet. Please if someone know how to pass username and password to firewall by command line.
Thank you

---

### Post by stmiller on 2011-02-05
Without knowing the specifics of your company's IT security setup, it will be difficult to know what you are referring to, or even how the authentication works that they have in place.

Have you contacted your company's IT staff? Cheers,

---

### Post by taseedorf on 2011-02-05
You cannot pass a username and password to a firewall using normal IP tables.  There must be some other security mechanism.

---

### Post by toolzen on 2011-02-05
Do you mean there is a company HTTP proxy that controls access? You could try:

export http_proxy=http://myuname:mypass@myproxy:myport

and then see if apt-get, etc. work.

---

