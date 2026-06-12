---
title: "LDAP for managing different types of users"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by spauldingsmails on 2008-07-01
Hi all

I currently have an openLdap server set up as my primary *nix account storage and authentication system (I know, I should be using kerberos, that's the next step) using Ubuntu Server 8.04. I'm also using ldap to authenticate users for my bugzilla, mediawiki, svn and joomla apps.

Currently, I have three *nix groups set up;
[LIST]
[*]internal - staff and other internal company users
[*]external - contractors and suppliers who need access to bugzilla, svn, etc
[*]customers - the customers we service
[/LIST]

Internal users also have access to other things such as NFS exports, while external and customer groups can only use our online apps.

Also users are stored in ou=People,dc=mycompanyname,dc=com, and I group users based on their *nix group. However, what I'm wondering is whether I should be using a organizational unit child, e.g.;

dc=mycompanyname,dc=com
|-ou=People
|--ou=Customers
|--ou=Internal
|--ou=External

As there seems no point to storing external and customers groups as *nix groups because they will never have access to the server's filesystem.

Additionally, it is likely that Customers and External can be stored using the Address Book Entry schema as it seems to capture all the information we require.

I'm probably going to go with this new plan and am really just looking for validation that I'm on the right track. If I'm not on the right track what should I be doing to improve the structure of my ldap server?

Any help much appreciated.

---

### Post by jpeddicord on 2008-07-01
Not a tutorial, so moved appropriately. :)

---

