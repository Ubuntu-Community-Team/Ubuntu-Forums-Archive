---
title: "*** ADVISE *** Best Choice for new file server"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by MaquinaX on 2007-12-12
Hello Guys,
                   Here's my situation, I'm a novice in networking, and was looking to put together an Ubuntu file server. Some of the options I would like available are for clients to be authenticated by server during boot login, also, where server can get any files from clients, where server can send messages to clients,
server manages network traffic efficiently, to where if several users are on at once, network traffic doesn't come to a halt (why does this happen?). Some of the client machines will be Win Based, but I would prefer not to use samba, taking to account some of the horror stories I've read about it.
All suggestions will be appreciated. Thank you all in advance.

           MaquinaX

---

### Post by MaquinaX on 2007-12-12
bump...

---

### Post by MaquinaX on 2007-12-13
bump

---

### Post by MaquinaX on 2007-12-13
bump

---

### Post by jcostom on 2007-12-13
First, bumping over & over again is just rude.

Second, "horror stories" about Samba?  Like?  Most folks don't have a problem with Samba, and it can easily function as a domain controller, which is what you're asking for.

If you want to be slick about it, setup LDAP-based user authentication for Samba, then you'll also have an LDAP directory hanging around that you can use for other things down the line.

The only things I could suggest are bringing your network traffic "to a halt" on the server side would be slow link speeds or a grossly under-sized server.

---

### Post by MaquinaX on 2007-12-13
> **jcostom said:**
> First, bumping over & over again is just rude.

Second, "horror stories" about Samba?  Like?  Most folks don't have a problem with Samba, and it can easily function as a domain controller, which is what you're asking for.

If you want to be slick about it, setup LDAP-based user authentication for Samba, then you'll also have an LDAP directory hanging around that you can use for other things down the line.

The only things I could suggest are bringing your network traffic "to a halt" on the server side would be slow link speeds or a grossly under-sized server.

Thank you JCostom for the advise. I'll take your advise, and begin to research more about it to see
exactly what it is that I have to do. Thanx again.

MaquinaX:)

---

